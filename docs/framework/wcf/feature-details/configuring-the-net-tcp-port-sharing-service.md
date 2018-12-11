---
title: Net.TCP Bağlantı Noktası Hizmetini Yapılandırma
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: 7232fc587aa7f63167034f7474d6c5e7476048ed
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153481"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>Net.TCP Bağlantı Noktası Hizmetini Yapılandırma
Net.TCP taşıma kullanan şirket içinde barındırılan Hizmetler Denetim birkaç Gelişmiş ayarları gibi `ListenBacklog` ve `MaxPendingAccepts`, ağ iletişimi için kullanılan temel alınan TCP yuva davranışını yönetir. Ancak, her yuva için bu ayarları yalnızca, varsayılan olarak etkin aktarım bağlama bağlantı noktası paylaşımı, devre dışı bırakmışsa bağlama düzeyinde uygulanır.  
  
 Net.tcp bağlama zaman sağlar bağlantı noktası Paylaşımı (ayarlayarak `portSharingEnabled =true` aktarım bağlama öğesi üzerindeki), örtük olarak bir dış işlem (Net.TCP bağlantı noktası paylaşma hizmeti barındıran yani SMSvcHost.exe,) sağlayan kendi adına TCP yuva yönetmek için. Örneğin, TCP kullanılırken belirtin:  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 Bu şekilde yapılandırıldığında, hizmetin aktarım bağlama öğesi üzerinde belirtilen herhangi bir yuva ayarı SMSvcHost.exe tarafından belirtilen yuva ayarları yerine göz ardı edilir.  
  
 SMSvcHost.exe yapılandırmak için erişimi adlı bir XML yapılandırma dosyası oluşturun ve SMSvcHost.exe yürütülebilir dosya (örneğin, C:\Windows\Microsoft.NET\Framework\v4.5) aynı fiziksel dizine yerleştirin.  
  
 Aşağıdaki örnek, bir ' % s'örnek erişimi, açıkça belirtilen tüm yapılandırılabilir değerler için varsayılan ayarlarla gösterir.  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!—16 * # of processors -->  
          maxPendingAccepts="4"<!— 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!—30 seconds -->  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Erişimi değiştirme zamanı  
 Genel olarak, bu dosyada belirtilen herhangi bir yapılandırma ayarı tüm hizmetler Net.TCP bağlantı noktası paylaşım hizmetini kullanan bir bilgisayara etkilediğinden bakım erişimi dosyasının içeriğini değiştirirken edilmelidir. Bu uygulamaları içerir [!INCLUDE[wv](../../../../includes/wv-md.md)] TCP Etkinleştirmesi özellikleri Windows İşlem Etkinleştirme Hizmeti (WAS) kullanın.  
  
 Ancak, bazen Net.TCP bağlantı noktası Paylaşımı hizmeti varsayılan yapılandırmasını değiştirmeniz gerekebilir. Örneğin, varsayılan değeri `maxPendingAccepts` 4 * İşlemci sayısı. Çok sayıda bağlantı noktası Paylaşımı kullanan hizmetleri barındıran sunucular, en yüksek performans sağlamak için bu değeri artırabilirsiniz. İçin varsayılan değer `maxPendingConnections` 100'dür. Bu değer bir hizmete çağrı yapma birden çok eşzamanlı istemciler varsa ve hizmeti istemci bağlantıları bırakıyor artırıldığında düşünmelisiniz.  
  
 Erişimi de bağlantı noktası paylaşma hizmeti yapabilir kimlikleri kullanmak işlemi hakkında bilgi içerir. Bir işlem paylaşımı paylaşılan bir TCP kullanmak için hizmet bağlantı noktasına bağlandığında bağlantı noktası, bağlantı işlem kimliği işlem yapmak için izin verilen kimlikleri listesini karşı işaretli Paylaşım Hizmeti bağlantı noktasını kullanın. Bu kimlikleri güvenlik tanımlayıcılarını (SID'ler) belirtilen \<allowAccounts > erişimi dosyasının bölümü. Varsayılan olarak, hizmet bağlantı noktası kullanma izni Administrators grubu üyelerinin yanı sıra sistem hesapları (LocalService, LocalSystem ve NetworkService) verilir. Açıkça uygun SID Paylaşım Hizmeti bağlantı noktasına bağlanmak için başka bir kimlik (örneğin, bir kullanıcı kimliği) olarak çalışan bir işlemin tanıyan uygulamaları (SMSvc.exe işlem olana kadar bu değişiklikler uygulanmaz erişimi eklemeniz gerekir yeniden).  
  
> [!NOTE]
>  Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] sistemleri ile kullanıcı hesabı denetimi (etkinleştirilmişse, yerel kullanıcıların UAC) yükseltilmiş izinler bile hesabını Administrators grubunun bir üyesidir. Bu kullanıcıların yapmasına izin vermek için bağlantı noktası paylaşma hizmeti olmadan yükseltme, kullanıcının SID (veya kullanıcının üyesi olduğu bir grubun SID) kullanımını açıkça eklenmelidir \<allowAccounts > bölümüne erişimi.  
  
> [!WARNING]
>  Özel bir varsayılan erişimi dosyasını belirtir `etwProviderId` SMSvcHost.exe İzleme hizmeti izlemeleri engellemesini önlemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<NET.TCP >](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
