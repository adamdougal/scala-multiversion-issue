### Project to demonstrate issue https://github.com/ADTRAN/gradle-scala-multiversion-plugin/issues/5

## Happy Case

When running the same task for all projects:

```bash
>> ./gradlew dummy --dry-run

:subproject1:dummy SKIPPED
:subproject2:dummy SKIPPED
:subproject1:recurseWithScalaVersion_2.11.11 SKIPPED

BUILD SUCCESSFUL in 0s
```

This works fine and as expected.

## Unhappy case

When I just run the dummy task for `subproject2` it will still recurse `subproject1`:

```bash
>> ./gradlew subproject2:dummy --dry-run

:subproject2:dummy SKIPPED
:subproject1:recurseWithScalaVersion_2.11.11 SKIPPED

BUILD SUCCESSFUL in 0s
```

No tasks in `subproject1` should have been run.