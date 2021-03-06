# np2ply.PLYWriter

This repo was built for exporting .ply files from numpy arrays. It's mainly meant to be used by the Taichi users and GAMES201 followers to conveniently playback their simulation in Houdini.

## Usage
```
from np2ply import PLYWriter

# set up the PLYWriter
writer = PLYWriter(num_vertices=20, num_faces=5, face_type="quad")
# Note
#      num_vertices is required and must be a positive integer
#      num_faces is optional, default to 0
#      face_type can be either "tri" or "quad", default to "tri"

# fill required channels
writer.add_vertex_pos(x,y,z)
writer.add_faces(findices)
# Note
#      .add_faces is unnecessary if num_faces is 0

# fill optional channels
writer.add_vertex_normal(vn[0,:], vn[1,:], vn[2,:])
writer.add_vertex_rgba(r,g,b,a)
writer.add_vertex_id()
writer.add_vertex_piece(np.ones(20))
writer.add_vertex_channel("vdata1", "float", vdata1)
writer.add_vertex_channel("vdata2", "uint", vdata2)
writer.add_face_id()
writer.add_face_piece(2*np.ones(5))
writer.add_face_channel("fdata", "float", fdata)

# export binary ply file
writer.export("example.ply")

# export ascii ply file
writer.export_ascii("example_ascii.ply")
```