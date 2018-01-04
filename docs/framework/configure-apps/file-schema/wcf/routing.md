---
title: "&lt;Yönlendirme&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ef71753a4b0ff20a966842119adb6e637ded1f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltroutinggt"></a>&lt;Yönlendirme&gt;

Türünü belirleme yönlendirme bir filtre kümesi tanımlamak için yapılandırma bölümünü temsil eder [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için ne zaman iletileri göndermek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak bir Filtre eşleşir.

[**\<system.serviceModel >**](system-servicemodel.md)   
&nbsp;&nbsp;**\<Yönlendirme >**

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
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String" 
               filterName="String" 
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
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
| [**\<filtreleri >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | Bir dizi türünü belirleme yönlendirme filtreleri içeren [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] gelen iletileri değerlendirirken MessageFilter kullanılır. |
| [**\<filterTables >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | Yönlendirme filtreleri ve filtre eşleştiğinde kullanmak için hangi uç noktaya belirtmek için hedef uç noktaları arasında eşlemeler içerir. |

### <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| **\<Sistem. ServiceModel >** | Tüm WCF yapılandırma öğelerinin kök öğesi. |

## <a name="see-also"></a>Ayrıca bkz.

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
