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
# <a name="configuring-the-nettcp-port-sharing-service"></a>Net.TCP Bağlantı Noktası Hizmetini Yapılandırma
Net.TCP aktarımını kullanan kendi kendine barındırılan hizmetler, ağ iletişimi için kullanılan temel TCP soketi davranışını yöneten `ListenBacklog` birkaç `MaxPendingAccepts`gelişmiş ayarı denetleyebilir. Ancak, her soket için bu ayarlar yalnızca aktarım bağlama varsayılan olarak etkinleştirilen bağlantı noktası paylaşımını devre dışı bıraktıysa bağlama düzeyinde geçerlidir.  
  
 Net.tcp bağlama bağlantı noktası paylaşımını `portSharingEnabled =true` etkinleştirdiğinde (taşıma bağlama öğesini ayarlayarak), dolaylı olarak harici bir işleme (Net.TCP Bağlantı Noktası Paylaşım Hizmeti'ni barındıran SMSvcHost.exe) adına TCP soketi yönetmeolanağı sağlar. Örneğin, TCP kullanırken şunları belirtin:  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 Bu şekilde yapılandırıldığında, hizmetin taşıma bağlama öğesinde belirtilen soket ayarları SMSvcHost.exe tarafından belirtilen soket ayarları lehine yoksayılır.  
  
 SMSvcHost.exe'yi yapılandırmak için, SmSvcHost.exe.config adında bir XML yapılandırma dosyası oluşturun ve yürütülebilir (örneğin, C:\Windows\Microsoft.NET\Framework\v4.5) ile aynı fiziksel dizine yerleştirin.  
  
 Aşağıdaki örnek, açıkça belirtilen tüm yapılandırılabilir değerler için varsayılan ayarları içeren bir örnek SMSvcHost.exe.config'i göstermektedir.  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Ne zaman SMSvcHost.exe.config değiştirmek için  
 Bu dosyada belirtilen yapılandırma ayarları Net.TCP Bağlantı Noktası Paylaşım Hizmeti kullanan bir bilgisayardaki tüm hizmetleri etkilediğinden, genel olarak, SMSvcHost.exe.config dosyasının içeriğini değiştirirken dikkatli olunmalıdır. Buna, Windows İşlem Etkinleştirme Hizmeti'nin (WAS) TCP Etkinleştirme özelliklerini kullanan Windows Vista'daki uygulamalar dahildir.  
  
 Ancak, bazen Net.TCP Bağlantı Noktası Paylaşım Hizmeti için varsayılan yapılandırmayı değiştirmeniz gerekebilir. Örneğin, varsayılan değer `maxPendingAccepts` 4 * işlemci sayısıdır. Bağlantı noktası paylaşımını kullanan çok sayıda hizmet barındıran sunucular, maksimum iş elde etmek için bu değeri artırabilir. Varsayılan değer `maxPendingConnections` 100'dür. Hizmeti çağıran birden çok eşzamanlı istemci varsa ve hizmet istemci bağlantılarını bırakıyorsa, bu değeri artırmayı da düşünmelisiniz.  
  
 SMSvcHost.exe.config ayrıca bağlantı noktası paylaşım hizmetinden yararlanabilecek işlem kimlikleri hakkında bilgi içerir. Bir işlem paylaşılan bir TCP bağlantı noktasından yararlanmak için bağlantı noktası paylaşım hizmetine bağlandığında, bağlantı işleminin işlem kimliği bağlantı noktası paylaşım hizmetinden yararlanmasına izin verilen kimlikler listesiyle karşılaştırılır. Bu kimlikler, SMSvcHost.exe.config dosyasının \<izin veren Hesaplar> bölümünde güvenlik tanımlayıcıları (SID'ler) olarak belirtilir. Varsayılan olarak, bağlantı noktası paylaşım hizmetini kullanma izni sistem hesaplarına (LocalService, LocalSystem ve NetworkService) ve Yöneticiler grubunun üyelerine verilir. Başka bir kimlik olarak çalışan bir işlemin (örneğin, kullanıcı kimliği) bağlantı noktası paylaşım hizmetine bağlanmasına izin veren uygulamaların, SMSvcHost.exe.config'e uygun SID'yi açıkça eklemesi gerekir (bu değişiklikler SMSvc.exe işlemi yeniden başlatılıncaya kadar uygulanmaz).  
  
> [!NOTE]
> Kullanıcı Hesabı Denetimi (UAC) etkinleştirilmiş Windows Vista sistemlerinde, yerel kullanıcılar hesapları Yöneticiler grubunun bir üyesi olsa bile yüksek izinlere ihtiyaç duyar. Bu kullanıcıların yükseklik olmadan bağlantı noktası paylaşım hizmetinden yararlanabilmeleri için, kullanıcının SID'sinin (veya kullanıcının üye olduğu bir \<grubun SID'sinin) SMSvcHost.exe.config'in izin verilen Hesaplar> bölümüne açıkça eklenmesi gerekir.  
  
> [!WARNING]
> Varsayılan SMSvcHost.exe.config dosyası, SMSvcHost.exe izlemenin hizmet izlemelerini engellemesini önlemek için bir özel `etwProviderId` belirtir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<net.tcp>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
