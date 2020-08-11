# LintRemoveNode

Sample project for a bug where lint complains about a removed node in manifest.

To reproduce:
1) Clone this repo
2) Run :app:lintRelease task

The task will fail because ExportedContentProvider complains about the
LibContentProvider.

This is incorrect tho, for two reasons:
1) ExportedContentProvider isn't exported, as declared in lib manifest
   it has exported=false. If the &lt;provider&gt; node override removed from 
   main manifest no warning would be issued.

2) Even if ExportedContentProvider was exported, the fact that it is marked
   to be removed in the app manifest should still silence the check.
