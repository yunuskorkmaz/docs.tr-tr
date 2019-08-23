---
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: cef34a8836c7b17fe9a85cac190090f42653df14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919247"
---
# <a name="declaredtypes"></a>\<declaredTypes >
Seri durumdan çıkarılırken <xref:System.Runtime.Serialization.DataContractSerializer> kullandığı bilinen türleri içerir.  
  
 Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).  
  
 system.runtime.serialization  
\<dataContractSerializer >  
\<declaredTypes >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="String ">
          <knownType type="String">
            <parameter index="Integer"/>
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
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<> Ekle](add-of-declaredtypes-element.md)|Bilinen türler gerektiren türler ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<dataContractSerializer >](datacontractserializer-of-system-runtime-serialization.md)|İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XML kodu, tanımlanmış türleri ve bir `DataContractSerializer` öğeye eklenen bilinen türleri gösterir. Örnek, eklenmekte olan üç tür gösterir. Birincisi, "Item" adlı bilinen bir tür kullanan "Orders" adlı özel bir türdür. Belirtilen ikinci tür, bilinen bir <xref:System.Collections.Generic.List%601> tür olarak `Item` kullanılan bir türüdür. Son olarak, belirtilen üçüncü tür bir <xref:System.Collections.Generic.Dictionary%602>. <xref:System.Collections.Generic.Dictionary%602> Sınıf türü, iki tür parametresi olan genel bir türdür. İlki anahtarı temsil eder ve ikincisi değeri temsil eder. Aşağıdaki örnek, bir <xref:System.Collections.Generic.List%601> ikinci türü (değer) bilinen türler listesine ekler. Bilinen türde kullanılacak tür `index` parametresini belirtmek için özniteliğini kullanmanız gerekir. Bu durumda, değer türü "1" olarak ayarlanmış dizin özniteliği ile gösterilir (koleksiyon sıfır tabanlıdır).  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
            <parameter index="1"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer >](datacontractserializer-element.md)
- [Veri Anlaşması Bilinen Türler](../../../wcf/feature-details/data-contract-known-types.md)
- [\<> Ekle](add-of-declaredtypes-element.md)
