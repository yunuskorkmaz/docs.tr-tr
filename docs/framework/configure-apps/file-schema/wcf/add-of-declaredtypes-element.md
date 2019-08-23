---
title: <add><declaredTypes> öğesinin
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 1ea008dcc72d555b00e9648ace95bb9522ffc2c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920182"
---
# <a name="add-of-declaredtypes-element"></a>\<\<DeclaredTypes > öğesinin > ekleyin
Seri durumdan çıkarma <xref:System.Runtime.Serialization.DataContractSerializer> sırasında tarafından kullanılan bir tür ekler. Her bir tanımlı tür, bir alan veya tanımlanmış türün özelliği olarak döndürülecek bilinen türleri içerir.  
  
 system.runtime.serialization  
\<dataContractSerializer >  
\<declaredTypes >  
\<\<DeclaredTypes > > ekleyin  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|türü|Gerekli dize özniteliği.<br /><br /> Tür adını (ad alanı dahil), derleme adını, sürüm numarasını, kültürü ve ortak anahtar belirtecini belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<knownType >](knowntype.md)|Eklenmekte olan, belirtilen tanımlı tür için bilinen türü belirtir. Belirtilen tür genel bir türse, bilinen türü döndürmek için hangi genel parametrenin kullanıldığını belirtmek üzere `<knownType>` öğesine bir parametre öğesi de eklemeniz gerekir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<declaredTypes >](declaredtypes.md)|Tarafından seri durumundan çıkarma sırasında bilinen türler gerektiren türleri içerir <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Bu öğenin kullanılmasıyla ilgili bir örnek için bkz. [ DataContractSerializer>.\<](datacontractserializer-element.md)  
  
> [!NOTE]
> <xref:System.Object> Türü <xref:System.Configuration.ConfigurationErrorsException> olarak eklerseniz ,biroluşturulur.`<declaredType>` Bunun nedeni <xref:System.Object> , türün yapılandırmada belirtilen bir tür olarak kullanılamaz.  
  
## <a name="example"></a>Örnek  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Veri Anlaşması Bilinen Türler](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer >](datacontractserializer-element.md)
- [\<\<DeclaredTypes > > ekleyin](add-of-declaredtypes-element.md)
