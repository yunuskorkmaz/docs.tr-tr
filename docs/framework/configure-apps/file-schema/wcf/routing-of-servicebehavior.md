---
title: '&lt;serviceBehavior&gt; &lt;yönlendirme&gt;'
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 5fb7febe365f73acf09ba74b07215fe9cc659efb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a>&lt;serviceBehavior&gt; &lt;yönlendirme&gt;
Dinamik yönlendirme yapılandırması değiştirilmesine izin veren yönlendirme hizmeti çalışma zamanı erişim sağlar.  
  
 \<system.ServiceModel>  
\<davranışları >  
\<serviceBehaviors>  
\<davranışı >  
\<Yönlendirme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String" 
               routeOnHeadersOnly="Boolean" 
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|filterTable|Yönlendirme hizmeti tarafından değerlendirilecek filtreleri içeren yönlendirme tablosunun adını belirten dize. Bu değer eşleşmelidir `name` özniteliği bir [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) öğesinde [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) bölümü.|  
|routeOnHeaderOnly|Filtre hem ileti gövdesi ve üst bilgi veya yalnızca üstbilgi inceleyin olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|soapProcessingEnabled|SOAP işleme gerçekleşip gerçekleşmediğini belirten bir Boole değeri.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmetin davranışı yapılandırmasına eklendiğinde, bu yapılandırma öğesi için hizmeti Yönlendirme sağlar. Bu öğe hizmeti tarafından kullanılacak gerçek yönlendirme tablosu belirtebilirsiniz.  
  
 Bu yapılandırma bölümü kullanarak, dağıtım düzeni değiştiğinde yönlendirme ayarlarınızı kolay bir şekilde değiştirebilirsiniz. Çalışma zamanında yeni yönlendirme ayarlarıyla yönlendirme uzantınızı kaydedebilirsiniz ve yeni iletileri güncelleştirilmiş yapılandırma bilgilerini kullanarak yönlendirme hizmeti başlar ve ne olursa olsun kuralları kullanarak yürütülen iletileri/oturumları bırakarak sırasında oturumlar, bulunduğunuz Bunlar başlatıldığında yerleştirin.  Bu oturum için güvenli, daha az geri dönüşüm yeniden yapılandırılması yönlendirme hizmeti çalışma zamanı sırasında yeteneği verir.  
  
