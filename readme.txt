1��ÿ�������������Ա����ţ�������ֺ�Email��ַ
	$ git config --global user.name "Your Name"
	$ git config --global user.email "email@example.com"

2�������ֿ�
	$ mkdir learngit        �����ֿ��ļ���
	$ cd learngit           ���ļ���(ͬʱҲ�Ǵ������������� cd D:)
	$ pwd                   �û���ʾ��ǰĿ¼
	$ git init              �����Ŀ¼���Git���Թ���Ĳֿ�
	��touch readme.txt
	��$ git add readme.txt          ����Git�����ļ���ӵ��ֿ�
	$ git commit -m "������ע��"    ����Git�����ļ��ύ���ֿ�

	$ git status   	        ������ʱ�����ղֿ⵱ǰ��״̬���鿴��Щֻ���޸Ĺ�,����û���ύ

	$ git diff+�ļ�         ���������޸���ʲô����

3���汾����
	
	$ git log               ��ʾ���������Զ���ύ��־


	�١�����ǻص���ǰ�汾

	$ git reset --hard HEAD^ 
	��^������һ���汾 ^^���ϰ汾 ����100����������дHEAD~100��


	�ڡ������ָ���ص�δ����ĳ���汾
	
	$ git reset --hard+commit id 
	�����commit id������git log�鿴�汾���״̬��

	$ git  reflog            ��ʾ���ÿһ������


4�����������ݴ���

	1����һ������git add���ļ���ӽ�ȥ��ʵ���Ͼ��ǰ��ļ��޸���ӵ��ݴ���
	2���ڶ�������git commit�ύ���ģ�ʵ���Ͼ��ǰ��ݴ��������������ύ����ǰ��֧��



