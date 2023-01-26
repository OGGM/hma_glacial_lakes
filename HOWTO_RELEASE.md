**How to issue a hma glacial lake release**

1. Go to your local main repository (not the fork) and ensure your main branch is synced:
```
git checkout main
git pull
```
2. Edit `version.py` to reflect the new version number (`v1.3`, `v1.4`, etc.)
3. On the main branch, commit the release in git:
```
git commit -a -m 'Release v1.X'
```
4. Tag the release:
```
git tag -a v1.X -m 'v1.X'
```
5. Push your changes to main:
```
git push origin main
git push origin --tags
```
5. Update the stable branch and push it. "stable" is used as a shortcut to the latest stable version (for permalinks, etc.). It's OK to force-push to main if necessary:
```
git checkout stable
git rebase main
git push origin stable
git checkout main
```
6. Edit `version.py` to revert to the dev version (i.e. `v1.X+1.dev`: `v1.4.dev`, `v1.5.dev`, etc.)
7. Commit your changes and push to main again:
```
git commit -a -m 'Revert to dev version'
git push origin main
```
8. Edit the Bokeh server configuration file to publish the new version on OGGM-Edu: https://github.com/OGGM/Bokeh-Docker/blob/master/bokeh.oggm.org/docker-compose.yml (I don't want to update this to stable in order to actively control that it works and force a rebuild of the server)
9. Test MyBinder link and docker comment in OGGM-Edu doccumentation: https://github.com/OGGM/oggm-edu/blob/master/docs/hma_glacial_lakes.rst 
 
