---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 7e440810fee1dddb7025d1385b1edb4838d98a39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925919"
---
# <a name="datacontractserializer"></a>\<dataContractSerializer >
İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer>. Bu öğe iki farklı hiyerarşilerde oluşur. Bunlardan biri aşağıdaki şema hiyerarşisi bölümünde listelenir ve diğer açıklamalar bölümünde listelenir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranış >  
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
|IgnoreExtensionDataObject|Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğu zaman, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri. Bu öznitelik yalnızca `<dataContractSerializer>` `<behavior>` öğesinin altında ayarlanabilir.|  
|MaxItemsInObjectGraph|Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı. Bu öznitelik 65536 ' dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >](behavior-of-servicebehaviors.md)|Bir hizmetin davranışına yönelik ayarların koleksiyonu.|  
|[\<System. Runtime. Serialization >](system-runtime-serialization.md)|<xref:System.Runtime.Serialization> Ad alanı bölümünün kök öğesini temsil eder ve seçeneklerini <xref:System.Runtime.Serialization.DataContractSerializer>ayarlamak için öğeleri içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu konunun giriş bölümünde belirtildiği gibi, \<X509Extension > öğesinin gerçekleştiği ikinci hiyerarşisidir.  
  
 [\<System. Runtime. Serialization >](system-runtime-serialization.md)  
  
 [\<dataContractSerializer >](datacontractserializer-element.md)  
  
 Bilinen türler hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [Veri Anlaşması Bilinen Türler](../../../wcf/feature-details/data-contract-known-types.md)
- [Veri Aktarma ve Seri Hale Getirme](../../../wcf/feature-details/data-transfer-and-serialization.md)
