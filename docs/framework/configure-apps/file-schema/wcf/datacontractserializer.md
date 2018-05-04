---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 0528ae823db500da3c3a1efc6934951c4e41cea7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="datacontractserializer"></a>dataContractSerializer
Yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 \<system.ServiceModel>  
\<davranışları >  
\<endpointBehaviors >  
\<davranışı >  
\<dataContractSerializer >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|ignoreExtensionDataObject|Yüklenmekte olan zaman bitiş noktası tarafından sağlanan verileri yoksayacak şekilde belirten bir Boole değeri serileştirilecek veya serisi.|  
|MaxItemsInObjectGraph|Tamsayı serileştirmek veya seri durumdan öğe sayısını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir uç nokta davranışını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bkz: <xref:System.Runtime.Serialization.DataContractSerializer> bilinen türleri hakkında daha fazla bilgi için.  
  
> [!CAUTION]
>  `<dataContractSerializer>` Davranışı öğesi (varsa) önce her zaman görünmelidir `<enableWebScript>` davranışı öğesi yapılandırma dosyasında. Aksi takdirde, bunun sonucunda oluşan davranışı tanımlanmamıştır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [Veri Anlaşması Bilinen Türler](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Veri Aktarma ve Seri Hale Getirme](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
