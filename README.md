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

TODO

## Desiderata

- Principles
  - Generic
    - As much of the same tooling should apply for cortical or fly, for example
      - Maybe requires setting intelligent defaults at runtime based on what you care about, e.g. for skeletonization radius parameters or something
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
  - Topology
    - Sholl analysis
    - Branch order
    - Strahler order
  - Density of points along an object
  - NBLAST
  - Checking if objects are in a volume
  - Alignment and deformation
- IO
  - SWC
  - Output to blender
  - Output to neuroglancer
- Neuron collection
  - Ability to do things like apply, map etc over a set of neurons
  - Groupby
- Metadata
  - Store metadata about the neuron
  - Store metadata about the annotations
  - Store metadata about the mesh and/or skeleton
- Mutability
  - E.g turn edits off or on
- Extensible
  - Allow subclassing
  - Having a base abstract class could help with this?
- Visualization
  - 1D (-ish)
    - Abstract, linear representation of a neuron
  - 2D
    - 2D projection of a 3D neuron
    - 2D _embedding_, not necessarily a projection
  - 3D
- Support for "featurization" of neuron morphologies
  - Define an API for people to add their own models which operate on these objects
- Support for fragments of neurons and compositional logic
  - E.g. dendrite + axon + soma = neuron?
- Deal with non-neuronal things, like layer or region bounds/masks
  - E.g. apply a parcellation to a neuron

## Questions

- Interest in SWC++?
-
