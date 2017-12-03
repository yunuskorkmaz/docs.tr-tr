---
title: dataContractSerializer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a64f5ae4573efbd8c0f7d622e6b94b7786585bb1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="datacontractserializer"></a>dataContractSerializer
Yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 \<Sistem. ServiceModel >  
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
 [Veri sözleşmesi bilinen türler](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Veri aktarma ve seri hale getirme](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
