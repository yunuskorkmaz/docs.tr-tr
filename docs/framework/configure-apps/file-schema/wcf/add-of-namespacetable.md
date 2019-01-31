---
title: <add> , <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 0e463ffa87e67bc5f100f9acf38ace6450b0ce40
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268711"
---
# <a name="add-of-namespacetable"></a>\<Ekle >, \<namespaceTable >
Eşleme sonra yönlendirme için XPath filtrelerinde kullanılan önek için ad alanı içeren bir yapılandırma öğesi temsil eder.  
  
 \<system.serviceModel>  
\<Yönlendirme >  
\<namespaceTable >  
\<Ekle >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|ad alanı|Ad alanı içeren bir dize.|  
|Ön eki|Bu ad alanı ön eki içeren bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namespaceTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|Ardından yönlendirme için XPath filtrelerinde kullanılan önek eşletirmeleri için ad alanı içeren bir öğe kümesini tanımlayan bir yapılandırma bölümünü temsil eder.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
