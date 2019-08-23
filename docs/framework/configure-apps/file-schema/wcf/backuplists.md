---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: b65cc4d04b5304e93b70509c9db3bc2248accb7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926430"
---
# <a name="backuplists"></a>\<backupLists >
Hata işlemede kullanılan bir yedekleme hizmetleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder. Her alt öğe, yönlendirme hizmetinin birincil uç noktaya ulaşılamadığından kullanmasını istediğiniz uç nokta kümesini belirten bir yedekleme listesidir. Listedeki ilk uç nokta kapalıysa, yönlendirme hizmeti otomatik olarak listedeki bir sonrakine devreder.  Bu sayede, istemci uygulamanızı karmaşık desenleri nasıl ele geçirebileceğiniz veya tüm hizmetlerinizin dağıtıldığı konusunda, uygulamanıza güvenilirlik eklemenin hızlı bir yolunu sunar.  
  
 \<system.serviceModel>  
\<Yönlendirme >  
\<backupLists >  
  
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
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Filtre >](filter.md)|Birincil uç noktaya ulaşılamadığından, yönlendirme hizmeti 'nin kullanmasını istediğiniz uç noktaların listesini içerir. biçimindeki telefon numarasıdır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Yönlendirme >](routing.md)|Gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü ve hedef bitiş noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlamak için bir yapılandırma bölümünü temsil eder. Filtre eşleştiğinde iletileri gönder.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
