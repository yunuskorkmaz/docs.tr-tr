---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: eb8ff3905f7696f4c71a79e31db1b8f82c9f0d3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925592"
---
# <a name="findcriteria"></a>\<findCriteria >
Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi. Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.  
  
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
|süre|Ağdaki hizmetlerden gelen yanıtlar için beklenecek en uzun süreyi belirten bir TimeSpan değeri. Varsayılan süre 20 saniyedir.|  
|maxResults|Ağ veya Internet üzerindeki hizmetlerden, beklenecek en fazla yanıt sayısını belirten bir tamsayı. `duration` Öznitelikte belirtilen değerin süresi geçtiğinde en fazla yanıt alınmışsa, bulma işlemi sonlanır.|  
|scopeMatchBy|Araştırma iletisindeki kapsamları uç noktayla eşleştirirken kullanılacak eşleşen algoritmayı belirten bir URI.<br /><br /> Desteklenen beş kapsam eşleştirme kuralı vardır. Kapsam eşleştirme kuralı belirtmezseniz, `ScopeMatchByPrefix` kullanılır. Bu hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<contractTypeNames >](contracttypenames.md)|İş akışı hizmeti sözleşme türlerinin adlarını içeren yapılandırma öğelerinin koleksiyonu.|  
|\<\<FindCriteria > Uzantıları >|Uzantıları sağlayan XML öğe nesneleri koleksiyonu.|  
|[\<kapsamlar >](scopes.md)|Belirli bir hizmet veya hizmeti bulmak için bulma işlemi sırasında kullanılan mutlak URI 'Ler içeren nesneler koleksiyonu.<br /><br /> Belirli bir hizmet bulunursa, hizmet URI 'si ile kapsam URI 'SI arasında başarılı bir eşleşme yapılmıştır, bazen eşleştirmeyi ele alan kapsam kurallarının yardımıyla.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](standardendpoints.md)|Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
