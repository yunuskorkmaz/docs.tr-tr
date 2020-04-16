---
title: Net.TCP Bağlantı Noktası Hizmetini Yapılandırma
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: fea2e734099c4c623dcde2a37f4c164cf9ce61ac
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464190"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="1d394-102">Net.TCP Bağlantı Noktası Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1d394-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="1d394-103">Net.TCP aktarımını kullanan kendi kendine barındırılan hizmetler, ağ iletişimi için kullanılan temel TCP soketi davranışını yöneten `ListenBacklog` birkaç `MaxPendingAccepts`gelişmiş ayarı denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1d394-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="1d394-104">Ancak, her soket için bu ayarlar yalnızca aktarım bağlama varsayılan olarak etkinleştirilen bağlantı noktası paylaşımını devre dışı bıraktıysa bağlama düzeyinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1d394-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="1d394-105">Net.tcp bağlama bağlantı noktası paylaşımını `portSharingEnabled =true` etkinleştirdiğinde (taşıma bağlama öğesini ayarlayarak), dolaylı olarak harici bir işleme (Net.TCP Bağlantı Noktası Paylaşım Hizmeti'ni barındıran SMSvcHost.exe) adına TCP soketi yönetmeolanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d394-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="1d394-106">Örneğin, TCP kullanırken şunları belirtin:</span><span class="sxs-lookup"><span data-stu-id="1d394-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="1d394-107">Bu şekilde yapılandırıldığında, hizmetin taşıma bağlama öğesinde belirtilen soket ayarları SMSvcHost.exe tarafından belirtilen soket ayarları lehine yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="1d394-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="1d394-108">SMSvcHost.exe'yi yapılandırmak için, SmSvcHost.exe.config adında bir XML yapılandırma dosyası oluşturun ve yürütülebilir (örneğin, C:\Windows\Microsoft.NET\Framework\v4.5) ile aynı fiziksel dizine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="1d394-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="1d394-109">Aşağıdaki örnek, açıkça belirtilen tüm yapılandırılabilir değerler için varsayılan ayarları içeren bir örnek SMSvcHost.exe.config'i göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1d394-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="1d394-110">Ne zaman SMSvcHost.exe.config değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="1d394-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="1d394-111">Bu dosyada belirtilen yapılandırma ayarları Net.TCP Bağlantı Noktası Paylaşım Hizmeti kullanan bir bilgisayardaki tüm hizmetleri etkilediğinden, genel olarak, SMSvcHost.exe.config dosyasının içeriğini değiştirirken dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d394-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="1d394-112">Buna, Windows İşlem Etkinleştirme Hizmeti'nin (WAS) TCP Etkinleştirme özelliklerini kullanan Windows Vista'daki uygulamalar dahildir.</span><span class="sxs-lookup"><span data-stu-id="1d394-112">This includes applications on Windows Vista that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="1d394-113">Ancak, bazen Net.TCP Bağlantı Noktası Paylaşım Hizmeti için varsayılan yapılandırmayı değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1d394-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="1d394-114">Örneğin, varsayılan değer `maxPendingAccepts` 4 \* işlemci sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="1d394-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="1d394-115">Bağlantı noktası paylaşımını kullanan çok sayıda hizmet barındıran sunucular, maksimum iş elde etmek için bu değeri artırabilir.</span><span class="sxs-lookup"><span data-stu-id="1d394-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="1d394-116">Varsayılan değer `maxPendingConnections` 100'dür.</span><span class="sxs-lookup"><span data-stu-id="1d394-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="1d394-117">Hizmeti çağıran birden çok eşzamanlı istemci varsa ve hizmet istemci bağlantılarını bırakıyorsa, bu değeri artırmayı da düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="1d394-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="1d394-118">SMSvcHost.exe.config ayrıca bağlantı noktası paylaşım hizmetinden yararlanabilecek işlem kimlikleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1d394-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="1d394-119">Bir işlem paylaşılan bir TCP bağlantı noktasından yararlanmak için bağlantı noktası paylaşım hizmetine bağlandığında, bağlantı işleminin işlem kimliği bağlantı noktası paylaşım hizmetinden yararlanmasına izin verilen kimlikler listesiyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="1d394-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="1d394-120">Bu kimlikler, SMSvcHost.exe.config dosyasının \<izin veren Hesaplar> bölümünde güvenlik tanımlayıcıları (SID'ler) olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="1d394-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="1d394-121">Varsayılan olarak, bağlantı noktası paylaşım hizmetini kullanma izni sistem hesaplarına (LocalService, LocalSystem ve NetworkService) ve Yöneticiler grubunun üyelerine verilir.</span><span class="sxs-lookup"><span data-stu-id="1d394-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="1d394-122">Başka bir kimlik olarak çalışan bir işlemin (örneğin, kullanıcı kimliği) bağlantı noktası paylaşım hizmetine bağlanmasına izin veren uygulamaların, SMSvcHost.exe.config'e uygun SID'yi açıkça eklemesi gerekir (bu değişiklikler SMSvc.exe işlemi yeniden başlatılıncaya kadar uygulanmaz).</span><span class="sxs-lookup"><span data-stu-id="1d394-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d394-123">Kullanıcı Hesabı Denetimi (UAC) etkinleştirilmiş Windows Vista sistemlerinde, yerel kullanıcılar hesapları Yöneticiler grubunun bir üyesi olsa bile yüksek izinlere ihtiyaç duyar.</span><span class="sxs-lookup"><span data-stu-id="1d394-123">On Windows Vista systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="1d394-124">Bu kullanıcıların yükseklik olmadan bağlantı noktası paylaşım hizmetinden yararlanabilmeleri için, kullanıcının SID'sinin (veya kullanıcının üye olduğu bir \<grubun SID'sinin) SMSvcHost.exe.config'in izin verilen Hesaplar> bölümüne açıkça eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d394-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1d394-125">Varsayılan SMSvcHost.exe.config dosyası, SMSvcHost.exe izlemenin hizmet izlemelerini engellemesini önlemek için bir özel `etwProviderId` belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d394-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d394-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d394-126">See also</span></span>

- [<span data-ttu-id="1d394-127">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="1d394-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
