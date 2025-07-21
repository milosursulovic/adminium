<template>
  <div class="min-h-screen bg-gradient-to-br from-indigo-100 via-white to-blue-100">
    <div class="max-w-7xl mx-auto py-10 px-4">
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        <div
          v-for="app in apps"
          :key="app.name"
          @click="goTo(app.link)"
          class="bg-white rounded-2xl shadow-lg p-6 cursor-pointer hover:shadow-xl transition relative"
        >
          <span
            :class="[
              'absolute top-3 right-3 text-xs font-medium px-2 py-1 rounded-full',
              app.status === 'Aktivna'
                ? 'bg-green-100 text-green-700'
                : app.status === 'Beta'
                ? 'bg-yellow-100 text-yellow-700'
                : 'bg-gray-200 text-gray-600',
            ]"
          >
            {{ app.status }}
          </span>

          <div class="flex items-center gap-4 mb-4">
            <img :src="app.iconPath" alt="ikonica" class="w-10 h-10 object-contain" />
            <div>
              <h2 class="text-xl font-semibold text-slate-700">{{ app.name }}</h2>
              <p class="text-sm text-slate-500">{{ app.desc }}</p>
            </div>
          </div>

          <div class="text-right">
            <span class="text-blue-600 hover:underline text-sm">Otvori aplikaciju →</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script setup>
const baseUrl = `https://${import.meta.env.VITE_HOST_IP_ADDRESS}`

const apps = [
  {
    name: 'NetDesk',
    iconPath: new URL('@/assets/icons/netdesk.png', import.meta.url).href,
    desc: 'Upravljanje IP adresama i RDP konekcijama.',
    link: `${baseUrl}:${import.meta.env.VITE_NETDESK_PORT}`,
    status: 'Aktivna',
  },
  {
    name: 'NetPulse',
    iconPath: new URL('@/assets/icons/netpulse.png', import.meta.url).href,
    desc: 'Status računara i pingovanje mreže.',
    link: `${baseUrl}:${import.meta.env.VITE_NETPULSE_PORT}`,
    status: 'U razvoju',
  },
  {
    name: 'AssetMap',
    iconPath: new URL('@/assets/icons/assetmap.png', import.meta.url).href,
    desc: 'Inventar hardverskih i softverskih komponenti.',
    link: `${baseUrl}:${import.meta.env.VITE_ASSETMAP_PORT}`,
    status: 'U razvoju',
  },
  {
    name: 'ChangeTrack',
    iconPath: new URL('@/assets/icons/changetrack.png', import.meta.url).href,
    desc: 'Zapis svih mrežnih promena.',
    link: `${baseUrl}:${import.meta.env.VITE_CHANGETRACK_PORT}`,
    status: 'U razvoju',
  },
  {
    name: 'ScriptCast',
    iconPath: new URL('@/assets/icons/scriptcast.png', import.meta.url).href,
    desc: 'Slanje i izvršavanje skripti na udaljenim računarima.',
    link: `${baseUrl}:${import.meta.env.VITE_SCRIPTCAST_PORT}`,
    status: 'U razvoju',
  },
  {
    name: 'SecuScan',
    iconPath: new URL('@/assets/icons/secuscan.png', import.meta.url).href,
    desc: 'Stanje antivirus zaštite i ažuriranja.',
    link: `${baseUrl}:${import.meta.env.VITE_SECUSCAN_PORT}`,
    status: 'U razvoju',
  },
  {
    name: 'SafeKey',
    iconPath: new URL('@/assets/icons/safekey.png', import.meta.url).href,
    desc: 'Baza sistemskih lozinki sa pristupom po nivou.',
    link: `${baseUrl}:${import.meta.env.VITE_SAFEKEY_PORT}`,
    status: 'U razvoju',
  },
  {
    name: 'Maintainer',
    iconPath: new URL('@/assets/icons/maintainer.png', import.meta.url).href,
    desc: 'Raspored održavanja i zadaci u kalendaru.',
    link: `${baseUrl}:${import.meta.env.VITE_MAINTAINER_PORT}`,
    status: 'U razvoju',
  },
  {
    name: 'FileDrive',
    iconPath: new URL('@/assets/icons/filedrive.png', import.meta.url).href,
    desc: 'Lokalna platforma za deljenje fajlova i upravljanje pristupom.',
    link: `${baseUrl}:${import.meta.env.VITE_FILEDRIVE_PORT}`,
    status: 'Aktivna',
  },
  {
    name: 'HelpDesk',
    iconPath: new URL('@/assets/icons/helpdesk.png', import.meta.url).href,
    desc: 'Sistem za prijavu i praćenje tehničkih problema.',
    link: `${baseUrl}:${import.meta.env.VITE_HELPDESK_PORT}`,
    status: 'Aktivna',
  },
  {
    name: 'DNS Logovi',
    iconPath: new URL('@/assets/icons/dnslogger.png', import.meta.url).href,
    desc: 'Sistem za praćenje DNS logova.',
    link: `${baseUrl}:${import.meta.env.VITE_DNS_LOGGER_PORT}`,
    status: 'Aktivna',
  },
  {
    name: 'SQLite Čitač',
    iconPath: new URL('@/assets/icons/sqliteviewer.png', import.meta.url).href,
    desc: 'Alat za čitanje SQLite baza.',
    link: `${baseUrl}:${import.meta.env.VITE_SQLITE_VIEWER_PORT}`,
    status: 'Aktivna',
  },
]

function goTo(link) {
  window.open(link, '_blank')
}
</script>
