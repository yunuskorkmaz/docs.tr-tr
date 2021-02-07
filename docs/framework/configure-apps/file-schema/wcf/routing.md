---
description: 'Hakkında daha fazla bilgi edinin: <routing>'
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 62222b527a14310b66015d4fdc4503e6cff25c8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683352"
---
# \<routing>

Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> . Ayrıca, bir filtre eşleştiğinde ileti göndermek için hedef uç noktalarını tanımlayan yönlendirme tablolarını tanımlar.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
## <a name="syntax"></a>Syntax  
  
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

Yok

### <a name="child-elements"></a>Alt öğeleri

|     | Description |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | Gelen iletiler değerlendirilirken Windows Communication Foundation (WCF) MessageFilter türünü belirten bir yönlendirme filtreleri kümesi içerir. |
| [**\<filterTables>**](filtertables.md) | Filtre eşleştiğinde kullanılacak bitiş noktasını belirtmek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içerir. |

### <a name="parent-elements"></a>Üst öğeler

|     | Description |
| --- | ----------- |
| **\<system.ServiceModel>** | Tüm WCF yapılandırma öğelerinin kök öğesi. |

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
