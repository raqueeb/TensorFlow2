PS C:\Users\Test> docker pull tensorflow/serving

Using default tag: latest
latest: Pulling from tensorflow/serving
22e816666fd6: Pull complete
079b6d2a1e53: Pull complete 
11048ebae908: Pull complete                                                                                                             
c58094023a2e: Pull complete                                                                                                             
4dee0153a839: Pull complete                                                                                                             
90850b98765d: Pull complete                                                                                                             
de0a35913cb5: Pull complete                                                                                                             
91e09abfcd7f: Pull complete                                                                                                             
Digest: sha256:091c1d0440815e250114a6d0232ad3cb1d320c64b1ebb75ed8a80184fc25482d
Status: Downloaded newer image for tensorflow/serving:latest
docker.io/tensorflow/serving:latest



$ git clone https://github.com/tensorflow/serving

Cloning into 'serving'...
remote: Enumerating objects: 54, done.
remote: Counting objects: 100% (54/54), done.
remote: Compressing objects: 100% (52/52), done.
Receiving objects:  48% (9475/19738), 3.61 MiB | 195.00 KiB/s
remote: Total 19738 (delta 36), reused 20 (delta 2), pack-reused 19684
Receiving objects: 100% (19738/19738), 5.22 MiB | 178.00 KiB/s, done.
Resolving deltas: 100% (14964/14964), done.



PS E:\git_portable> docker run -t --rm -p 8501:8501 -v "E:\git_portable\serving\tensorflow_serving\servables\tensorflow\testdata\saved_model_half_plus_two_cpu:/models/half_plus_two" -e MODEL_NAME=half_plus_two tensorflow/serving

2019-11-10 07:11:17.037045: I tensorflow_serving/model_servers/server.cc:85] Building single TensorFlow model file config:  model_name: half_plus_two model_base_path: /models/half_plus_two
2019-11-10 07:11:17.037797: I tensorflow_serving/model_servers/server_core.cc:462] Adding/updating models.
2019-11-10 07:11:17.037861: I tensorflow_serving/model_servers/server_core.cc:573]  (Re-)adding model: half_plus_two
2019-11-10 07:11:17.158245: I tensorflow_serving/core/basic_manager.cc:739] Successfully reserved resources to load servable {name: half_plus_two version: 123}
2019-11-10 07:11:17.158435: I tensorflow_serving/core/loader_harness.cc:66] Approving load for servable version {name: half_plus_two version: 123}
2019-11-10 07:11:17.158496: I tensorflow_serving/core/loader_harness.cc:74] Loading servable version {name: half_plus_two version: 123}
2019-11-10 07:11:17.158573: I external/org_tensorflow/tensorflow/cc/saved_model/reader.cc:31] Reading SavedModel from: /models/half_plus_two/00000123
2019-11-10 07:11:17.170610: I external/org_tensorflow/tensorflow/cc/saved_model/reader.cc:54] Reading meta graph with tags { serve }
2019-11-10 07:11:17.172642: I external/org_tensorflow/tensorflow/core/platform/cpu_feature_guard.cc:142] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2 FMA
2019-11-10 07:11:17.212202: I external/org_tensorflow/tensorflow/cc/saved_model/loader.cc:202] Restoring SavedModel bundle.
2019-11-10 07:11:17.230431: I external/org_tensorflow/tensorflow/cc/saved_model/loader.cc:151] Running initialization op on SavedModel bundle at path: /models/half_plus_two/00000123
2019-11-10 07:11:17.236016: I external/org_tensorflow/tensorflow/cc/saved_model/loader.cc:311] SavedModel load for tags { serve }; Status: success. Took 77445 microseconds.
2019-11-10 07:11:17.237262: I tensorflow_serving/servables/tensorflow/saved_model_warmup.cc:105] No warmup data file found at /models/half_plus_two/00000123/assets.extra/tf_serving_warmup_requests
2019-11-10 07:11:17.247605: I tensorflow_serving/core/loader_harness.cc:87] Successfully loaded servable version {name: half_plus_two version: 123}
2019-11-10 07:11:17.250931: I tensorflow_serving/model_servers/server.cc:353] Running gRPC ModelServer at 0.0.0.0:8500 ...
[warn] getaddrinfo: address family for nodename not supported
2019-11-10 07:11:17.252948: I tensorflow_serving/model_servers/server.cc:373] Exporting HTTP/REST API at:localhost:8501 ...


