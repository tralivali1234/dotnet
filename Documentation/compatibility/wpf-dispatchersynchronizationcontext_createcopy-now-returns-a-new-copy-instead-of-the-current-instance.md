## WPF DispatcherSynchronizationContext.CreateCopy now returns a new copy instead of the current instance

### Scope
Minor

### Version Introduced
4.5

### Source Analyzer Status
Available

### Change Description
In the .NET Framework 4, DispatcherSynchronizationContext.CreateCopy() returned a reference to the current instance, primarily as a performance optimization. In the .NET Framework 4.5, it returns a new instance which makes it possible for the first time to conclude that equal references indicate the executing thread is in the correct synchronization context.  It is unlikely that code that checks the identity of these references will be affected, but because of the change, code that calls DispatcherSynchronizationContext.CreateCopy should be tested as part of migration to the .NET Framework 4.5 or newer.

- [ ] Quirked
- [ ] Build-time break

### Recommended Action
Be aware that DispatcherSynchronizationContext.CreateCopy() will now return a new SynchronizationContext object.  Previously, code that used equivalence of references generated this way was not actually checking whether it was in the proper context, but does when built against .NET 4.5 or newer.  While unlikely to cause issues, exercising the affected code paths should be enough to determine if this poses any problem.

### Affected APIs
* `M:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy`

### Category
Windows Presentation Foundation (WPF)

[More information](https://msdn.microsoft.com/en-us/library/hh367887(v=vs.110).aspx#wpf)

<!-- breaking change id: 38 -->
