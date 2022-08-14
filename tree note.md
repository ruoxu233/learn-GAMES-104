# videos
## 第一节：游戏引擎导论 1:15:42
## 第二节：引擎架构分层 1:06:52
## 第三节：如何构建游戏世界 59:18
## 第四节：游戏引擎中的渲染实践 1:40:57
## 第五节：渲染中光和材质的数学魔法 2:08:37
### basic light
Blinn-Phong model:Blinn-Phong reflection = ambient + diffuse + specular
    light = simple_light + ambient_light
    material = Blinn-Phong material
    shadow_map
### pre-computed global illumination
Spherical_Harmonics
    SH_lightmap
        1. parameterized all scence into 2D alias
        11. calculate irradiance probes
        12. compress probes into SH_coefficients
        2. store SH_coefficients into 2D alias textures
    light_promps + reflection_probes
        3D SH_coefficients
        add dynamic objects
        handle both diffuse and specular shading
### phisical based material{PDR}
if microfaces_theory is true: 
    BRDF model

normal distribution function

geometric attenuation term (self-shadowing)

fresnel equation

disney principled BRDF
    disney princuple material parameters

PBR specular glossiness
-> PBR metaillic roughness

### Image-Based Lighting (IBL)
### classic shadow solution
cascade shadow
PCF
percentage closer soft shadow{PCSS}
variance soft shadow map

### moving wave of high quality
real time ray traing

real time global illumination
    screen space
    SDF based
    voxel based
    RSM/ RTX

### virtual shadow maps
1:53:52


## 第六节(上)：游戏中地形大气和云的渲染1:16:37

### geomatrix
heightfield
-> mesh grids

adaptive mesh tessellation
    triangle-based subdivision
    quadtree-based subdivision
        solving T-junction among quad grids
    triangulated irregular network{TIN}

hardware tessellation{directX11}
    hull-shader stage(oringle triangle)
    tessellator stage: return small triangle
    domain stage: return 3D small triangle
-> mesh shader pipeliner{directX12}

real time deformable terrain

volumetric representation
    marching cubes
    transition cell lookup table

### material
use [#phisical based material{PDR}]

texture splatting:
    simple blending
        return texture1.rgb * a1 + texture2.rgb * a2
    blending with height
        return height1 > height2?texture1.rgb:texture2.rgb
    blending with height + biased

sampling from material texture array

parallax and displacement mapping
    color mapping
    bump mapping
    parallax mapping
    displacement mapping

virtual texture{VT}
    VT implementationm, direct storge and DMA

floating-point precision error
    camera relative rendering

tree rendering
decorator rendering
road and decals rendering
procedure terrain


## 第六节(下)：游戏中地形大气和云的渲染 59:38
### atmosphere theory
analytic atmosphere appearance modeling(angle1,angle2):
    return light

participating media & light{radiative transfer equation{RTE}}:
    absorption
    out-scattering
    emission
    in-scattering
-[intergre]-> volume rendering equation{VRE}

scattering
    Rayleigh scattering
        particle < wavelength
        if wavelength++
            scattering--
    Mie scattering
        partical > wavelength
    
absorption
    Ozone{O3}
    Methane{CH4}

single scattering
-> multi scattering

ray marching

### sky

precomputed atmospheric scattering
-> production quick sky and atmosphere renfering


### cloud

mesh based cloud modeling
billboard cloud
volumetric cloud modeling

noise functions:
    perlin noise
    worley noise
    voronoi

cloud density model:
    basic distribustion
    basic shape
    more details

randering cloud by ray marching

## 第七节：游戏中渲染管线、后处理和其他的一切 1:58:51
### ambient occlusion{AO, approxmation of attenuation of ambient light}
precomputed AO

screen space ambient occlusion{SSAO}
-> SSAO+
horizon based ambient occlusion{HBAO}
groud truth based ambient occlusion{GTAO}
ray tracing ambient occlusion

### fog
height fog:
    linear
    exp
    exp square
voxel based volumetric fog:


### anti aliasing{AA}
when high frequency to low frequency need anti aliasing

Super-sample AA{SSAA} and Multi sample AA{MSAA}
Fast approximate AA{FXAA}
    horizontal convolution + vertical convolution
    blend nearbt pixels
temporal AA{TAA}


### post process
bloom
    lenses can never focus perfectly
    airy disk
tone mapping
    no way to directly display HDR image in a SDR device
    high dynamic range to standard dynamic range
    
    tone mapping curve:
        filmic s-curve
    academy color encoding system{ACES}

color grading{lookup table}


### pipline
forward rendering
deferred rendering
    rendering G-buffer
        albedo, specular, normals, depth
tile based renderingdddd
tile based deferred rendering
forward+ (tile based) rendering
cluster based rendering
visibility buffer

### frame graph{directed acyclic graph}

### V-syns & G-syns

### homework 2


## 第八节(上)：游戏引擎的动画技术基础 1:14:26

### 2d animation
sprite animation
-> live2D

### 3d animation
rigid hierarchical animation
morph target animation
3D skinned animation
    2D skinned animation
physics based animation
    -> per-vertex animation

#### animation content creation

digital content creator + animator
motion capture
deep learning

### skinned animation implementation

T-pose < A-pose

skeleton pose

### math of 3D rotation
euler angle
    use in place a object, can not interpolate
quaternion --> matrix mult --> rotaton_matrix(axis,rotation_angle)



## 第八节(下)：游戏引擎的动画技术基础 52:12

### join pose orientation, position, scale


### animation compression


### animation DCC


## 第九节：高级动画技术：动画树、IK和表情动画 1:46:55

### animation blend
### inverse kinematics
### animation pipeline
### animation graph
### facial animation
### retargeting

## 番外：104播放20万了，来唠唠嗑 04:05
## 第十节：游戏引擎中物理系统的基础理论和算法 | GAMES104-现代游戏引擎：从入门到实践 2:07:17
## 第十一节：物理系统：高级应用 | GAMES104-现代游戏引擎：从入门到实践 ## 2:02:40 