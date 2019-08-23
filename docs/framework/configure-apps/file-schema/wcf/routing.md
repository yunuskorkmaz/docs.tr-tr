---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 3c7e9cb1284ab55c8dd199d9fb47a223698814f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934134"
---
# <a name="routing"></a>\<Yönlendirme >

Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> türünü ve hedef bitiş noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder. Filtre eşleştiğinde iletileri gönder.

[ **\<System. serviceModel >** ](system-servicemodel.md)   
&nbsp;&nbsp; **\<Yönlendirme >**
  
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
| [ **\<Filtreler >** ](filters-of-routing.md) | Gelen iletiler değerlendirilirken Windows Communication Foundation (WCF) MessageFilter türünü belirten bir yönlendirme filtreleri kümesi içerir. |
| [ **\<filterTables >** ](filtertables.md) | Filtre eşleştiğinde kullanılacak bitiş noktasını belirtmek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içerir. |

### <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| **\<sistemin. ServiceModel >** | Tüm WCF yapılandırma öğelerinin kök öğesi. |

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
