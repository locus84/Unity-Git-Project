Unity Git Project
=================
An empty Unity project, setup for proper use with Git.

## What it offers
#### Gitignore
A gitignore file that ignores Unity's folders `library` and `temp`, as well as Visual Studio project files and some others.

It's very similar to https://github.com/github/gitignore/blob/master/Unity.gitignore

#### Git LFS
Integrates `Git Large File Storage` to handle binary assets.

The files tracked Git LFS are:
* Image files (`bmp`, `exr`, `gif`, `hdr`, `iff`, `jpg`, `jpeg`, `pict`, `png`, `psd`, `tga`, `tiff`)<br>
  (based on https://docs.unity3d.com/Manual/ImportingTextures.html)
* Audio files (`mp3`, `ogg`, `wav`, `aif`, `aiff`, `mod`, `it`, `s3m`, `xm`)<br>
  (based on https://docs.unity3d.com/Manual/AudioFiles.html)
* Video files (`mov`, `mpg`, `mpeg`, `mp4`, `avi`, `asf`)<br>
  (based on https://docs.unity3d.com/Manual/class-MovieTexture.html)
* 3D model files (`fbx`, `dae`, `3ds`, `dxf`, `obj`, `skp`, `blend`, `c4d`)<br>
  (based on https://docs.unity3d.com/Manual/3D-formats.html)

#### UnityYAMLMerge
Since Unity 5, Unity includes a simple text-based mergetool for Unity files (scenes, prefabs, .asset files).
The files `.gitconfig` and `.gitattributes` make it the mergetool for all three of these files.

.asset files include ScriptableObjects and ProjectSettings files.

## How to use
Download or fork this repository, then open the project with Unity.

Alternatively, copy these files into your project's root folder:
* `.gitattributes`
* `.gitconfig`
* `.gitignore`

Make sure that `Git LFS` is installed on every system in the project. See https://git-lfs.github.com/ for more info.

By default, the UnityYAMLMerge path is set to the Windows 64-bit path.
Please check https://docs.unity3d.com/Manual/SmartMerge.html for the paths for other systems
and change the .gitconfig file on your local machine accordingly.

Consider running `git update-index --skip-worktree .gitconfig` in order to not commit your custom Unity path.

Alternatively, do not add the provided `.gitconfig` file to your project, but rather copy its contents to your global `.gitconfig`, located in your home folder. Do this once for every participant.

If you have problems adding this to your global config, use these commands instead:
```
git config --global merge.tool unityyamlmerge
git config --global mergetool.unityyamlmerge.cmd "<path-to-untyyamlmerge> merge -p \"\$BASE\" \"\$REMOTE\" \"\$LOCAL\" \"\$MERGED\""
```
