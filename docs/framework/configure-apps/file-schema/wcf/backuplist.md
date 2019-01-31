---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 1e2b3eacbc845ad40030f3a48be2ef93c4ddbd8c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262441"
---
# <a name="backuplist"></a>\<backupList >
Bir birincil uç noktaya erişilemiyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç nokta kümesine numaralandırır yedek listesini tanımlamak için bir yapılandırma bölümünü temsil eder. Listedeki ilk uç kapalı ise, yönlendirme hizmeti otomatik olarak bir listesi için devredilmesini.  Bu istemci uygulamanıza karmaşık desenlerle nasıl ele alınacağını ya da tüm hizmetlerinizin dağıtıldığı öğretmek zorunda kalmadan uygulamanıza güvenilirlik eklemeniz için hızlı bir yol sağlar.  
  
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
|[\<Filtre >](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Yedekleme uç noktaları listesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bölümde, bir ileti için bir iletişim özel durumu olması durumunda birincil uç noktasına gönderilirken aktarılmaz uç noktaları sıralı bir koleksiyonunu içerir.  
  
 Birincil uç noktaya gönderme listelenen `endpointName` özniteliği [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) bir iletişim özel durumu ile başarısız oluyor, yönlendirme hizmeti ilk uç noktasına bu iletiyi göndermeyi deneyecek yapılandırma bölümü. Bu da bir iletişim özel durumu ile başarısız olursa, yönlendirme hizmeti iletişim özel durumu veya tüm uç noktaların dışındaki bir hata gönderme girişimi başarılı olana kadar döndürür, bu bölümde yer alan sonraki iletiye ileti göndermeye çalışır koleksiyonu bir hata döndürdü.  
  
 Bir iletişim özel durumu "Hedef" adlı birincil uç noktaya gönderme döndürürse, aşağıdaki örnekte, "alternateServiceQueue" ileti göndermek hizmet dener. Bu deneme bir iletişim özel durumu da döndürürse, yönlendirme hizmeti koleksiyonda sonraki uç nokta ileti göndermek dener.  
  
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