![Curl](../assets/curl.png "Curl call")


PS E:\git_portable> docker ps

CONTAINER ID        IMAGE                                                    COMMAND                  CREATED             STATUS              PORTS                              NAMES
c6e0b94c10b9        tensorflow/tensorflow:2.0.0-py3-jupyter-pandas-sklearn   "bash -c 'source /et…"   2 hours ago         Up 2 hours          0.0.0.0:8888->8888/tcp             tensorflow2
c0a477f441fb        tensorflow/serving                                       "/usr/bin/tf_serving…"   2 hours ago         Up 2 hours          8500/tcp, 0.0.0.0:8501->8501/tcp   hungry_robinson


PS E:\git_portable> curl -d '{"instances": [1.0, 2.0, 5.0]}' -X POST http://localhost:8501/v1/models/half_plus_two:predict

Invoke-WebRequest : A parameter cannot be found that matches parameter name 'X'.
At line:1 char:42
+ curl -d '{"instances": [1.0, 2.0, 5.0]}' -X POST http://localhost:850 ...
    + CategoryInfo          : InvalidArgument: (:) [Invoke-WebRequest], ParameterBindingException
    + FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.InvokeWebRequestCommand


tensorflow / tensorflow : 2.0.0rc0-py3-jupyter

docker pull tensorflow/tensorflow:2.0.0-py3-jupyter

Working

docker run -it -p 8888:8888 -v "c:/users/test/google drive/dlbook:/tf" --rm --name tensorflow2 tensorflow/tensorflow:2.0.0-py3-jupyter-pandas 

docker run -it -p 8888:8888 -v "c:/users/test/google drive:/tf" --rm --name tensorflow2 tensorflow/tensorflow:2.0.0-py3-jupyter-pandas 

docker run -it -p 8888:8888 -v "c:/users/test/google drive:/tf" --rm --name tensorflow2 tensorflow/tensorflow:2.0.0-py3-jupyter

docker run -it -p 8888:8888 -v "c:/users/test/google drive/dlbook:/tf" --rm tensorflow/tensorflow:2.0.0-py3-jupyter --restart unless-stopped

docker run -it -p 8888:8888 -v "c:/users/test/google drive/dlbook:/tf" tensorflow/tensorflow:2.0.0-py3-jupyter


docker run -it -p 8888:8888 -v e:/posts:/tf --rm tensorflow/tensorflow:2.0.0-py3-jupyter

docker run -it -p 8888:8888 -v ${PWD}:/tf --rm tensorflow/tensorflow:2.0.0-py3-jupyter

-v ${PWD}

docker run -it -p 8888:8888 -v C:/Users/Test/Google Drive/DLbook:/tf --rm tensorflow/tensorflow:2.0.0-py3-jupyter

"C:\Users\Test\Google Drive\DLbook"

docker run -it -p 8888:8888 -v e:/posts:/tf --rm tensorflow/tensorflow:2.0.0-py3-jupyter

docker run -it -p 8888:8888 tensorflow/tensorflow:2.0.0-py3-jupyter

docker run -it -p 8888:8888 tensorflow/tensorflow:2.0.0rc0-py3-jupyter

docker run -it -p 8888:8888 -v C:\Users\Mr. raqueeb\Documents:/tmp --rm --name tensorflow2 tensorflow/tensorflow:2.0.0rc0-py3-jupyter

docker run -it -p 8888:8888 -v C:\ProgramData\Docker:/tmp --rm --name tensorflow2 tensorflow/tensorflow:2.0.0rc0-py3-jupyter

docker run -it -p 8888:8888 -v C:\ProgramData\Docker:/notebook --rm --name tensorflow2 tensorflow/tensorflow:2.0.0rc0-py3-jupyter

docker run -it p 8888:8888 --volume //e/posts:/tf -rm --name tensorflow2 tensorflow/tensorflow:2.0.0-py3-jupyter

docker create -t -i -v i:/project/web01:/mnt/test fedora /bin/bash

docker run -it p 8888:8888 -v e:/posts:/tf -rm --name tensorflow2 tensorflow/tensorflow:2.0.0-py3-jupyter

C:\ProgramData\Docker

docker pull tensorflow/tensorflow:latest-gpu-jupyter

docker container ls -a

docker container rm 7f6a0963b4fc

docker container stop $(docker container ls -aq)

