import os, subprocess

def get_files(directory):
  file_paths = []
  # Walk the tree.
  for root, directories, files in os.walk(directory):
    for filename in files:
      # Join the two strings in order to form the full filepath.
      filepath = os.path.join(root, filename)
      file_paths.append(filepath)  # Add it to the list.
  return file_paths

# Environment configuration
env = Environment(ENV=os.environ)
env.AppendUnique(PDFLATEXFLAGS='-synctex=1')
# Build all the figures in the tikz folder
SConscript('tikz/SConscript', variant_dir='figures', duplicate=0)

# Building function
def build_and_clean(filename, dependencies=None):
  pdf = env.PDF(filename + '.tex')
  if dependencies is not None:
    Depends(pdf, dependencies)
  env.Precious(pdf)
  # Clean up
  extensions = ['.synctex.gz', '.bbl', '.blg', '.bcf']
  for extension in extensions:
    env.Clean(pdf, filename + extension)
  env.Clean(pdf, 'SConstructc')
  env.Clean(pdf, '.sconsign.dblite')
  env.NoClean(pdf)

## PAPER
dependencies = ['references.bib']
dependencies = get_files('sections')
dependencies += get_files('figures')
build_and_clean('main', dependencies=dependencies)

## PRESENTATION
# build_and_clean('presentation')
