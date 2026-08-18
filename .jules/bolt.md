
## 2025-02-26 - Optimized deepClone
**Learning:** `JSON.parse(JSON.stringify(obj))` is commonly used to deep clone objects, but creating a custom recursive deep copy implementation is ~4-5x faster for typical nested objects. \`structuredClone\` exists but is actually much slower than either for typical simple JS objects in this environment.
**Action:** Replaced JSON serialization approach with a fast recursive deep clone function.


## 2025-02-26 - Optimized getCharWidth
**Learning:** In the `textShapeR.js` text measuring code, `getCharWidth` was using sequential `RegExp.test()` calls which are relatively slow. Replacing it with an O(1) lookup map (using a `Float64Array` mapping unicode to width) speeds up character width measurements ~10-15x, which runs millions of times during shaping.
**Action:** Replaced regex-based `getCharWidth` with a flat array lookup map.