docker run -it tensorflow/tensorflow:2.0.0-py3-jupyter /bin/bash
pip install pandas

docker export --output="tensorflow.tar" fc8da732849a

docker run tensorflow/tensorflow:2.0.0-py3-jupyter bash -c "apt-get update && apt-get install -y pandas"

PS C:\Users\Test> docker pull tensorflow/serving
Using default tag: latest
latest: Pulling from tensorflow/serving
22e816666fd6: Pull complete                                                                                                                                             079b6d2a1e53: Pull complete                                                                                                                                             11048ebae908: Pull complete                                                                                                                                             c58094023a2e: Pull complete                                                                                                                                             4dee0153a839: Pull complete                                                                                                                                             90850b98765d: Pull complete                                                                                                                                             de0a35913cb5: Pull complete                                                                                                                                             91e09abfcd7f: Pull complete                                                                                                                                             Digest: sha256:091c1d0440815e250114a6d0232ad3cb1d320c64b1ebb75ed8a80184fc25482d
Status: Downloaded newer image for tensorflow/serving:latest
docker.io/tensorflow/serving:latest


curl -d '{"instances": [1.0, 2.0, 5.0]}' -X POST http://localhost:8501/v1/models/half_plus_two:predict

curl -d '{"instances": [1.0, 2.0, 5.0]}' -X POST http://localhost:8501/v1/models/half_plus_two:predict

C:\WINDOWS\system32>curl -d "{\"instances\": [1.0, 5.0, 9.0]}" -X POST http://127.0.0.1:8501/v1/models/half_plus_two:predict
{
    "predictions": [2.5, 4.5, 6.5
    ]
}

E:\git_portable\serving\tensorflow_serving\servables\tensorflow\testdata\saved_model_half_plus_three


docker run -t --rm -p 8507:8507 -v "E:\git_portable\serving\tensorflow_serving\servables\tensorflow\testdata\saved_model_half_plus_three:/models/half_plus_three" -e MODEL_NAME=half_plus_three tensorflow/serving


curl -d "{\"instances\": [1.0,2.0,5.0]}" -X POST http://localhost:8507/v1/models/saved_model_half_plus_three:predict


PS E:\git_portable> docker run -t --rm -p 8507:8507 -v "E:\git_portable\serving\tensorflow_serving\servables\tensorflow\testdata\saved_model_half_plus_three:/models/half_plus_three" -e MODEL_NAME=half_plus_three tensorflow/serving
2019-11-10 16:32:41.006983: I tensorflow_serving/model_servers/server.cc:85] Building single TensorFlow model file config:  model_name: half_plus_three model_base_path: /models/half_plus_three
2019-11-10 16:32:41.007173: I tensorflow_serving/model_servers/server_core.cc:462] Adding/updating models.
2019-11-10 16:32:41.007190: I tensorflow_serving/model_servers/server_core.cc:573]  (Re-)adding model: half_plus_three
2019-11-10 16:32:41.112369: I tensorflow_serving/core/basic_manager.cc:739] Successfully reserved resources to load servable {name: half_plus_three version: 123}
2019-11-10 16:32:41.112428: I tensorflow_serving/core/loader_harness.cc:66] Approving load for servable version {name: half_plus_three version: 123}
2019-11-10 16:32:41.112460: I tensorflow_serving/core/loader_harness.cc:74] Loading servable version {name: half_plus_three version: 123}
2019-11-10 16:32:41.112493: I external/org_tensorflow/tensorflow/cc/saved_model/reader.cc:31] Reading SavedModel from: /models/half_plus_three/00000123
2019-11-10 16:32:41.190027: I external/org_tensorflow/tensorflow/cc/saved_model/reader.cc:54] Reading meta graph with tags { serve }
2019-11-10 16:32:41.190727: I external/org_tensorflow/tensorflow/core/platform/cpu_feature_guard.cc:142] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2 FMA
2019-11-10 16:32:41.210597: I external/org_tensorflow/tensorflow/cc/saved_model/loader.cc:202] Restoring SavedModel bundle.
2019-11-10 16:32:41.241783: I external/org_tensorflow/tensorflow/cc/saved_model/loader.cc:151] Running initialization op on SavedModel bundle at path: /models/half_plus_three/00000123
2019-11-10 16:32:41.247985: I external/org_tensorflow/tensorflow/cc/saved_model/loader.cc:311] SavedModel load for tags { serve }; Status: success. Took 135489 microseconds.
2019-11-10 16:32:41.249075: I tensorflow_serving/servables/tensorflow/saved_model_warmup.cc:105] No warmup data file found at /models/half_plus_three/00000123/assets.extra/tf_serving_warmup_requests
2019-11-10 16:32:41.257380: I tensorflow_serving/core/loader_harness.cc:87] Successfully loaded servable version {name: half_plus_three version: 123}
2019-11-10 16:32:41.261126: I tensorflow_serving/model_servers/server.cc:353] Running gRPC ModelServer at 0.0.0.0:8500 ...
[warn] getaddrinfo: address family for nodename not supported
2019-11-10 16:32:41.262500: I tensorflow_serving/model_servers/server.cc:373] Exporting HTTP/REST API at:localhost:8501 ...
[evhttp_server.cc : 238] NET_LOG: Entering the event loop ...
PS E:\git_portable>
PS E:\git_portable> docker ps
CONTAINER ID        IMAGE                                                    COMMAND                  CREATED             STATUS              PORTS                                   NAMES
5f0bb96c40ed        tensorflow/serving                                       "/usr/bin/tf_serving…"   7 minutes ago       Up 7 minutes        8500-8501/tcp, 0.0.0.0:8507->8507/tcp   epic_mendel
c6e0b94c10b9        tensorflow/tensorflow:2.0.0-py3-jupyter-pandas-sklearn   "bash -c 'source /et…"   9 hours ago         Up 9 hours          0.0.0.0:8888->8888/tcp                  tensorflow2
c0a477f441fb        tensorflow/serving                                       "/usr/bin/tf_serving…"   9 hours ago         Up 9 hours          8500/tcp, 0.0.0.0:8501->8501/tcp        hungry_robinson
PS E:\git_portable>
PS E:\git_portable> docker container stop $(docker container ls -aq)
5f0bb96c40ed
c6e0b94c10b9
c0a477f441fb


