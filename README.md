# comments-remover-using-python
Python Code snippet to remove "#" from the beginning of a line.

---
Opening the files using File handler. 
Source file sample.txt
---
cat sample.txt
```obtained by the selenium
defect operated browser is 
less when compared with 
the results that are 
obtained by me manually
datetime operating the browser.
```
The below code remove the # from the begining of the lines and write to a temporary file created with the 'tempfile' python module. Later the former is renamed to the actual file name
```sh
import sys,os,tempfile
usage = 'python3 uncommenter.py file_name'
file = sys.argv[1]

if len(sys.argv) == 2  and os.path.isfile(file) :
  fh_read = open(file)
  fh_write = tempfile.NamedTemporaryFile(mode='w',delete=False)
  tmpfile = fh_write.name

  for line in fh_read:
    if line.startswith('#'):
      line = line.lstrip('#')
      fh_write.write(line)
    else:
      fh_write.write(line) 

  fh_write.close() 
  os.rename(tmpfile,file)
  
else:
  print('Actual usage of the script is :', usage )

```

After the execution:
```
$ python3 uncommenter.py sample.txt

$ cat sample.txt
obtained by the selenium
defect operated browser is 
less when compared with 
the results that are 
obtained by me manually
datetime operating the browser. 
```
