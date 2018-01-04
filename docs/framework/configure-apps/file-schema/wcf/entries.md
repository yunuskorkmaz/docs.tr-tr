---
title: '&lt;girdileri&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1bd6fd679d3f6440ff685c8cd2646b1fa0a13e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltentriesgt"></a>&lt;girdileri&gt;
Yönlendirme filtreleri ve ne zaman bir filtre ile eşleşen için iletileri göndermek için hedef uç noktaları arasındaki eşlemeleri içeren bir yönlendirme girişi.  
  
 \<system.serviceModel >  
\<Yönlendirme >  
\<routingTables >  
\<Tablo >  
\<girişleri >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<filtreleri >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Bir filtre önceden tanımlanmış bir istemci uç noktası eşler. Bu filtre ile eşleşen iletileri bu hedefe gönderilir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Bir yönlendirme tablosu içeren bir yapılandırma bölümü.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
