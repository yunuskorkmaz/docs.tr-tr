---
title: <dataContractSerializer> <System. Runtime. Serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: a8d379e7a37bca0cdb58836a6afdf814320e2411
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190195"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a>\<dataContractSerializer> / \<system.runtime.serialization>

İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer"
                       type="String" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|IgnoreExtensionDataObject|Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğu zaman, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri. Bu öznitelik yalnızca `<dataContractSerializer>` öğesinin altında ayarlanabilir `<behavior>` .|  
|MaxItemsInObjectGraph|Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı. Bu öznitelik 65536 ' dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<xref:System.Runtime.Serialization.DataContractSerializer>Seri durumdan çıkarılırken kullandığı bilinen türleri içerir.<br /><br /> Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|Ad alanı bölümünün kök öğesini temsil eder <xref:System.Runtime.Serialization> ve seçeneklerini ayarlamak için öğeleri içerir <xref:System.Runtime.Serialization.DataContractSerializer> .|  
  
## <a name="remarks"></a>Açıklamalar  

 Bilinen türler hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization.DataContractSerializer> . ve [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [Veri Sözleşmesi Bilinen Türler](../../../wcf/feature-details/data-contract-known-types.md)
