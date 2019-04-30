---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: bff19f106d86c73dea80b8b57bb73442eaa2cf9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704043"
---
# <a name="filter"></a>\<Filtre >

Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi tanımlar<xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri de tüm destekleyici veri ya da filtre tarafından parametre olarak değerlendirilirken kullanılacak.

\<system.serviceModel > \<yönlendirme > \<filtreleri > \<Filtre >
  
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
| CustomType | Filtre olarak kullanılmak üzere özel türünün tam olarak nitelenmiş tür adını içeren bir dize. Varsa `filterType` ayarlanır `custom`, bu öznitelik sınıfı oluşturmak için tam olarak nitelenmiş tür adını içerir.  `filterData` Özel tür filtrenin değerlendirmesi sırasında kullanılacak değerler de içerebilir. |
| Filtre veri | Filtre verisi içeren bir dize. Bu öznitelik belirtme hakkında daha fazla bilgi için bkz. <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| Filtre türü | Filtre türü içeren bir dize. Bu özniteliktir <xref:System.ServiceModel.Routing.Configuration.FilterType> türü.  Bu ile nasıl çalıştığı hakkında daha fazla bilgi için `filterData` özniteliği için bkz: <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| name       | Bu filtre öğesinin benzersiz adını içeren bir dize. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| ------- | ----------- |
| [\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlamak için bir yapılandırma bölümünü<xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri değerlendirmek kullanılacak. |

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
