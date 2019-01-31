---
title: <add> , <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 7267b8719987ecd25bcca78a7897a0d4172a42ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264576"
---
# <a name="add-of-entries"></a>\<Ekle >, \<girişleri >
Bu önceden tanımlanmış bir istemci uç noktası için bir filtre eşlemeleri bir yönlendirme girişi temsil eder. Bu filtreyle eşleşen iletileri bu hedefe gönderilir.  
  
 \<system.serviceModel>  
\<Yönlendirme >  
\<filterTables >  
\<filterTable >  
\<Giriş >  
\<Ekle >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|backupList|Yedekleme uç noktaları listesini bir başvuru belirten bir dize.|  
|uç noktası|Bir başvuru tarafından belirtilen filtreyle eşleşen iletileri alacak bir istemci uç noktası belirten bir dize `filterName` özniteliği.|  
|filterName|Bir filtre öğeye başvuru belirten bir dize.|  
|öncelik|Bu giriş önceliğini belirten bir tamsayı.<br /><br /> Yönlendirme tablosundaki girdileri en düşük önceliği olan 0 ile önceliğine bağlı olarak değerlendirilir. Tüm girişleri belirli bir öncelik için eşzamanlı olarak değerlendirilir, hiçbir eşleşen girişi bulundu geçerli öncelik için öncelik düzeye değerlendirilir.<br /><br /> Bu değer isteğe bağlıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Yönlendirme eşleme girişleri içeren bir yapılandırma bölümü.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
