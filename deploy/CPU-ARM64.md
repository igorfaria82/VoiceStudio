# Native CPU / ARM64 container

Build from the repository root with `docker build -f deploy/Dockerfile.cpu .`.
This optional deployment preserves the maintained browser renderer and backend,
upstream licenses, entrypoint, and authentication. No CUDA/ROCm runtime or
architecture emulation is required. The frozen CPU dependency group is used.
Native builds require the included C/C++/CMake and Rust toolchains for sphn/Opus.

Persist `/app/omnivoice_data`; the backend listens on container port 3900.
Set a strong secret `OMNIVOICE_API_KEY` before startup. Keep host port mappings
and public proxy domains disabled until health and authentication have been
verified. Never bake credentials into the image or Git repository.

CPU inference can be substantially slower and individual optional engines may
have architecture-specific requirements. Successful image build does not verify
model downloads or inference. Models remain subject to their upstream licenses.
