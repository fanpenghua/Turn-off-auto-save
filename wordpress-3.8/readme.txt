一、关闭自动修订功能和自动保存功能
根目录下找到wp-config.php
在define('WP_DEBUG', false);后面填加
define('WP_POST_REVISIONS', false); //关闭自动修订功能
define('AUTOSAVE_INTERVAL', 86400); //设置自动保存时间为一天，达到变相关闭自动保存的目的。


/wp-admin/index.php  -- 去除 打开 此页面新增一条 草稿的的代码干扰属于BUG

<?php wp_dashboard(); ?>


/wp-admin/includes/post.php -- 'post_status' => auto-draft 改为 draft (把自动草稿，变为草稿。方便ID延续)

469 行
$post_id = wp_insert_post( array( 'post_title' => __( 'Auto Draft' ), 'post_type' => $post_type, 'post_status' => 'auto-draft' ) );



二、Wordpress上传文件中文乱码的解决方案（MD5转文件名）
找到/wp-admin/includes/file.php这个文件，

找到329行


// Move the file to the uploads dir
//$new_file = $uploads['path'] . "/$filename";




在以上代码之前添加如下内容

//MD5加密，兼容中文文件
$shawnee_name = substr(md5(substr($filename,0,-4).time()),0,12);
$shawnee_ext = substr($filename,-4);
$filename = $shawnee_name.$shawnee_ext;

将中文文件进行转换