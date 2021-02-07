---
description: 'Hakkında daha fazla bilgi edinin: <namespaceTable>'
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 73bfac93fba3247c02c2d86d1482af2563015a76
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684093"
---
# \<namespaceTable>

Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
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
| [**\<filter>**](filter.md) | XPath ifadeleri için kullanılan bir ad alanı ön eki eşlemesini tanımlar. |

### <a name="parent-elements"></a>Üst öğeler

|     | Description |
| --- | ----------- |
| [**\<routing>**](routing.md) | Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü belirleyen bir yönlendirme filtresi kümesini tanımlamak için bir yapılandırma bölümünü temsil eder <xref:System.ServiceModel.Dispatcher.MessageFilter> . Ayrıca, bir filtre eşleştiğinde ileti göndermek için hedef uç noktalarını tanımlayan yönlendirme tablolarını tanımlar. |

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
