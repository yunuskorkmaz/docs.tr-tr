---
title: '&lt;Filtre&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 186c511cd8a69cef5e30e369641628a10a0972d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt"></a>&lt;Filtre&gt;

Türünü belirler yönlendirme filtre tanımlayan [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri de tüm destekleyici veri veya filtre tarafından gerekli parametreleri olarak hesaplanırken kullanılacak.

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
| customType | Filtre olarak kullanılacak özel türünün tam olarak nitelenmiş tür adını içeren dize. Varsa `filterType` ayarlanır `custom`, bu öznitelik sınıfı oluşturmak için tam olarak nitelenmiş tür adını içerir.  `filterData`Ayrıca özel türü filtresi değerlendirme sırasında kullanılacak değerler içerebilir. |
| Filtre veri | Filtre veri içeren bir dize. Bu öznitelik belirtme hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| filterType | Filtre türü içeren bir dize. Bu özniteliktir <xref:System.ServiceModel.Routing.Configuration.FilterType> türü.  Bunun ile işleyişi hakkında daha fazla bilgi için `filterData` özniteliği için bkz: <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| name       | Bu filtre öğesinin benzersiz adını içeren dize. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| ------- | ----------- |
| [\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Türünü belirleme yönlendirme bir filtre kümesi tanımlamak için bir yapılandırma bölümü [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri hesaplanırken kullanılacak. |

## <a name="see-also"></a>Ayrıca bkz.

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
