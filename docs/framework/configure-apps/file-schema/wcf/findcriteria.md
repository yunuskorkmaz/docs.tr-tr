---
title: '&lt;findCriteria&gt;'
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: b90e6cab923075dbf750dc0d26a0eb1196cfde32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741266"
---
# <a name="ltfindcriteriagt"></a>&lt;findCriteria&gt;
Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi. Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.  
  
 \<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            </contractTypeNames>
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
|süre|Ağdaki hizmetlerden yanıtları için beklenecek en uzun süreyi belirten bir Timespan değeri. Varsayılan süre 20 saniyedir.|  
|maxresults bağımsız değişkenini|İçin bir ağ veya Internet üzerinde hizmetlerden beklenilecek en fazla sayısını belirten bir tamsayı. En yüksek yanıt belirtilen değerden önce almış `duration` özniteliği geçti, bulma işlemi sona erer.|  
|scopeMatchBy|Kapsamlar araştırma iletisi ve onun uç noktasında alanları eşleştirirken kullanılan eşleştirme algoritmasını belirleyen bir URI.<br /><br /> Desteklenen beş kapsam eşleştirme kuralları vardır. Bir kapsam eşleşen kural belirtmezseniz `ScopeMatchByPrefix` kullanılır. Bu hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<contractTypeNames >](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|İş akışı hizmeti sözleşmesi türlerinin adlarını içeren yapılandırma öğelerinin koleksiyonu.|  
|\<Uzantılar >, \<findCriteria >|XML öğesi uzantıları sağlayan bir nesneleri koleksiyonu.|  
|[\<kapsamları >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Mutlak bir URI'leri içeren bir bulma işlemi sırasında belirli bir hizmet veya hizmetleri bulmak için kullanılan nesneleri koleksiyonu.<br /><br /> Hizmete bulunursa başarılı bir eşleşme hizmet URI'si ile eşleşen zorluklar işleyen kapsam kuralları yardımıyla bazen kapsam URI arasındaki yapıldı.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Hizmet keşif işlemine bir istemci olarak katılmak için bir uygulama tarafından gerekli olan ayarları içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
