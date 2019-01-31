---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 9c4c7fa4f778642d549deebce6e7476f4da13a0d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283692"
---
# <a name="entries"></a>\<Giriş >
Bir yönlendirme girişi, ne zaman eşleşen filtre ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri içerir.  
  
 \<system.serviceModel>  
\<Yönlendirme >  
\<routingTables >  
\<Tablo >  
\<Giriş >  
  
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
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<filtreleri >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Bu önceden tanımlanmış bir istemci uç noktası için bir filtre eşler. Bu filtreyle eşleşen iletileri bu hedefe gönderilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Bir yönlendirme tablosu içeren bir yapılandırma bölümü.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
