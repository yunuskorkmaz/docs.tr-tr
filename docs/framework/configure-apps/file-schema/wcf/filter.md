---
description: 'Hakkında daha fazla bilgi edinin: <filter>'
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 993d2265ac3a714475e8cbe9e8a2c3f93c46bde2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664684"
---
# \<filter>

Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü <xref:System.ServiceModel.Dispatcher.MessageFilter> , ayrıca filtrenin gerektirdiği destekleyici verileri veya parametreleri belirleyen bir yönlendirme filtresi tanımlar.

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
## <a name="syntax"></a>Syntax  
  
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
| customType | Filtre olarak kullanılacak özel türün tam nitelikli tür adını içeren bir dize. , `filterType` Olarak ayarlandıysa `custom` , bu öznitelik oluşturulacak sınıfın tam nitelikli tür adını içerir.  `filterData` özel tür filtresi değerlendirmesi sırasında kullanılacak değerleri de içerebilir. |
| filterData | Filtre verilerini içeren bir dize. Bu özniteliği belirtme hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> .. |
| filterType | Filtre türünü içeren bir dize. Bu öznitelik <xref:System.ServiceModel.Routing.Configuration.FilterType> türü.  Bunun özniteliğiyle nasıl çalıştığı hakkında daha fazla bilgi için `filterData` bkz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> .. |
| name       | Bu filtre öğesinin benzersiz adını içeren bir dize. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| ------- | ----------- |
| [\<routing>](routing.md) | Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümü <xref:System.ServiceModel.Dispatcher.MessageFilter> . |

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
