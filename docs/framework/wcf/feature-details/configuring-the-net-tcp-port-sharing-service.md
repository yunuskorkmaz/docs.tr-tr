---
description: 'Daha fazla bilgi edinin: net. TCP bağlantı noktası paylaşım hizmetini yapılandırma'
title: Net.TCP Bağlantı Noktası Hizmetini Yapılandırma
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: 9e6a09c1dd986bc96a9d518d25226dd211b3e6ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780706"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>Net.TCP Bağlantı Noktası Hizmetini Yapılandırma

Net. TCP aktarımını kullanan şirket içinde barındırılan hizmetler, ve gibi çeşitli gelişmiş ayarları denetleyebilir ve bu da `ListenBacklog` `MaxPendingAccepts` ağ iletişimi için kullanılan temeldeki TCP yuvasının davranışını yönetir. Ancak, her bir yuva için bu ayarlar varsayılan olarak etkinleştirilen bağlantı noktası paylaşımını devre dışı bırakılmışsa yalnızca bağlama düzeyinde geçerlidir.  
  
 Bir net. TCP bağlaması, bağlantı noktası paylaşımını ( `portSharingEnabled =true` taşıma bağlama öğesinde ayarı yaparak) etkinleştirirse, bir dış işleme (yani net. TCP bağlantı noktası paylaşım hizmetini barındıran SMSvcHost.exe), TCP yuvasını adına yönetmek için örtülü olarak izin verir. Örneğin, TCP kullanırken şunları belirtin:  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 Bu şekilde yapılandırıldığında, hizmetin aktarım bağlama öğesinde belirtilen tüm yuva ayarları, SMSvcHost.exe tarafından belirtilen yuva ayarları göz ardı edilerek dikkate alınmaz.  
  
 SMSvcHost.exe yapılandırmak için SmSvcHost.exe.config adlı bir XML yapılandırma dosyası oluşturun ve SMSvcHost.exe yürütülebiliri ile aynı fiziksel dizine yerleştirin (örneğin, C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 Aşağıdaki örnekte, açıkça belirtilen tüm yapılandırılabilir değerler için varsayılan ayarlarla birlikte bir örnek SMSvcHost.exe.config gösterilmektedir.  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>SMSvcHost.exe.config ne zaman değiştirilir  

 Genel olarak, SMSvcHost.exe.config dosyanın içeriğini değiştirirken dikkatli olunmalıdır çünkü bu dosyada belirtilen herhangi bir yapılandırma ayarı net. TCP bağlantı noktası paylaşma hizmetini kullanan bir bilgisayardaki tüm hizmetleri etkiler. Bu, Windows Vista 'da Windows Işlem etkinleştirme hizmeti 'nin (WAS) TCP etkinleştirme özelliklerini kullanan uygulamalar içerir.  
  
 Ancak, bazen net. TCP bağlantı noktası paylaşma hizmeti için varsayılan yapılandırmayı değiştirmeniz gerekebilir. Örneğin, için varsayılan değer `maxPendingAccepts` 4 * işlemci sayısıdır. Bağlantı noktası Paylaşımı kullanan çok sayıda hizmeti barındıran sunucular, en yüksek aktarım hızını elde etmek için bu değeri artırabilir. İçin varsayılan değer `maxPendingConnections` 100 ' dir. Hizmeti çağıran birden çok eş zamanlı istemci varsa ve hizmet istemci bağlantılarını bırakırken, bu değeri artırmayı göz önünde bulundurmanız gerekir.  
  
 SMSvcHost.exe.config, bağlantı noktası paylaşım hizmetini kullanan işlem kimlikleri hakkında bilgiler de içerir. Bir işlem, paylaşılan bir TCP bağlantı noktasını kullanmak için bağlantı noktası paylaşım hizmetine bağlandığında, bağlanan işlemin işlem kimliği, bağlantı noktası paylaşım hizmetini kullanmasına izin verilen kimliklerin bir listesine göre denetlenir. Bu kimlikler SMSvcHost.exe.config dosyasının bölümünde güvenlik tanımlayıcıları (SID) olarak belirtilir \<allowAccounts> . Varsayılan olarak, bağlantı noktası paylaşım hizmetini kullanma izni, sistem hesaplarına (LocalService, LocalSystem ve NetworkService) ve Yöneticiler grubunun üyelerine verilir. Bağlantı noktası paylaşma hizmetine bağlanmak için başka bir kimlik (örneğin, bir kullanıcı kimliği) olarak çalışan bir işlemin, SMSvcHost.exe.config uygun SID 'yi açıkça eklemesi gerekir (Bu değişiklikler, SMSvc.exe işlemi yeniden başlatılana kadar uygulanmaz).  
  
> [!NOTE]
> Kullanıcı hesabı denetimi (UAC) özellikli Windows Vista sistemlerinde, hesapları Yöneticiler grubunun bir üyesi olsa da, yerel kullanıcılar yükseltilmiş izinler gerektirir. Bu kullanıcıların bağlantı noktası paylaşım hizmetini yükseltme olmadan kullanmasına izin vermek için, kullanıcının SID 'SI (veya kullanıcının üye olduğu bir grubun SID 'SI) \<allowAccounts> SMSvcHost.exe.config bölümüne açıkça eklenmelidir.  
  
> [!WARNING]
> Varsayılan SMSvcHost.exe.config dosyası, `etwProviderId` SMSvcHost.exe izlemenin hizmet izlemelerinde kesintiye uğramasını engellemek için bir özel belirtir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<net.tcp>](../../configure-apps/file-schema/wcf/net-tcp.md)
