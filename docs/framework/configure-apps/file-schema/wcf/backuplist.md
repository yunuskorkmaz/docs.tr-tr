---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 478211755b9131c03b72777ee95ff7223b9092c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850277"
---
# \<backupList>
Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz bir uç nokta kümesini belirten bir yedekleme listesi tanımlamak için bir yapılandırma bölümünü temsil eder. Listedeki ilk uç nokta kapalıysa, yönlendirme hizmeti otomatik olarak listedeki bir sonrakine devreder.  Bu sayede, istemci uygulamanızı karmaşık desenleri nasıl ele geçirebileceğiniz veya tüm hizmetlerinizin dağıtıldığı konusunda, uygulamanıza güvenilirlik eklemenin hızlı bir yolunu sunar.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Bu uç nokta listesini tanımlamak için kullanılan adı belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<filter>](filter.md)||  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<routing>](routing.md)|Yedekleme uç noktalarının listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bölüm, birincil uç noktaya gönderilirken bir iletişim özel durumu olayında bir iletinin iletilebilecek sıralı bitiş noktaları koleksiyonunu içerir.  
  
 Özniteliğinde listelenen birincil uç noktaya gönderme bir `endpointName` [\<add>](add-of-entries.md) iletişim özel durumuyla başarısız olursa, yönlendirme hizmeti iletiyi bu yapılandırma bölümünde ilk uç noktaya göndermeye çalışır. Bu aynı zamanda bir iletişim özel durumu ile başarısız olursa, yönlendirme hizmeti iletiyi bu bölümde yer alan sonraki iletiye göndermeye çalışır, bu da gönderme girişimi başarılı olur, iletişim özel durumu dışında bir hata döndürür veya koleksiyondaki tüm uç noktalar bir hata döndürdü.  
  
 Aşağıdaki örnekte, "hedef" adlı birincil uç noktaya gönderme bir iletişim özel durumu döndürürse, hizmet iletiyi "alternateServiceQueue" olarak göndermeye çalışır. Bu girişim ayrıca bir iletişim özel durumu döndürürse, yönlendirme hizmeti iletiyi koleksiyondaki bir sonraki uç noktaya göndermeye çalışır.  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
