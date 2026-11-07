
add_library(bte STATIC
	bte.c
	hci.c
	l2cap.c
	btmemb.c
	btmemr.c
	btpbuf.c
	physbusif.c
)

target_link_libraries(bte PRIVATE wiiuse_bte_lwbt_inc)

wiiuse_bte_lwbt_install_lib(bte)
