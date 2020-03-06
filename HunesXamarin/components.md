### Commands to push and delete your packege to Local Server

##### Push

Usage: dotnet nuget push [arguments] [options] to push a packege. <br>
Example: `dotnet nuget push Id.Packege.1.0.0.nupkg -k 1234 -s http://127.0.0.0/nuget`<br>
Type `dotnet nuget push --help` to get help <br>

##### Delete

Usage: `dotnet nuget delete [arguments] [options]` to delete a packege. <br>
Example: `dotnet nuget delete Id.Packege 1.0.0 -k 1234 -s http://127.0.0.0/nuget` <br>
Type `dotnet nuget push --help` to get help <br> 

### How to implement changelog your project

1. Install last version `Hunes.Xamarin.Changelog` from local server actually located in http://192.168.0.72/nuget.
2. Make a list of items changelog. Example:

```c#
private List<Changelog> GetChangelogs()
{
    List<Changelog> changelogs = new List<Changelog>();

    try
    {
        changelogs.Add(new Changelog()
        {
            Date = new DateTime(2019, 02, 19),
            Version = "1.0.0",
            Items = new List<ItemChangeLog>()
            {
                new ItemChangeLog() { Description = "- Changed feature on project.", TypeChangelog = eTypeChangelog.Changed },
                new ItemChangeLog() { Description = "- Added feature on project.", TypeChangelog = eTypeChangelog.Added },
                new ItemChangeLog() { Description = "- Fixed feature on project.", TypeChangelog = eTypeChangelog.Fixed },
                new ItemChangeLog() { Description = "- Removed feature on project.", TypeChangelog = eTypeChangelog.Removed },
                new ItemChangeLog() { Description = "- Security feature on project.", TypeChangelog = eTypeChangelog.Security }
            }
        }); 

        return changelogs;
    }
    catch (Exception)
    {
        throw;
    }
    finally
    {
        changelogs = null;
    }
}
```

3. Get the StackLayout from ChangelogView:

```c#
ChangelogView changelogView = new ChangelogView(GetChangelogs());
changelogView.GetStackLayout();
```
