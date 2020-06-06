---
title: <add> / <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850387"
---
# <a name="add-of-namespacetable"></a>\<add> / \<namespaceTable>
Bu, daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşleme için bir ad alanı içeren bir yapılandırma öğesini temsil eder.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|ad alanı|Ad alanını içeren bir dize.|  
|koy|Bu ad alanı için öneki içeren bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
