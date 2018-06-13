---
title: '&lt;backupList&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 7e7361b24c0444b5f3d51a6f5bf079d5eb2dee18
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745558"
---
# <a name="ltaddgt-of-ltbackuplistgt"></a>&lt;backupList&gt; &lt;ekleme&gt;
Bir yedekleme endpoint öğesi tanımlayan bir yapılandırma öğesi temsil eder.  
  
 \<system.serviceModel>  
\<Yönlendirme >  
\<backupLists >  
\<backupList >  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Yedekleme uç noktanın adını belirten dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Birincil endpoint ulaşılamıyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktaları listesini içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
