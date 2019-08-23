---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: d5feab6cb374f98e683cf15f797de4f478e23131
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919916"
---
# <a name="backuplist"></a>\<backupList >
Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz bir uç nokta kümesini belirten bir yedekleme listesi tanımlamak için bir yapılandırma bölümünü temsil eder. Listedeki ilk uç nokta kapalıysa, yönlendirme hizmeti otomatik olarak listedeki bir sonrakine devreder.  Bu sayede, istemci uygulamanızı karmaşık desenleri nasıl ele geçirebileceğiniz veya tüm hizmetlerinizin dağıtıldığı konusunda, uygulamanıza güvenilirlik eklemenin hızlı bir yolunu sunar.  
  
 \<system.serviceModel>  
\<Yönlendirme >  
\<backupLists >  
\<backupList >  
  
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
|[\<Filtre >](filter.md)||  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönlendirme >](routing.md)|Yedekleme uç noktalarının listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bölüm, birincil uç noktaya gönderilirken bir iletişim özel durumu olayında bir iletinin iletilebilecek sıralı bitiş noktaları koleksiyonunu içerir.  
  
 Add > özniteliğindelistelenen`endpointName` birincil uç noktaya gönderme bir iletişim özel durumuyla başarısız olursa, yönlendirme hizmeti iletiyi bu yapılandırma bölümündeki ilk uç noktaya göndermeye çalışır. [ \<](add-of-entries.md) Aynı zamanda bir iletişim özel durumu ile başarısız olursa, yönlendirme hizmeti iletiyi bu bölümde bulunan sonraki iletiye göndermeye çalışır, çünkü gönderme girişimi başarılı olur, iletişim özel durumu dışında bir hata döndürür veya koleksiyon bir hata döndürdü.  
  
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
