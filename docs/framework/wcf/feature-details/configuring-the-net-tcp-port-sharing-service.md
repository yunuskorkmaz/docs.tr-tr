---
title: Net.TCP Bağlantı Noktası Hizmetini Yapılandırma
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: c5dc80391ec5f655fadd31c59eef76015b9965d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949612"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>Net.TCP Bağlantı Noktası Hizmetini Yapılandırma
Net. TCP aktarımını kullanan şirket içinde barındırılan hizmetler, `ListenBacklog` ve gibi çeşitli gelişmiş ayarları denetleyebilir ve `MaxPendingAccepts`bu da ağ iletişimi için kullanılan temeldeki TCP yuvasının davranışını yönetir. Ancak, her bir yuva için bu ayarlar varsayılan olarak etkinleştirilen bağlantı noktası paylaşımını devre dışı bırakılmışsa yalnızca bağlama düzeyinde geçerlidir.  
  
 Bir net. TCP bağlaması bağlantı noktası paylaşımını (taşıma bağlama öğesi `portSharingEnabled =true` üzerinde ayarı yaparak) etkinleştirirse, bir dış işleme (yani net. TCP bağlantı noktası paylaşım hizmetini barındıran SMSvcHost. exe) kendi adına TCP yuvasını yönetmek için örtülü olarak izin verir. Örneğin, TCP kullanırken şunları belirtin:  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 Bu şekilde yapılandırıldığında, hizmetin aktarım bağlama öğesinde belirtilen tüm yuva ayarları SMSvcHost. exe tarafından belirtilen yuva ayarları dikkate alınmaz.  
  
 SMSvcHost. exe ' yi yapılandırmak için SmSvcHost. exe. config adlı bir XML yapılandırma dosyası oluşturun ve SMSvcHost. exe yürütülebilir dosyası ile aynı fiziksel dizine yerleştirin (örneğin, C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 Aşağıdaki örnek, açıkça belirtilen tüm yapılandırılabilir değerler için varsayılan ayarlarla bir SMSvcHost. exe. config dosyası gösterir.  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>SMSvcHost. exe. config ne zaman değiştirilir  
 Genel olarak, SMSvcHost. exe. config dosyasının içeriğini değiştirirken dikkatli olunmalıdır çünkü bu dosyada belirtilen herhangi bir yapılandırma ayarı net. TCP bağlantı noktası paylaşım hizmetini kullanan bir bilgisayardaki tüm hizmetleri etkiler. Bu, Windows işlem [!INCLUDE[wv](../../../../includes/wv-md.md)] etkinleştirme hizmeti 'nin (was) TCP etkinleştirme özelliklerini kullanan uygulamalar içerir.  
  
 Ancak, bazen net. TCP bağlantı noktası paylaşma hizmeti için varsayılan yapılandırmayı değiştirmeniz gerekebilir. Örneğin, için `maxPendingAccepts` varsayılan değer 4 * işlemci sayısıdır. Bağlantı noktası Paylaşımı kullanan çok sayıda hizmeti barındıran sunucular, en yüksek aktarım hızını elde etmek için bu değeri artırabilir. İçin `maxPendingConnections` varsayılan değer 100 ' dir. Hizmeti çağıran birden çok eş zamanlı istemci varsa ve hizmet istemci bağlantılarını bırakırken, bu değeri artırmayı göz önünde bulundurmanız gerekir.  
  
 SMSvcHost. exe. config, bağlantı noktası paylaşım hizmetini kullanan işlem kimlikleri hakkındaki bilgileri de içerir. Bir işlem, paylaşılan bir TCP bağlantı noktasını kullanmak için bağlantı noktası paylaşım hizmetine bağlandığında, bağlanan işlemin işlem kimliği, bağlantı noktası paylaşım hizmetini kullanmasına izin verilen kimliklerin bir listesine göre denetlenir. Bu kimlikler SMSvcHost. exe. config dosyasının \<AllowAccounts > bölümünde güvenlik tanımlayıcıları (SID) olarak belirtilir. Varsayılan olarak, bağlantı noktası paylaşım hizmetini kullanma izni, sistem hesaplarına (LocalService, LocalSystem ve NetworkService) ve Yöneticiler grubunun üyelerine verilir. Bağlantı noktası paylaşım hizmetine bağlanmak için başka bir kimlik (örneğin, bir kullanıcı kimliği) olarak çalışan bir işlemin, SMSvcHost. exe. config 'e uygun SID 'yi açıkça eklemesi gerekir (Bu değişiklikler SMSvc. exe işlemi tamamlanana kadar uygulanmaz) yeniden başlatıldı).  
  
> [!NOTE]
> Kullanıcı hesabı denetimi (UAC) etkin olan sistemlerde,hesaplarıYöneticilergrubununbirüyesiolsada,yerelkullanıcılaryükseltilmişizinlergerektirir.[!INCLUDE[wv](../../../../includes/wv-md.md)] Bu kullanıcıların bağlantı noktası paylaşım hizmetini yükseltme olmadan kullanmasına izin vermek için, kullanıcının SID 'si (veya kullanıcının üye olduğu bir grubun SID 'si) SMSvcHost. exe. config dosyasının \<AllowAccounts > bölümüne açıkça eklenmelidir.  
  
> [!WARNING]
>  Varsayılan SMSvcHost. exe. config dosyası, SMSvcHost. `etwProviderId` exe izlemenin hizmet izlemelerinde kesintiye uğramasını engellemek için bir özel belirtir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<net. TCP >](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
