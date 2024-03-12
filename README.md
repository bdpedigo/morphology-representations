# morphology-representations

## MeshParty

<!-- ```mermaid
flowchart TD

meshparty
iterator.py
mesh_filters.py
mesh_skel_utils.py
meshlabserver.py
ray_tracing.py
skeleton.py
skeleton_io.py
skeleton_utils.py
skeletonize.py
spatial_annotations.py
trimesh_io.py
trimesh_repair.py
trimesh_vtk.py
utils.py
utils_io.py
``` -->

### Modules/code

- meshwork
  - meshwork.py
    - `AnchoredAnnotationManager`
    - `AnchoredAnnotation`
      - Takes in a name, data, maybe a mesh, mask, point_array, etc.
    - Meshwork
      - Combo of a mesh, skeleton, a little bit of metadata
      - `self._anno` is an `AnchoredAnnotationManager`
    - add/anchor/remove annotations
    - masking
    - mapping between mesh and skeleton
    - branch points
    - distance computations
    - linear density
    - visualization
    - io
    - HDF5 loading?
  - meshwork_io.py
  - algorithms.py
    - `split_axon_by_synapses` (synapse flow centrality?)
- skeleton_quality
- iterator.py
- mesh_filters.py
- mesh_skel_utils.py
- meshlabserver.py
- ray_tracing.py
- skeleton.py
- skeleton_io.py
- skeleton_utils.py
- skeletonize.py
- spatial_annotations.py
- trimesh_io.py
- trimesh_repair.py
- trimesh_vtk.py
- utils.py
- utils_io.py

### Notes

- Feels like the `_MeshIndex`, `_SkeletonIndex` things are special cases of a more general mapping between objects?
- Hard to understand at a glance how all of the mappings between sub-objects work, indices, etc.
- Bespoke way of storing the object

## Navis

## Desiderata

- Representation itself
  - Represent a mesh and/or a skeleton together
  - Represent point annotations mapped to the mesh and/or the skeleton
    - Synapses as a special case of this
  - Represent "segment" annotations mapped to the mesh and/or the skeleton
    - E.g. "axon", "dendrite", "soma"
- Operations (simpler)
  - Masking
  - Topology
    - Branch points
    - End points
    - Roots
    - Checking if tree
    - Traversing the tree (e.g. `jump_distal/proximal`)
    - Path distance to root or to another point
    - Decomposing into segments
  - Density of points along an object
- Algorithms (heavier)
  - Conversion between representations
    - Marching cubes
    - Skeletonization
  - Synapse flow centrality
  - Branch order (how many branch points between node and root)
  - Strahler order
  - Density of points along an object
- IO
  - SWC
- Neuron collection
- Visualization
  - 1D (-ish)
    - Abstract, linear representation of a neuron
  - 2D
    - 2D projection of a 3D neuron
    - 2D _embedding_, not necessarily a projection
  - 3D

## Questions

- Interest in SWC++?
-
