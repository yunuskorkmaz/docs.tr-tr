---
title: '&lt;Yönlendirme&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 855faedfd2e9523e939174441b0cfa50e052b375
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565884"
---
# <a name="ltroutinggt"></a>&lt;Yönlendirme&gt;

Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için hedef bitiş noktalarını tanımlayan tabloları yapılırken kullanılacak ne zaman eşleşen bir filtre, iletileri gönderir.

[**\<system.serviceModel>**](system-servicemodel.md)   
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

Hiçbiri

### <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [**\<filtreleri >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | Windows Communication Foundation (WCF) MessageFilter türünü gelen iletileri değerlendirmek kullanılacağını belirlemek yönlendirme süzgeçleri kümesini içerir. |
| [**\<filterTables >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | Filtreler eşleştiğinde kullanmak için hangi uç noktaya belirtmek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri içerir. |

### <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| **\<sistemi. ServiceModel >** | Tüm WCF yapılandırma öğelerinin kök öğe. |

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
