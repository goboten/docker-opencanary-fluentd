Opencanary�ƘA�g���邽�߂�fluentd���\�z���邽�߂�Dockerfile�ł��B

docker�C���[�W�\�z�T���v���̓p�u���b�N�C���[�W���Q�l�ɂ��Ă��܂��Bhttps://hub.docker.com/r/fluent/fluentd/   

�C���[�W���쐬���邽�߂ɓK���Ȗ��O�Ńf�B���N�g�����쐬���܂��B(�����ł�fluent�Ƃ��܂�)  
�ȉ��̗l�Ƀt�@�C����z�u���܂�

 fluent/  
 ������ Dockerfile  
 ������ fluent.conf <- �_�~�[�t�@�C���Ȃ̂�0byte�̋�t�@�C�����쐬���Ă��܂��B  
 ������ plugins/  

fluent�t�H���_��fluent.conf��plugins�t�H���_�̓p�u���b�N�C���[�W����쐬����Ƃ��ɕK�v�ƂȂ邽�ߍ쐬�������܂��B  
Dockerfile�ɂ��Ă��p�u���b�N�y�[�W�ɏ�����Ă�����e�̃v���O�C���� fluent-plugin-elasticsearch �� fluent-plugin-record-reformer ��ǉ����Ă��邾���ł��B  
���Ƃ́A�N���I�v�V�����ŋ��fluent.conf��ݒ�ς݂�fluent.conf�ɍ����ւ��邾���ł��B  
�����ւ��邽�߂� fluent.conf ��ۑ�����f�B���N�g����p�ӂ��܂��B  
�����ւ��p��fluent.conf��dist�f�B���N�g����fluent.conf�ƂȂ�܂��B  
 
 /fluentd/  
 ������ etc/  
     ������ fluent.conf  

����́A�N�����ɓǂݍ���fluent.conf�̑��M���ύX���邽�߂Ɏg�p���Ă��܂��B  
���̂��߁A���ۂɓ��������߂�fluent.conf��z�u���Ă��������B  

�����āAdocker�t�@�C������C���[�W���쐬����͈̂ȉ��̃R�}���h�ō쐬���Ă��܂��B  
$ sudo docker build -t fluentd ./  

�N���͈ȉ��̃R�}���h�ƂȂ�܂��B  
$ sudo docker run --name fluentd -d -p 1514:1514 -v /fluentd/etc:/fluentd/etc fluentd

