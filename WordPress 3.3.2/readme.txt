关闭自动修订功能和自动保存功能
根目录下找到wp-config.php
在define('WP_DEBUG', false);后面填加
define('WP_POST_REVISIONS', false); //关闭自动修订功能
define('AUTOSAVE_INTERVAL', 86400); //设置自动保存时间为一天，达到变相关闭自动保存的目的。


/wp-admin/index.php  - 去除 打开 此页面新增一条 草稿的的代码干扰属于BUG



/wp-admin/includes/post.php 屏蔽自动删除 auto-draft

"if ( $create_in_db ) {
  // Cleanup old auto-drafts more than 7 days old
  //$old_posts = $wpdb->get_col( ""SELECT ID FROM $wpdb->posts WHERE post_status = 'auto-draft' AND DATE_SUB( NOW(), INTERVAL 7 DAY ) > post_date"" );
  //foreach ( (array) $old_posts as $delete )
  // wp_delete_post( $delete, true ); // Force delete"




/wp-admin/includes/post.php    auto-draft 改为 draft (把自动草稿，变为草稿。方便ID延续)

  $post_id = wp_insert_post( array( 'post_title' => __( 'Auto Draft' ), 'post_type' => $post_type, 'post_status' => 'auto-draft' ) );
