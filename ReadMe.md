# SqlMigraine

SQL Server database migration tool.

- [Boards](https://dev.azure.com/david-palumbo/SqlMigraine/_workitems/recentlyupdated/)
- [Pipelines](https://dev.azure.com/david-palumbo/SqlMigraine/_build)

## Goals

Migrate the manual process of using migration dacpacs.

## Manual Migration Process

1. Create a database version table
   ```SQL
   CREATE TABLE [dbo].[DatabaseVersion]
   (
       [Version] INT NOT NULL PRIMARY KEY,
       [ReleasedOn] DATETIME NOT NULL,
       [ReleaseNotes] NVARCHAR(MAX) NULL
   )
   ```
2. Create dacpac snapshot using Visual Studio IDE
   1. Names should be generated in a sequential manner ([SnapshotName].[versionNumber].dacpac)
3. Generate new migration folder in **Migrations** folder
   1. **Version 0 to 1**
      1. PreDeploy.sql
      2. PostDeploy.sql
4. Update VersionCheck script
5. Update VersionInsert script