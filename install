export DEBIAN_FRONTEND noninteractive
export GIT_SSL_NO_VERIFY true
useradd -m freeswitch
mkdir -p /opt/freeswitch
chown -R freeswitch.freeswitch /opt/freeswitch

apt-get -y -qq update
apt-get install -y --no-install-recommends autoconf automake build-essential gawk git-core libasound2-dev libdb-dev libexpat1-dev libcurl4-openssl-dev libgdbm-dev libgnutls-dev libjpeg-dev libncurses5 libncurses5-dev libperl-dev libogg-dev libssl-dev libtiff4-dev libtool libvorbis-dev libx11-dev libzrtpcpp-dev make python-dev snmp snmpd subversion unixodbc-dev uuid-dev zlib1g-dev libsqlite3-dev libpcre3-dev libspeex-dev libspeexdsp-dev libldns-dev libedit-dev libpq-dev libmemcached-dev curl lua5.1
git clone -b master https://stash.freeswitch.org/scm/fs/freeswitch.git /usr/local/src/freeswitch
ln -s /usr/include/postgresql/libpq-fe.h  /usr/local/src/freeswitch/src/mod/event_handlers/mod_cdr_pg_csv/ &&\
ln -s /usr/include/postgresql/postgres_ext.h  /usr/local/src/freeswitch/src/mod/event_handlers/mod_cdr_pg_csv/ &&\
ln -s /usr/include/postgresql/pg_config_ext.h  /usr/local/src/freeswitch/src/mod/event_handlers/mod_cdr_pg_csv/ &&\
cd /usr/local/src/freeswitch
echo "" > /usr/local/src/freeswitch/modules.conf &&\
  for module in applications/mod_commands applications/mod_conference applications/mod_curl applications/mod_db applications/mod_dptools applications/mod_enum applications/mod_esf applications/mod_esl applications/mod_expr applications/mod_fifo applications/mod_hash applications/mod_sms applications/mod_spandsp codecs/mod_amr codecs/mod_amrwb codecs/mod_g723_1 codecs/mod_g729 codecs/mod_ilbc codecs/mod_speex dialplans/mod_dialplan_xml endpoints/mod_loopback endpoints/mod_sofia event_handlers/mod_cdr_csv event_handlers/mod_cdr_pg_csv event_handlers/mod_event_socket formats/mod_local_stream formats/mod_native_file formats/mod_shout formats/mod_sndfile formats/mod_tone_stream languages/mod_lua loggers/mod_console loggers/mod_logfile loggers/mod_syslog xml_int/mod_xml_curl; do echo $module >> /usr/local/src/freeswitch/modules.conf ; done &&\
  ./bootstrap.sh -j &&\
  ./configure --prefix=/opt/freeswitch --enable-core-pgsql-support &&\
 make; make install && make all && apt-get clean
rm -fr /usr/local/src/freeswitch
