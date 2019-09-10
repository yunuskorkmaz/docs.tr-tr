---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855248"
---
# <a name="filter"></a>\<Filtre >

Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü, ayrıca filtrenin gerektirdiği destekleyici verileri veya parametreleri belirleyen bir yönlendirme filtresi tanımlar.

[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;[ **\<Yönlendirme >** ](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtreler >** ](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Filtre >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

| Öznitelik  | Açıklama |
| ---------- | ----------- |
| customType | Filtre olarak kullanılacak özel türün tam nitelikli tür adını içeren bir dize. `filterType` , Olarak`custom`ayarlandıysa, bu öznitelik oluşturulacak sınıfın tam nitelikli tür adını içerir.  `filterData`özel tür filtresi değerlendirmesi sırasında kullanılacak değerleri de içerebilir. |
| filterData | Filtre verilerini içeren bir dize. Bu özniteliği belirtme hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| filterType | Filtre türünü içeren bir dize. Bu öznitelik <xref:System.ServiceModel.Routing.Configuration.FilterType> türü.  Bunun `filterData` özniteliğiyle nasıl çalıştığı hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| name       | Bu filtre öğesinin benzersiz adını içeren bir dize. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| ------- | ----------- |
| [\<Yönlendirme >](routing.md) | Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümü. |

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
