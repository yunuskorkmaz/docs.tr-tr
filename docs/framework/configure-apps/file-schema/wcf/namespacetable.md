---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: 0316e983446644671ead2f8f843dc91b493b29c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933166"
---
# <a name="namespacetable"></a>\<namespaceTable >

Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.

**\<System. serviceModel >**    
&nbsp;&nbsp; **\<Yönlendirme >**    
&nbsp;&nbsp;&nbsp;&nbsp; **\<namespaceTable >**
  
## <a name="syntax"></a>Sözdizimi  
  
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

Yok.

### <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [ **\<Filtre >** ](filter.md) | XPath ifadeleri için kullanılan bir ad alanı ön eki eşlemesini tanımlar. |

### <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| [ **\<Yönlendirme >** ](routing.md) | Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü ve hedef bitiş noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder. Filtre eşleştiğinde iletileri gönder. |

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
