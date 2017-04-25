## WPF DataTemplate elements are now visible to UIA

### Scope
Edge

### Version Introduced
4.5

### Source Analyzer Status
Available

### Change Description
Previously, DataTemplate elements were invisible to UI Automation. Beginning in 4.5, UI Automation will detect these elements. This is useful in many cases, but can break tests that depend on UIA trees not containing DataTemplate elements.

- [ ] Quirked
- [ ] Build-time break

### Recommended Action
UI Auomation tests for this app may need updated to account for the UIA tree now including previously invisible DataTemplate elements. For example, tests that expect some elements to be next to each other may now need to expect previously invisible UIA elements in between. Or tests that rely on certain counts or indexes for UIA elements may need updated with new values.

### Affected APIs
* `M:System.Windows.DataTemplate.#ctor`
* `M:System.Windows.DataTemplate.#ctor(System.Object)`

### Category
Windows Presentation Foundation (WPF)

[More information](https://msdn.microsoft.com/en-us/library/hh367887\(v=vs.110\).aspx#wpf)

<!-- breaking change id: 3 -->
