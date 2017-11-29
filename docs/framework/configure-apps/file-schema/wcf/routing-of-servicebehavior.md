---
title: "&lt;serviceBehavior&gt; &lt;yönlendirme&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4e5c27b2b276e6659680dabfd9460c6d072bad3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a>&lt;serviceBehavior&gt; &lt;yönlendirme&gt;
Dinamik yönlendirme yapılandırması değiştirilmesine izin veren yönlendirme hizmeti çalışma zamanı erişim sağlar.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
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
  
