# RAWLS reader

## Description

Read and convert `.rawls` generated syntehsis image format into `.ppm`.

`.rawls` store all pixels values as *float* and keeps also information about generated image (renderer used).

`.rawls` contains 3 blocks and specific lines information within each block:
- IHDR: 
    - **First line:** next information line size into byte
    - **Second line:** `{width}` `{height}` `{nbChannels}`
- COMMENTS
    - **All lines:** information from the renderer as comment
- DATA
    - **First line:** data block size
    - **Next lines:** all pixels values as byte code at each line

Example of `.rawls` file:
```rawls
IHDR
12
�   �      
COMMENTS
#Samples 100
#Filter 
  #params 
#Film image
  #params "integer xresolution" [1000 ] "integer yresolution" [1000 ] "string filename" ["killeroo-simple.rawls_20" ] 
#Sampler halton
 #params "integer pixelsamples" [8 ] 
#Accelerator 
  #params 
#Integrator path
  #params 
#Camera perspective
  #params "float fov" [39 ] 
#LookAt 400 20 30  0 63 -110  0 0 1
DATA
12000000
BABBAB_��B
��YB��YBY�B
@=B@=B��B
��3B��3B��jB
....
+Z<BZ<B2\zB
��OB��OB���B
```

## How it works ?

```
make compile
```

Convert the `.rawls` image format into `.ppm` 
```
./rawls_reader --image ../path/to/image.rawls_20 --outfile image.ppm
```