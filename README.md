# jme3-testdata

Test data for the jMonkeyEngine examples and tests.

Maven Central: `org.jmonkeyengine:jme3-testdata`

## Releases

Releases are started by hand: run the **Release to Maven Central** workflow
(`.github/workflows/release.yml`) from the Actions tab. The run computes the
version of the day in `YYYY-MM-DD` form, pushes the matching tag, creates the
GitHub release with that name and then publishes the artifact to Maven Central.

A second release on the same day gets a counter as suffix, and the counter
resets the next day:

| Release of the day | Version |
|---|---|
| 1st | `2026-09-19` |
| 2nd | `2026-09-19-2` |
| 3rd | `2026-09-19-3` |
| 1st of the next day | `2026-09-20` |

Publishing credentials are checked before creating a tag or GitHub release. If a
release run fails, rerun it from the Actions tab: once its tag has been pushed,
every attempt reuses the same version and GitHub release, even on a later day.
An upload that a previous attempt recorded as successful is skipped. A new
manual dispatch starts a separate release and allocates a new version.

Every push to `master` triggers the **Publish snapshot to Maven Central** workflow
(`.github/workflows/snapshot.yml`), publishing
`org.jmonkeyengine:jme3-testdata:<YYYY-MM-DD>-SNAPSHOT`. Snapshot uploads are
serialized without cancelling an upload in progress. Runs whose commit is no
longer the head of `master` are skipped before uploading, so a queued run or a
rerun of an older commit cannot replace a newer snapshot.

The version of the day and the counter are computed by
[`scripts/next-version.sh`](scripts/next-version.sh), covered by
[`scripts/next-version-test.sh`](scripts/next-version-test.sh).

## Licenses

The assets themselves are third-party test data under mixed licenses.

| Asset | Author | License |
|---|---|---|
| Sinbad character | Zi Ye | CC BY-SA 3.0 |
| LightProbes (Quarry 03) | Sergej Majboroda | CC0 |
| Lagoon skybox | hazelwhorley.com | CC BY-NC 3.0 |
| PBR terrain textures | cc0textures.com | CC0 |
| Jaime character | nehon | BSD (same as jMonkeyEngine) |
| Duck (glTF sample) | Sony Computer Entertainment | SCEA Shared Source License 1.0 |
| Utah Teapot | Martin Newell | Public domain |
| Cornell Box | Cornell University | unclear |
| Sponza atrium | Frank Meinl / Crytek | CC BY |
| MonkeyHead (Suzanne) | unclear | unclear |
| TwoChairs.obj | unclear | unclear |
| PBR scene | nehon | unclear |
| Ferrari | author unknown | unclear |
| town.zip, wildhouse.zip (demo scenes) | author unknown | unclear |
| Ninja, Oto, Elephant, Buggy, Boat, Tank, HoverTank, SpaceCraft, Tree and other test models | author unknown | unclear |
| Beach, DotScene, ManyLights scenes | author unknown | unclear |
| Sounds, explosion/smoke sprites, interface graphics, other test textures | author unknown | unclear |
