all: eapol-key-auth
include ../rules.include

CFLAGS += -DCONFIG_IEEE80211R_AP
CFLAGS += -DCONFIG_IEEE80211R
CFLAGS += -DCONFIG_TDLS

LIBS += $(SRC)/common/libcommon.a
LIBS += $(SRC)/crypto/libcrypto.a
LIBS += $(SRC)/tls/libtls.a
LIBS += $(SRC)/eap_common/libeap_common.a
LIBS += $(SRC)/l2_packet/libl2_packet.a
LIBS += $(SRC)/utils/libutils.a
LIBS += $(SRC)/wps/libwps.a
LIBS += $(SRC)/eapol_auth/libeapol_auth.a
LIBS += $(SRC)/eap_server/libeap_server.a
LIBS += $(SRC)/ap/libap.a
LIBS += $(SRC)/radius/libradius.a

eapol-key-auth: eapol-key-auth.o $(OBJS) $(LIBS)
	$(LDO) $(LDFLAGS) -o $@ $^ -Wl,--start-group $(LIBS) -Wl,--end-group

clean:
	$(MAKE) -C $(SRC) clean
	rm -f eapol-key-auth *~ *.o *.d ../*~ ../*.o ../*.d

-include $(OBJS:%.o=%.d)
