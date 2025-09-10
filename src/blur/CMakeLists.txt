add_subdirectory(kcm)

set(lightlyshaders_blur_SOURCES
    blur.cpp
    blur.qrc
    main.cpp
)

kconfig_add_kcfg_files(lightlyshaders_blur_SOURCES
    blurconfig.kcfgc
)

add_library(lightlyshaders_blur MODULE ${lightlyshaders_blur_SOURCES})
target_link_libraries(lightlyshaders_blur PRIVATE
 
    KWinX11::kwin

    KF6::ConfigGui
    PRIVATE XCB::XCB
    KDecoration3::KDecoration

    lshelper
)

install(TARGETS lightlyshaders_blur DESTINATION ${KDE_INSTALL_PLUGINDIR}/kwin-x11/effects/plugins)
