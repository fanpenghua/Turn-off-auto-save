һ���ر��Զ��޶����ܺ��Զ����湦��
��Ŀ¼���ҵ�wp-config.php
��define('WP_DEBUG', false);�������
define('WP_POST_REVISIONS', false); //�ر��Զ��޶�����
define('AUTOSAVE_INTERVAL', 86400); //�����Զ�����ʱ��Ϊһ�죬�ﵽ����ر��Զ������Ŀ�ġ�


/wp-admin/index.php  -- ȥ�� �� ��ҳ������һ�� �ݸ�ĵĴ����������BUG

<?php wp_dashboard(); ?>


/wp-admin/includes/post.php -- 'post_status' => auto-draft ��Ϊ draft (���Զ��ݸ壬��Ϊ�ݸ塣����ID����)

469 ��
$post_id = wp_insert_post( array( 'post_title' => __( 'Auto Draft' ), 'post_type' => $post_type, 'post_status' => 'auto-draft' ) );



����Wordpress�ϴ��ļ���������Ľ��������MD5ת�ļ�����
�ҵ�/wp-admin/includes/file.php����ļ���

�ҵ�329��


// Move the file to the uploads dir
//$new_file = $uploads['path'] . "/$filename";




�����ϴ���֮ǰ�����������

//MD5���ܣ����������ļ�
$shawnee_name = substr(md5(substr($filename,0,-4).time()),0,12);
$shawnee_ext = substr($filename,-4);
$filename = $shawnee_name.$shawnee_ext;

�������ļ�����ת��