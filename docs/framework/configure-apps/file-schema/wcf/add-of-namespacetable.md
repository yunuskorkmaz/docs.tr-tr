---
title: <add> / <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 32eff2e7bfdf1aee4c7d37a0e06166afba3cb398
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566740"
---
# <a name="add-of-namespacetable"></a>\<\<NamespaceTable > > ekleyin
Bu, daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşleme için bir ad alanı içeren bir yapılandırma öğesini temsil eder.  
  
 \<system.serviceModel>  
\<Yönlendirme >  
\<namespaceTable >  
\<> Ekle  
  
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
|prefix|Bu ad alanı için öneki içeren bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namespaceTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|Daha sonra yönlendirme için XPath filtrelerinde kullanılabilecek önek eşlemelerine yönelik ad alanı içeren bir öğe kümesi tanımlamak için bir yapılandırma bölümünü temsil eder.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