C:\WINDOWS\system32>curl -d "{\"instances\": [1.0, 5.0, 9.0]}" -X POST http://127.0.0.1:8501/v1/models/half_plus_two:predict
{
    "predictions": [2.5, 4.5, 6.5
    ]
}
C:\WINDOWS\system32>curl -d "{\"instances\": [1.0, 5.0, 9.0]}" -X POST http://localhost:8507/v1/models/saved_model_half_plus_three:predict
curl: (52) Empty reply from server

C:\WINDOWS\system32>curl -d "{\"instances\": [1.0, 5.0, 9.0]}" -X POST http://localhost:8501/v1/models/saved_model_half_plus_three:predict
{ "error": "Servable not found for request: Latest(saved_model_half_plus_three)" }
C:\WINDOWS\system32>curl -d "{\"instances\": [1.0, 5.0, 9.0]}" -X POST http://localhost:8507/v1/models/saved_model_half_plus_three:predict
curl: (52) Empty reply from server

C:\WINDOWS\system32>curl -d "{\"instances\": [1.0, 5.0, 9.0]}" -X POST http://localhost:8507/v1/models/saved_model_half_plus_three:predict
curl: (52) Empty reply from server

C:\WINDOWS\system32>curl -d "{\"instances\": [1.0, 5.0, 9.0]}" -X POST http://localhost:8507/v1/models/saved_model_half_plus_three:predict
curl: (52) Empty reply from server

C:\WINDOWS\system32>curl -d "{\"instances\": [1.0,2.0,5.0]}" -X POST http://localhost:8507/v1/models/saved_model_half_plus_three:predict
curl: (52) Empty reply from server

C:\WINDOWS\system32>curl -d "{\"instances\": [1.0,2.0,5.0]}" -X POST http://localhost:8500/v1/models/saved_model_half_plus_three:predict
curl: (7) Failed to connect to localhost port 8500: Connection refused

C:\WINDOWS\system32>curl -d "{\"instances\": [1.0,2.0,5.0]}" -X POST http://localhost:8501/v1/models/saved_model_half_plus_three:predict
curl: (7) Failed to connect to localhost port 8501: Connection refused

C:\WINDOWS\system32>curl -d "{\"instances\": [1.0,2.0,5.0]}" -X POST http://localhost:8507/v1/models/saved_model_half_plus_three:predict
curl: (52) Empty reply from server

C:\WINDOWS\system32>
