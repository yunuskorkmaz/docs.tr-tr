---
title: '&lt;NET.TCP&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3d22b6feef80dbff8c7f20b130ce2b0f9702c9e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnettcpgt"></a>&lt;NET.TCP&gt;
Ağ Yapılandırması ayarlarını belirtir. TCP bağlantı noktası paylaşımı aynı TCP bağlantı noktasını paylaşmak birden çok işlemlerinin sağlayan hizmet.  
  
 \<system.serviceModel.activation >  
\<NET.TCP >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="Integer"  
          maxPendingAccepts="Integer"  
          maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan"  
          teredoEnabled="Boolean">  
          <allowAccounts>  
             <!-- LocalSystem account -->   
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->   
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->   
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->   
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only)-->   
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a>Tür  
 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`listenBacklog`|Paylaşılan bağlantı kabul edilir, ancak henüz için gönderilir değil en fazla bekleyen bağlantı belirten bir tamsayı [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Hizmetleri. Varsayılan değer 10'dur.|  
|`maxPendingAccepts`|Dinleme bitiş Paylaşım Hizmeti için en çok bekleyen eşzamanlı kabul iş parçacığı belirten bir tamsayı. Varsayılan değer 2'dir.|  
|`MaxPendingConnections`|Uygulama tarafından kabul edilmesi için bekleyen dinleyicisi olabilir bağlantılarının maksimum sayısı. Bu kota değeri aşıldığında, yeni gelen bağlantıları bırakılan yerine kabul edilmesi için bekleniyor. İleti güvenliği gibi bağlantı özellikleri birden fazla bağlantı açmak bir istemci neden olabilir. Hizmet yöneticileri bu ek bağlantılar için bu kota değeri ayarlanırken dikkate. Varsayılan değer 10'dur.|  
|`receiveTimeout`|A `TimeSpan` çerçeveleme veri okumak ve altı çizili bağlantılarından bağlantı gönderme gerçekleştirmek için zaman aşımını belirtir. Varsayılan değer "00: 00:10".|  
|`teredoEnabled`|Hizmet bağlantı noktası TCP üzerinde dinlenecek Microsoft Teredo hizmeti kullanıp kullanmadığını belirten bir Boole değeri bağlantı noktalarını adına [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri. Varsayılan, `false` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<allowAccounts >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|İçeren yapılandırma öğelerinin koleksiyonu bir `securityIdentifier` kullanıcı hesapları için işlemleri barındıran belirtmek için özniteliği [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri ve Paylaşım Hizmeti bağlantı erişim verilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel.activation >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bağlantı noktası paylaşma hakkında daha fazla bilgi için bkz: [Net.TCP bağlantı noktası paylaşma](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded). Paylaşım Hizmeti bağlantı noktasını yapılandırmak nasıl anlamak için bkz: [Net.TCP bağlantı noktası Paylaşımı hizmeti yapılandırma](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [Net.TCP Bağlantı Noktası Paylaşımı](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded)  
 [Net.TCP Bağlantı Noktası Hizmetini Yapılandırma](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)
