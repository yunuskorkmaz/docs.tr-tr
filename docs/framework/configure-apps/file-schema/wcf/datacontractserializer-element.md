---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: b635f03d1e4a6628a76d678f7366482717276376
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116395"
---
# <a name="datacontractserializer"></a>\<dataContractSerializer >
İçin yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>. Bu öğe, iki farklı hiyerarşilere gerçekleşir. Bir listelenir aşağıdaki şema hiyerarşisini bölümü ve diğer açıklamalar bölümünde listelenir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
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
|IgnoreExtensionDataObject|Bunu edilirken bitiş noktası tarafından sağlanan veri yoksay belirten bir Boole değeri serileştirilecek veya serisi. Bu öznitelik yalnızca ayarlanabilir `<dataContractSerializer>` altında `<behavior>` öğesi.|  
|maxItemsInObjectGraph|Serileştirmek veya seri durumdan çıkarılacak öğeleri maksimum sayısını belirten bir tamsayı. Bu öznitelik 65536'dır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|Bir koleksiyon için bir hizmet davranışını ayarlar.|  
|[\<System.Runtime.Serialization >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|İçin olan kök öğesini temsil eden <xref:System.Runtime.Serialization> ad uzayı bölümü ve seçeneklerini ayarlamak için öğeleri içeren <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu konunun giriş belirtildiği gibi ikinci hiyerarşide budur \<X509Extension > öğesi oluşur.  
  
 [\<System.Runtime.Serialization >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 Bilinen türler hakkında daha fazla bilgi için bkz: <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [Veri Anlaşması Bilinen Türler](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Veri Aktarma ve Seri Hale Getirme](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
