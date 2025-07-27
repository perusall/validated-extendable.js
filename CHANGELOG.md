# Changelog

## [8.0.0] - 2024-12-19

### Breaking Changes

- **Zod 4 Required**: This package now requires Zod v4.0.10 or later
- Removed backward compatibility with Zod v3
- Updated peer dependency to `zod ^4.0.10`

### Changed

- Updated package description to reflect Zod 4 compatibility only
- Simplified code by removing Zod 3 compatibility layer
- Updated `getNeverValue()` function to use `z.never()` directly

### Migration Guide

To upgrade from v7.x to v8.0.0:

1. Update your Zod dependency to v4.0.10 or later:

   ```bash
   npm install zod@^4.0.10
   # or
   pnpm add zod@^4.0.10
   # or
   yarn add zod@^4.0.10
   ```

2. Update this package:

   ```bash
   npm install validated-extendable@^8.0.0
   # or
   pnpm add validated-extendable@^8.0.0
   # or
   yarn add validated-extendable@^8.0.0
   ```

3. No code changes required - the API remains the same:

```typescript
import { z } from 'zod';
import { Validated } from 'validated-extendable';

class Person extends Validated(
  z.object({
    name: z.string(),
    age: z.number(),
  })
) {}
```

## [7.4.0] - 2024-06-13

### Added

- **Zod 4 Compatibility**: Added support for Zod 4 while maintaining backward compatibility with Zod 3.25.0+
- Compatible with both `zod` (v3) and `zod/v4` imports
- Handles API changes between Zod versions (e.g., `z.NEVER` vs `z.never()`)

### Changed

- Updated peer dependency to require `zod ^3.25.0` or later
- Updated type definitions to work with both Zod 3 and 4 type systems
- Enhanced package description to mention Zod 4 support

### Technical Details

- Added compatibility layer for `z.NEVER` (Zod 3) and `z.never()` (Zod 4)
- Updated TypeScript types to remove dependency on `z.ZodTypeDef` where necessary
- Added type assertions to handle differences in Zod 3/4 type systems
- All existing functionality remains unchanged and fully compatible

### Migration Guide

No breaking changes for existing users. Simply upgrade to `zod@^3.25.0` to get Zod 4 support.

For Zod 4 users:

```typescript
// Both imports work
import { z } from 'zod'; // Zod 3 or 4
import { z } from 'zod/v4'; // Zod 4 specific (when available)

// Usage remains exactly the same
class Person extends Validated(
  z.object({
    name: z.string(),
    age: z.number(),
  })
) {}
```
