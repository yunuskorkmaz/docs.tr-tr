---
title: "&lt;yönlendirme&gt; &lt;filtreleri&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c9dd9faf63ade725bb8bea12b40390fd30c91973
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltersgt-of-ltroutinggt"></a>&lt;yönlendirme&gt; &lt;filtreleri&gt;

Türünü belirleme yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri hesaplanırken kullanılacak.

[**\<system.serviceModel >**](system-servicemodel.md)   
&nbsp;&nbsp;[**\<Yönlendirme >**](routing.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<filtreleri >**

## <a name="syntax"></a>Sözdizimi

```xml
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String" 
              filterData="String" 
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [**\<Filtre >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | Türünü belirleyen bir yönlendirme filtre içeren [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> gelen iletileri hesaplanırken kullanılır. |

### <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| [**\<Yönlendirme >**](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Türünü belirleme yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için ne zaman iletileri göndermek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak bir Filtre eşleşir. |

## <a name="see-also"></a>Ayrıca bkz.

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
