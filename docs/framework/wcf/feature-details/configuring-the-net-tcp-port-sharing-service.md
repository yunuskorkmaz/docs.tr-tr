---
title: Net.TCP Bağlantı Noktası Hizmetini Yapılandırma
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: 3afc4cf50ac0dda0198ca8986177fd3028f9837e
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029365"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="3b705-102">Net.TCP Bağlantı Noktası Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3b705-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="3b705-103">Net.TCP taşıma kullanan şirket içinde barındırılan Hizmetler Denetim birkaç Gelişmiş ayarları gibi `ListenBacklog` ve `MaxPendingAccepts`, ağ iletişimi için kullanılan temel alınan TCP yuva davranışını yönetir.</span><span class="sxs-lookup"><span data-stu-id="3b705-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="3b705-104">Ancak, her yuva için bu ayarları yalnızca, varsayılan olarak etkin aktarım bağlama bağlantı noktası paylaşımı, devre dışı bırakmışsa bağlama düzeyinde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3b705-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="3b705-105">Net.tcp bağlama zaman sağlar bağlantı noktası Paylaşımı (ayarlayarak `portSharingEnabled =true` aktarım bağlama öğesi üzerindeki), örtük olarak bir dış işlem (Net.TCP bağlantı noktası paylaşma hizmeti barındıran yani SMSvcHost.exe,) sağlayan kendi adına TCP yuva yönetmek için.</span><span class="sxs-lookup"><span data-stu-id="3b705-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="3b705-106">Örneğin, TCP kullanılırken belirtin:</span><span class="sxs-lookup"><span data-stu-id="3b705-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="3b705-107">Bu şekilde yapılandırıldığında, hizmetin aktarım bağlama öğesi üzerinde belirtilen herhangi bir yuva ayarı SMSvcHost.exe tarafından belirtilen yuva ayarları yerine göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="3b705-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="3b705-108">SMSvcHost.exe yapılandırmak için erişimi adlı bir XML yapılandırma dosyası oluşturun ve SMSvcHost.exe yürütülebilir dosya (örneğin, C:\Windows\Microsoft.NET\Framework\v4.5) aynı fiziksel dizine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="3b705-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="3b705-109">Aşağıdaki örnek, bir ' % s'örnek erişimi, açıkça belirtilen tüm yapılandırılabilir değerler için varsayılan ayarlarla gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b705-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!--16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!--30 seconds -->  
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
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="3b705-110">Erişimi değiştirme zamanı</span><span class="sxs-lookup"><span data-stu-id="3b705-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="3b705-111">Genel olarak, bu dosyada belirtilen herhangi bir yapılandırma ayarı tüm hizmetler Net.TCP bağlantı noktası paylaşım hizmetini kullanan bir bilgisayara etkilediğinden bakım erişimi dosyasının içeriğini değiştirirken edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3b705-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="3b705-112">Bu uygulamaları içerir [!INCLUDE[wv](../../../../includes/wv-md.md)] TCP Etkinleştirmesi özellikleri Windows İşlem Etkinleştirme Hizmeti (WAS) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b705-112">This includes applications on [!INCLUDE[wv](../../../../includes/wv-md.md)] that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="3b705-113">Ancak, bazen Net.TCP bağlantı noktası Paylaşımı hizmeti varsayılan yapılandırmasını değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3b705-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="3b705-114">Örneğin, varsayılan değeri `maxPendingAccepts` 4 \* İşlemci sayısı.</span><span class="sxs-lookup"><span data-stu-id="3b705-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="3b705-115">Çok sayıda bağlantı noktası Paylaşımı kullanan hizmetleri barındıran sunucular, en yüksek performans sağlamak için bu değeri artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b705-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="3b705-116">İçin varsayılan değer `maxPendingConnections` 100'dür.</span><span class="sxs-lookup"><span data-stu-id="3b705-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="3b705-117">Bu değer bir hizmete çağrı yapma birden çok eşzamanlı istemciler varsa ve hizmeti istemci bağlantıları bırakıyor artırıldığında düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="3b705-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="3b705-118">Erişimi de bağlantı noktası paylaşma hizmeti yapabilir kimlikleri kullanmak işlemi hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="3b705-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="3b705-119">Bir işlem paylaşımı paylaşılan bir TCP kullanmak için hizmet bağlantı noktasına bağlandığında bağlantı noktası, bağlantı işlem kimliği işlem yapmak için izin verilen kimlikleri listesini karşı işaretli Paylaşım Hizmeti bağlantı noktasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b705-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="3b705-120">Bu kimlikleri güvenlik tanımlayıcılarını (SID'ler) belirtilen \<allowAccounts > erişimi dosyasının bölümü.</span><span class="sxs-lookup"><span data-stu-id="3b705-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="3b705-121">Varsayılan olarak, hizmet bağlantı noktası kullanma izni Administrators grubu üyelerinin yanı sıra sistem hesapları (LocalService, LocalSystem ve NetworkService) verilir.</span><span class="sxs-lookup"><span data-stu-id="3b705-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="3b705-122">Açıkça uygun SID Paylaşım Hizmeti bağlantı noktasına bağlanmak için başka bir kimlik (örneğin, bir kullanıcı kimliği) olarak çalışan bir işlemin tanıyan uygulamaları (SMSvc.exe işlem olana kadar bu değişiklikler uygulanmaz erişimi eklemeniz gerekir yeniden).</span><span class="sxs-lookup"><span data-stu-id="3b705-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b705-123">Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] sistemleri ile kullanıcı hesabı denetimi (etkinleştirilmişse, yerel kullanıcıların UAC) yükseltilmiş izinler bile hesabını Administrators grubunun bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="3b705-123">On [!INCLUDE[wv](../../../../includes/wv-md.md)] systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="3b705-124">Bu kullanıcıların yapmasına izin vermek için bağlantı noktası paylaşma hizmeti olmadan yükseltme, kullanıcının SID (veya kullanıcının üyesi olduğu bir grubun SID) kullanımını açıkça eklenmelidir \<allowAccounts > bölümüne erişimi.</span><span class="sxs-lookup"><span data-stu-id="3b705-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3b705-125">Özel bir varsayılan erişimi dosyasını belirtir `etwProviderId` SMSvcHost.exe İzleme hizmeti izlemeleri engellemesini önlemek için.</span><span class="sxs-lookup"><span data-stu-id="3b705-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b705-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b705-126">See Also</span></span>  
 [<span data-ttu-id="3b705-127">\<NET.TCP ></span><span class="sxs-lookup"><span data-stu-id="3b705-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
