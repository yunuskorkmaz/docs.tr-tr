---
title: '&lt;findCriteria&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8643c4f0affb9f693b42cd7631696200bb279489
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfindcriteriagt"></a>&lt;findCriteria&gt;
Bir bulma hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi. Ölçüt arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütleri (ne kadar süreyle arama son) bulun.  
  
 \<Sistem. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|süre|Ağ üzerinde yanıtları Hizmetleri'nden için beklenecek en uzun süreyi belirtir Timespan değeri. Varsayılan süre 20 saniyedir...|  
|maxResults|Bir ağ veya Internet üzerinde Hizmetleri'nden beklemek zorunda yanıtların en fazla sayısını belirten bir tamsayı. Belirtilen değer önce alınan en büyük yanıt varsa `duration` özniteliği geçtikten, bulma işlemi sona erer.|  
|scopeMatchBy|Uç noktası'nın araştırma iletiyle kapsamlarda eşleşen sırasında kullanılacak eşleştirme algoritması belirtin URI.<br /><br /> Beş desteklenen kapsam eşleştirme kuralları vardır. Bir kapsam eşleşen kural belirtmezseniz `ScopeMatchByPrefix` kullanılır. Bu hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<contractTypeNames >](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|İş akışı hizmeti sözleşme türlerinin adlarını içeren yapılandırma öğelerinin koleksiyonunu...|  
|\<Uzantıları >, \<findCriteria >|Uzantılar sağlarlar XML öğesi nesneleri koleksiyonu.|  
|[\<kapsamları >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Mutlak URI içeren bir bulma işlemi sırasında belirli bir hizmeti veya hizmetleri bulmak için kullanılan nesneleri koleksiyonu.<br /><br /> Belirli hizmet bulunursa, başarılı bir eşleşme hizmet URI'si ile eşleşen zorluklar işlemek kapsam kuralları yardımıyla bazen kapsam URI arasındaki yapıldı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Hizmet bulma işlemi bir istemci olarak'na katılmak için bir uygulama tarafından gerekli ayarları içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
