---
title: "Net.TCP Bağlantı Noktası Hizmetini Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b8b0d1920e70f0d9b6f837800bcc049999f6fde7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>Net.TCP Bağlantı Noktası Hizmetini Yapılandırma
Net.TCP taşıması kullanan kendi kendini barındıran Hizmetleri denetleyebilir birkaç Gelişmiş ayarları gibi `ListenBacklog` ve `MaxPendingAccepts`, ağ iletişimi için kullanılan temel alınan TCP yuva davranışını yönetir. Ancak, her yuva için bu ayarları yalnızca varsayılan olarak etkin aktarım bağlama bağlantı noktası paylaşımı, devre dışı bıraktı, bağlama düzeyinde uygulanır.  
  
 Net.tcp bağlama zaman sağlayan bağlantı noktası paylaşma (ayarlayarak `portSharingEnabled =true` aktarım bağlama öğesi üzerindeki), örtük olarak bir dış işlem (Net.TCP bağlantı noktası Paylaşımı hizmeti barındıran öğesine SMSvcHost.exe,) sağlayan TCP yuva kendi adına yönetmek için. Örneğin, TCP kullanılırken belirtin:  
  
```xml  
    <tcpTransport   
        portSharingEnabled="true"  
/>  
```  
  
 Bu şekilde yapılandırıldığında, hizmetin aktarım bağlama öğesi üzerindeki belirtilen tüm yuva ayarları SMSvcHost.exe tarafından belirtilen yuva ayarları lehinde göz ardı edilir.  
  
 SMSvcHost.exe yapılandırmak için erişimi adlı bir XML yapılandırma dosyası oluşturun ve SMSvcHost.exe yürütülebilir dosya (örneğin, C:\Windows\Microsoft.NET\Framework\v4.5) aynı fiziksel dizine yerleştirin.  
  
 Aşağıdaki örnek, örnek bir erişimi, açıkça belirtilen tüm yapılandırılabilir değerleri için varsayılan ayarları gösterilmektedir.  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Zaman erişimi değiştirmek için  
 Genel olarak, bu dosyada belirtilen herhangi bir yapılandırma ayarı tüm hizmetleri Net.TCP bağlantı noktası Paylaşımı hizmeti kullanan bir bilgisayarda etkilediğinden dikkatli erişimi dosyasının içeriğini değiştirirken olunmalıdır. Bu uygulamaları içerir [!INCLUDE[wv](../../../../includes/wv-md.md)] TCP etkinleştirme özellikleri Windows İşlem Etkinleştirme Hizmeti (WAS) kullanın.  
  
 Ancak, bazen Net.TCP bağlantı noktası Paylaşımı hizmeti varsayılan yapılandırmasını değiştirmeniz gerekebilir. Örneğin, varsayılan değeri `maxPendingAccepts` 4 * işlemcilerin sayısı. Çok sayıda bağlantı noktası Paylaşımı kullanan hizmetler barındıran sunucuları en yüksek verimlilik elde etmek için bu değeri artırabilirsiniz. İçin varsayılan değer `maxPendingConnections` 100'dür. Bu değer Ayrıca hizmet çağırma birden çok eşzamanlı istemciler varsa ve bu hizmeti istemci bağlantıları bırakarak artırmayı denemelisiniz.  
  
 Erişimi Paylaşım Hizmeti bağlantı noktası yapabilir kimlikleri kullanmak işlemi hakkında bilgiler de içerir. Bir işlem paylaşılan bir TCP kullanmak için hizmet Paylaşımı bağlantı noktasına bağlandığında, bağlantı noktası, bağlanma işlem kimliği işlem yapmak için izin verilen kimlikleri listesini karşı işaretli Paylaşım Hizmeti bağlantı noktasını kullanın. Bu kimlikleri güvenlik tanımlayıcılarını (SID'ler) belirtilen \<allowAccounts > erişimi dosyasının bölümü. Varsayılan olarak, hizmet bağlantı noktası kullanma izni Administrators grubunun üyeleri yanı sıra sistem hesapları (Yerelhizmet, LocalSystem ve NetworkService) verilir. Açıkça uygun SID Paylaşım Hizmeti bağlantı noktasına bağlanmak için başka bir kimlik (örneğin, bir kullanıcı kimliği) olarak çalışan bir işlemin izin uygulamaları (SMSvc.exe işlem olana kadar bu değişiklikler uygulanmaz erişimi eklemeniz gerekir yeniden).  
  
> [!NOTE]
>  Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] hesaplarında Yöneticiler grubunun bir üyesi olsa bile sistemler ile kullanıcı hesabı denetimi (etkin, yerel kullanıcılar gerektiren UAC) yükseltilmiş izinler. Bu kullanıcıların yapmasına izin vermek için bağlantı noktası hizmeti ayrıcalık, kullanıcının SID değeri (ya da kullanıcının üyesi olduğu bir grubun SID) olmadan paylaşma kullanımını açıkça eklenmelidir \<allowAccounts > erişimi bölümü.  
  
> [!WARNING]
>  Özel bir varsayılan erişimi dosyayı belirtir `etwProviderId` SMSvcHost.exe izleme ile hizmet izlemeleri engellemesini önlemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<NET.TCP >](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
