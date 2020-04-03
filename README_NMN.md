export GIT_HASH=`git log -1 --pretty=format:"%H"`

docker build -f Dockerfile.nmn_drop -t gcr.io/ai2-reviz/allennlp-demo-nmn-drop:$GIT_HASH .

docker run -p 8000:8000 \
	-v $HOME/.allennlp:/root/.allennlp \
	--rm \
	gcr.io/ai2-reviz/allennlp-demo-nmn-drop:$GIT_HASH \
	--model nmn-drop

docker push gcr.io/ai2-reviz/allennlp-demo-nmn-drop:$GIT_HASH
