# Install notes OpenFOAM on CentOS 7.6
#### Install notes
Following the notes of [openfoamwiki](https://openfoamwiki.net/index.php/Installation/Linux/OpenFOAM-6/CentOS_SL_RHEL#CentOS_7.5_.281804.29) below, installing OpenFOAM -6 from the OpenFOAM git repository on CentOS 7.6.1810 x86_64 more or less worked out of the box.

The only difference was that an OpenGL error occured for paraFoam. Recompiling ParaView with the "-rendering OpenGL" option resolved the issue:

```bash
cd $WM_THIRD_PARTY_DIR
./makeParaView -rendering OpenGL -mpi -python -qmake $(which qmake-qt4) > log.makePV 2>&1
```

#### Sources
https://openfoamwiki.net/index.php/Installation/Linux/OpenFOAM-6/CentOS_SL_RHEL#CentOS_7.5_.281804.29