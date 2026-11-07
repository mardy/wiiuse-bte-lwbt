
add_library(wiiuse STATIC
	classic.c
	dynamics.c
	events.c
	guitar_hero_3.c
	io.c
	io_wii.c
	ir.c
	nunchuk.c
	wiiboard.c
	wiiuse.c
	speaker.c
	wpad.c
	motion_plus.c
)

target_link_libraries(wiiuse PRIVATE wiiuse_bte_lwbt_inc)

wiiuse_bte_lwbt_install_lib(wiiuse)
