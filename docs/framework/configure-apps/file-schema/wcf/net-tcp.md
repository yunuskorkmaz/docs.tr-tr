---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 12709d58d9192825598b15a50baa10a54450226e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178079"
---
# \<net.tcp>

NET için yapılandırma ayarlarını belirtir. Birden çok işlemin aynı TCP bağlantı noktasını paylaşmasına izin veren TCP bağlantı noktası paylaşım hizmeti.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
## <a name="syntax"></a>Syntax  
  
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
|`listenBacklog`|Paylaşılan bağlantıdan kabul edilen ancak henüz Windows Communication Foundation (WCF) hizmetlerine dağıtılan en fazla bekleyen bağlantıları belirten bir tamsayı. Varsayılan değer 10 ' dur.|  
|`maxPendingAccepts`|Paylaşım hizmeti için dinleme uç noktasındaki en fazla bekleyen eşzamanlı iş parçacığı sayısını belirten bir tamsayı. Varsayılan değer 2 ' dir.|  
|`MaxPendingConnections`|Dinleyicinin uygulama tarafından kabul edilmesini bekleye, en fazla bağlantı sayısı. Bu kota değeri aşıldığında, kabul edilmesini beklemek yerine yeni gelen bağlantılar bırakılır. İleti güvenliği gibi bağlantı özellikleri istemcinin birden fazla bağlantı açmasına neden olabilir. Bu kota değerini ayarlarken hizmet yöneticileri bu ek bağlantıları dikkate almalıdır. Varsayılan değer 10 ' dur.|  
|`receiveTimeout`|<xref:System.TimeSpan>Çerçeveleme verilerini okumak ve alt çizgi bağlantılarından bağlantı dağıtma işlemini gerçekleştirmek için zaman aşımını belirten bir. Varsayılan değer "00:00:10" dır.|  
|`teredoEnabled`|Bağlantı noktası paylaşım hizmetinin, WCF Hizmetleri adına TCP bağlantı noktalarında dinlemek için Microsoft Teredo hizmetini kullanıp kullanmadığını gösteren bir Boolean değer. Varsayılan değer: `false`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|`securityIdentifier`WCF hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirtmek için bir özniteliği içeren yapılandırma öğelerinin bir koleksiyonu ve paylaşım hizmetine bağlantı erişimi verilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|SMSvcHost.exe dinleyici işlemi için yapılandırma ayarlarını içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bağlantı noktası paylaşımı hakkında daha fazla bilgi için bkz. [net. TCP bağlantı noktası paylaşma](../../../wcf/feature-details/net-tcp-port-sharing.md). Bağlantı noktası paylaşım hizmetini nasıl yapılandıracağınızı anlamak için bkz. [net. TCP bağlantı noktası paylaşım hizmetini yapılandırma](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [Net.TCP Bağlantı Noktası Paylaşımı](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [Net.TCP Bağlantı Noktası Hizmetini Yapılandırma](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
