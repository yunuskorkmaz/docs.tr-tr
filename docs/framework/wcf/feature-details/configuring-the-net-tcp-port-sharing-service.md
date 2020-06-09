---
title: Net.TCP Bağlantı Noktası Hizmetini Yapılandırma
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: acfb720ba74cda62b2949263fcb31d356671b4f3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597520"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="b796f-102">Net.TCP Bağlantı Noktası Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b796f-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="b796f-103">Net. TCP aktarımını kullanan şirket içinde barındırılan hizmetler, ve gibi çeşitli gelişmiş ayarları denetleyebilir ve bu da `ListenBacklog` `MaxPendingAccepts` ağ iletişimi için kullanılan temeldeki TCP yuvasının davranışını yönetir.</span><span class="sxs-lookup"><span data-stu-id="b796f-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="b796f-104">Ancak, her bir yuva için bu ayarlar varsayılan olarak etkinleştirilen bağlantı noktası paylaşımını devre dışı bırakılmışsa yalnızca bağlama düzeyinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b796f-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="b796f-105">Bir net. TCP bağlaması bağlantı noktası paylaşımını ( `portSharingEnabled =true` taşıma bağlama öğesi üzerinde ayarı yaparak) etkinleştirirse, bir dış işleme (yani net. TCP bağlantı noktası paylaşım hizmetini barındıran SMSvcHost. exe) kendi ADıNA TCP yuvasını yönetmek için örtülü olarak izin verir.</span><span class="sxs-lookup"><span data-stu-id="b796f-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="b796f-106">Örneğin, TCP kullanırken şunları belirtin:</span><span class="sxs-lookup"><span data-stu-id="b796f-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="b796f-107">Bu şekilde yapılandırıldığında, hizmetin aktarım bağlama öğesinde belirtilen tüm yuva ayarları SMSvcHost. exe tarafından belirtilen yuva ayarları dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="b796f-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="b796f-108">SMSvcHost. exe ' yi yapılandırmak için SmSvcHost. exe. config adlı bir XML yapılandırma dosyası oluşturun ve SMSvcHost. exe yürütülebilir dosyası ile aynı fiziksel dizine yerleştirin (örneğin, C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="b796f-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="b796f-109">Aşağıdaki örnek, açıkça belirtilen tüm yapılandırılabilir değerler için varsayılan ayarlarla bir SMSvcHost. exe. config dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="b796f-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!-- 16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!-- 30 seconds -->  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->  
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->  
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
    </system.serviceModel.activation>
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="b796f-110">SMSvcHost. exe. config ne zaman değiştirilir</span><span class="sxs-lookup"><span data-stu-id="b796f-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="b796f-111">Genel olarak, SMSvcHost. exe. config dosyasının içeriğini değiştirirken dikkatli olunmalıdır çünkü bu dosyada belirtilen herhangi bir yapılandırma ayarı net. TCP bağlantı noktası paylaşım hizmetini kullanan bir bilgisayardaki tüm hizmetleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="b796f-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="b796f-112">Bu, Windows Vista 'da Windows Işlem etkinleştirme hizmeti 'nin (WAS) TCP etkinleştirme özelliklerini kullanan uygulamalar içerir.</span><span class="sxs-lookup"><span data-stu-id="b796f-112">This includes applications on Windows Vista that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="b796f-113">Ancak, bazen net. TCP bağlantı noktası paylaşma hizmeti için varsayılan yapılandırmayı değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b796f-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="b796f-114">Örneğin, için varsayılan değer `maxPendingAccepts` 4 \* işlemci sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="b796f-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="b796f-115">Bağlantı noktası Paylaşımı kullanan çok sayıda hizmeti barındıran sunucular, en yüksek aktarım hızını elde etmek için bu değeri artırabilir.</span><span class="sxs-lookup"><span data-stu-id="b796f-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="b796f-116">İçin varsayılan değer `maxPendingConnections` 100 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b796f-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="b796f-117">Hizmeti çağıran birden çok eş zamanlı istemci varsa ve hizmet istemci bağlantılarını bırakırken, bu değeri artırmayı göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b796f-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="b796f-118">SMSvcHost. exe. config, bağlantı noktası paylaşım hizmetini kullanan işlem kimlikleri hakkındaki bilgileri de içerir.</span><span class="sxs-lookup"><span data-stu-id="b796f-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="b796f-119">Bir işlem, paylaşılan bir TCP bağlantı noktasını kullanmak için bağlantı noktası paylaşım hizmetine bağlandığında, bağlanan işlemin işlem kimliği, bağlantı noktası paylaşım hizmetini kullanmasına izin verilen kimliklerin bir listesine göre denetlenir.</span><span class="sxs-lookup"><span data-stu-id="b796f-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="b796f-120">Bu kimlikler \<allowAccounts> SMSvcHost. exe. config dosyasının bölümünde güvenlik tanımlayıcıları (SID) olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b796f-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="b796f-121">Varsayılan olarak, bağlantı noktası paylaşım hizmetini kullanma izni, sistem hesaplarına (LocalService, LocalSystem ve NetworkService) ve Yöneticiler grubunun üyelerine verilir.</span><span class="sxs-lookup"><span data-stu-id="b796f-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="b796f-122">Bağlantı noktası paylaşım hizmetine bağlanmak için başka bir kimlik (örneğin, bir kullanıcı kimliği) olarak çalışan bir işlemin, SMSvcHost. exe. config 'e uygun SID 'yi açıkça eklemesi gerekir (Bu değişiklikler SMSvc. exe işlemi yeniden başlatılana kadar uygulanmaz).</span><span class="sxs-lookup"><span data-stu-id="b796f-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b796f-123">Kullanıcı hesabı denetimi (UAC) özellikli Windows Vista sistemlerinde, hesapları Yöneticiler grubunun bir üyesi olsa da, yerel kullanıcılar yükseltilmiş izinler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b796f-123">On Windows Vista systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="b796f-124">Bu kullanıcıların bağlantı noktası paylaşım hizmetini yükseltme olmadan kullanmasına izin vermek için, kullanıcının SID 'SI (veya kullanıcının üye olduğu bir grubun SID 'SI) \<allowAccounts> SMSvcHost. exe. config ' in bölümüne açıkça eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="b796f-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b796f-125">Varsayılan SMSvcHost. exe. config dosyası, `etwProviderId` SMSvcHost. exe izlemenin hizmet izlemelerinde kesintiye uğramasını engellemek için bir özel belirtir.</span><span class="sxs-lookup"><span data-stu-id="b796f-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b796f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b796f-126">See also</span></span>

- [\<net.tcp>](../../configure-apps/file-schema/wcf/net-tcp.md)
