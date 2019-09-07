---
title: <routing> / <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397727"
---
# <a name="routing-of-servicebehavior"></a>\<\<ServiceBehavior > yönlendirme >
Yönlendirme yapılandırmasına dinamik değişiklik yapılmasına izin vermek için yönlendirme hizmetine çalışma zamanı erişimi sağlar.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Yönlendirme >**  
  
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
|filterTable|Yönlendirme hizmeti tarafından değerlendirilecek filtreleri içeren yönlendirme tablosunun adını belirten bir dize. Bu değer, `name` [FilterTables > bölümündeki bir FilterTable > öğesinin özniteliğiyle eşleşmelidir. \<](filtertables.md) [ \<](filtertable.md)|  
|yalnızca routeonheader|Filtrenin hem ileti gövdesini hem de üstbilgiyi veya yalnızca üstbilgiyi incelemenizi belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|soapProcessingEnabled|SOAP işlemenin gerçekleşmesi gerekip gerekmediğini belirten bir Boolean değer.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi hizmet için yönlendirmeyi sağlar. Bu öğedeki hizmet tarafından kullanılacak gerçek yönlendirme tablosunu belirtebilirsiniz.  
  
 Bu yapılandırma bölümünü kullanarak, dağıtım düzeniniz değiştiğinde hareket halindeyken yönlendirme ayarlarınızı değiştirebilirsiniz. Çalışma zamanında, kendi yönlendirme uzantınızı yeni yönlendirme ayarlarıyla kaydedebilir ve yönlendirme hizmeti yeni iletiler ve oturumlar için güncelleştirilmiş yapılandırma bilgilerini kullanmaya başlar ve bu durumda, hangi kuralların kullanıldığı konusunda uçuş iletilerini/oturumlarını bırakır başlatıldıklarında yer.  Bu sayede, çalışma zamanı sırasında yönlendirme hizmetinin oturum güvenli, geri dönüşüm için daha az yeniden yapılandırılması yapabilirsiniz.  
