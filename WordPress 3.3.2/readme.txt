�ر��Զ��޶����ܺ��Զ����湦��
��Ŀ¼���ҵ�wp-config.php
��define('WP_DEBUG', false);�������
define('WP_POST_REVISIONS', false); //�ر��Զ��޶�����
define('AUTOSAVE_INTERVAL', 86400); //�����Զ�����ʱ��Ϊһ�죬�ﵽ����ر��Զ������Ŀ�ġ�


/wp-admin/index.php  - ȥ�� �� ��ҳ������һ�� �ݸ�ĵĴ����������BUG



/wp-admin/includes/post.php �����Զ�ɾ�� auto-draft

"if ( $create_in_db ) {
  // Cleanup old auto-drafts more than 7 days old
  //$old_posts = $wpdb->get_col( ""SELECT ID FROM $wpdb->posts WHERE post_status = 'auto-draft' AND DATE_SUB( NOW(), INTERVAL 7 DAY ) > post_date"" );
  //foreach ( (array) $old_posts as $delete )
  // wp_delete_post( $delete, true ); // Force delete"




/wp-admin/includes/post.php    auto-draft ��Ϊ draft (���Զ��ݸ壬��Ϊ�ݸ塣����ID����)

  $post_id = wp_insert_post( array( 'post_title' => __( 'Auto Draft' ), 'post_type' => $post_type, 'post_status' => 'auto-draft' ) );
