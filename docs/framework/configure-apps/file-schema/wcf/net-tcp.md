---
title: '&lt;net.tcp&gt;'
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: c67aeca183eb476460fa0be2c6dcd9c6077165d8
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579349"
---
# <a name="ltnettcpgt"></a>&lt;net.tcp&gt;
Ağ yapılandırma ayarlarını belirtir. TCP bağlantı noktası paylaşımı birden çok işlem aynı TCP bağlantı noktasını paylaşmasına izin veren hizmeti.  
  
 \<system.serviceModel.activation>  
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
|`listenBacklog`|Paylaşılan bağlantıdan kabul edilir, ancak henüz Windows Communication Foundation (WCF) hizmetlerine gönderilen değil bekleyen en yüksek bağlantı belirten bir tamsayı. Varsayılan değer 10'dur.|  
|`maxPendingAccepts`|Hizmetler için olan uç noktaları en fazla bekleyen eşzamanlı kabul iş parçacığı belirten bir tamsayı. Varsayılan değer 2'dir.|  
|`MaxPendingConnections`|Uygulama tarafından kabul edilmeyi bekliyor dinleyicinin sahip olabileceği bağlantıları sayısı. Bu kota değeri aşıldığında, yeni gelen bağlantılar kesilir yerine kabul edilmeyi bekliyor. Bağlantı özellikleri ileti güvenliği gibi birden fazla bağlantı açmak bir istemci neden olabilir. Hizmet yöneticileri, bu ek bağlantılar için bu kota değeri ayarlarken hesap. Varsayılan değer 10'dur.|  
|`receiveTimeout`|A `TimeSpan` ve çerçeveleme verilerini okumak ve altı çizili bağlantılardan bağlantı dağıtımını gerçekleştirmek için zaman aşımını belirtir. Varsayılan değer "00: 00:10".|  
|`teredoEnabled`|Hizmet bağlantı noktası WCF hizmetlerinin adına TCP bağlantı noktalarında dinlemek için Microsoft Teredo hizmetini kullanıp kullanmadığını gösteren bir Boole değeri. Varsayılan, `false` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<allowAccounts >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Bir koleksiyon içeren yapılandırma öğelerinin bir `securityIdentifier` barındıran WCF hizmetleri ve Paylaşım Hizmeti bağlantı erişim izni verilen işlemleri için kullanıcı hesabı belirtmek için özniteliği.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Dinleyici işlem SMSvcHost.exe için yapılandırma ayarlarını içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bağlantı noktası paylaşma ile ilgili daha fazla bilgi için bkz: [Net.TCP bağlantı noktası paylaşma](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md). Bağlantı noktası hizmetini yapılandırma hakkında bilgi almak için bkz. [Net.TCP bağlantı noktası paylaşım hizmetini yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [Net.TCP Bağlantı Noktası Paylaşımı](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [Net.TCP Bağlantı Noktası Hizmetini Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
