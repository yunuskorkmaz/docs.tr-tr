---
title: '&lt;namespaceTable&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 1d3b61fa6653b3910e65b95fa96fd0657e72bf7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632917"
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a>&lt;namespaceTable&gt; &lt;ekleme&gt;
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
