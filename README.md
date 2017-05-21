# Reoriented Normal Mapping
This repository constains the code for <i>Reoriented Normal Mapping</i> [1], a technique to compute proper blending of tangent space normals via quaternion rotation. 

<img src="https://github.com/zigguratvertigo/ReorientedNormalMapping/blob/master/Website/RNM.png">

The code is provided in the form of a RenderMonkey project. You can download RenderMonkey [here](http://gpuopen.com/archive/gamescgi/rendermonkey-toolsuite/).

Additional details regarding the technique and how it compares to other approaches can be found [here](http://blog.selfshadow.com/publications/blending-in-detail/).

# Implementation Summary
<img src="https://github.com/zigguratvertigo/ReorientedNormalMapping/blob/master/Website/RNM2.png">

```hlsl
float3 t = tex2D(BaseNormal, uv) * float3(2, 2, 2) + float3(-1, -1, 0);
float3 u = tex2D(DetailNormal, uv) * float3(-2, -2, 2) + float3(1, 1, -1);
float3 r = t * dot(t, u) / t.z – u;
```

# References
[1] Barré-Brisebois, Colin and Hill, Stephen. "Blending in Detail - Reoriented Normal Mapping", 2012, [Available Online](http://blog.selfshadow.com/publications/blending-in-detail/).
