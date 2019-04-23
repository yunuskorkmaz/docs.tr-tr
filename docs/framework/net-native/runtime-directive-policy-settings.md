---
title: Çalışma Zamanı Yönerge İlkesi Ayarları
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9015ec35c2a3d13b986eb9524e4f2984d909eb21
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098240"
---
# <a name="runtime-directive-policy-settings"></a>Çalışma Zamanı Yönerge İlkesi Ayarları
> [!NOTE]
>  Bu konuda, .NET Native Geliştirici yayın öncesi bir yazılım olan Önizleme, ifade eder. Önizlemesi'nden indirebileceğiniz [Microsoft Connect Web sitesi](https://go.microsoft.com/fwlink/?LinkId=394611) (kayıt gerekir).  
  
 .NET Native için çalışma zamanı yönerge İlkesi ayarları, çalışma zamanında türler ve tür üyeleri için meta veri kullanılabilirliğini belirleyemedi. Yansıma, serileştirme ve seri durumundan çıkarma veya COM veya Windows çalışma zamanı için .NET Framework türlerinin hazırlama kullanan işlemleri gerekli meta veriler başarısız ve bir özel durum. En sık karşılaşılan özel durumlar [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ve (söz konusu olduğunda Interop) [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md).  
  
 Çalışma zamanı İlkesi ayarları, bir çalışma zamanı yönergeleri tarafından kontrol edilir (. rd.xml) dosyası. Her çalışma zamanı yönerge İlkesi, bir derleme gibi belirli program öğesinin tanımlar ( [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md) öğe), bir tür ( [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğe), veya bir yöntemi ( [ \<yöntemi >](../../../docs/framework/net-native/method-element-net-native.md) öğesi). Yönergesi, yansıma ilke türleri, seri hale getirme ilke türleri ve sonraki bölümde açıklanan birlikte çalışma ilke türlerine tanımlayan bir veya daha fazla özniteliklerini içerir. Özniteliğin değeri, ilke ayarını tanımlar.  
  
## <a name="policy-types"></a>İlke türleri  
 İlke türlerinden üç kategoriye dosyalarını tanıyacak çalışma zamanı yönergeleri: yansıma, seri hale getirme ve birlikte çalışma.  
  
-   Yansıma ilke türleri, hangi meta verilerini yansıma için çalışma zamanında kullanılabilir hale getirileceğini belirler:  
  
    -   `Activate` örneklerinin etkinleştirmesi için oluşturucuları, çalışma zamanı erişimi denetler.  
  
    -   `Browse` denetimleri hakkında bilgi için sorgulama öğeleri program.  
  
    -   `Dynamic` programlama. tüm türleri ve üyeleri dinamik etkinleştirmek için çalışma zamanı erişimi denetler.  
  
     Aşağıdaki tabloda, yansıma ilke türleri ve birlikte kullanılabilirler program öğelerini listeler.  
  
    |Öğe|Etkinleştirme|Göz atma|Dinamik|  
    |-------------|--------------|------------|-------------|  
    |[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<Attributeımplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)||✓|✓|  
    |[\<alan >](../../../docs/framework/net-native/field-element-net-native.md)||✓|✓|  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)||✓|✓|  
    |[\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||✓|✓|  
    |[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parametresi >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)||✓|✓|  
    |[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
-   Seri hale getirme İlkesi türleri, hangi meta verileri serileştirme ve seri durumundan çıkarma için çalışma zamanında kullanılabilir hale getirileceğini belirler:  
  
    -   `Serialize` Oluşturucular, alanlar ve Özellikler Newtonsoft JSON serileştirici gibi üçüncü taraf kitaplıklar tarafından serileştirilecek tür örnekleri etkinleştirmek için çalışma zamanı erişimi denetler.  
  
    -   `DataContractSerializer` Oluşturucular, alanları ve tür örnekleri tarafından serileştirilecek etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı.  
  
    -   `DataContractJsonSerializer` Oluşturucular, alanları ve tür örnekleri tarafından serileştirilecek etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sınıfı.  
  
    -   `XmlSerializer` Oluşturucular, alanları ve tür örnekleri tarafından serileştirilecek etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler <xref:System.Xml.Serialization.XmlSerializer> sınıfı.  
  
     Aşağıdaki tabloda, serileştirme ilke türleri ve birlikte kullanılabilirler program öğelerini listeler.  
  
    |Öğe|Seri hale getirme|DataContractSerializer|DataContractJsonSerializer|XmlSerializer|  
    |-------------|---------------|----------------------------|--------------------------------|-------------------|  
    |[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Attributeımplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)|||||  
    |[\<alan >](../../../docs/framework/net-native/field-element-net-native.md)|✓||||  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)|||||  
    |[\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|||||  
    |[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Parametresi >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)|✓||||  
    |[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|✓|  
    |[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|✓|  
  
-   Birlikte çalışma ilke türleri, hangi meta veri başvuruları türleri, değer türleri ve işlev işaretçileri, COM ve Windows çalışma zamanı geçirmek için çalışma zamanında kullanılabilir hale getirileceğini belirler:  
  
    -   `MarshalObject` COM ve Windows çalışma zamanı için başvuru türleri için yerel hazırlama denetler.  
  
    -   `MarshalDelegate` işlev işaretçileri olarak temsilci türlerinin yerel hazırlama denetler.  
  
    -   `MarshalStructure` COM ve Windows çalışma zamanı değer türleri için yerel hazırlama denetler.  
  
     Aşağıdaki tabloda, birlikte çalışma ilke türleri ve birlikte kullanılabilirler program öğelerini listeler.  
  
    |Öğe|MarshalObject|MarshalDelegate|MarshalStructure|  
    |-------------|-------------------|---------------------|----------------------|  
    |[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<Attributeımplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)||||  
    |[\<alan >](../../../docs/framework/net-native/field-element-net-native.md)||||  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)||||  
    |[\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||||  
    |[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parametresi >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)||||  
    |[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<türü >](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
## <a name="policy-settings"></a>İlke ayarları  
 Her ilke türü, aşağıdaki tabloda listelenen değerlerden biri olarak ayarlanabilir. Tür üyelerini temsil eden öğe diğer öğeleri ilke ayarlarından farklı bir dizi desteklediğini unutmayın.  
  
|İlke ayarı|Açıklama|`Assembly`, `Namespace`, `Type`, ve `TypeInstantiation` öğeleri|`Event`, `Field`, `Method`, `MethodInstantiation`, ve `Property` öğeleri|  
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|`All`|Tüm türleri ve .NET Native araç zinciri kaldırmaz üyeleri için ilke sağlar.|✓||  
|`Auto`|Varsayılan ilkenin ilke türü için bir program öğesi için kullanılması gerektiğini belirtir. Bu ilke türü için bir ilke atlama için aynıdır. `Auto` genellikle ilkeyi bir üst öğeden devralındı belirtmek için kullanılır.|✓|✓|  
|`Excluded`|İlkeyi belirli program öğesi için devre dışı olduğunu belirtir. Örneğin, çalışma zamanı yönerge:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> Bu meta verileri belirtir `BusinessClasses.Person` ya göz atmak için veya dinamik olarak oluşturmak ve değiştirmek sınıf kullanılamıyor `Person` nesneleri.|✓|✓|  
|`Included`|Meta veri üst türü için kullanılabilir durumdaysa, bir ilke sağlar.||✓|  
|`Public`|Türe veya üyeye gereksizdir ve bu nedenle kaldırır araç zincirinizi belirler sürece genel tür veya üyeler için ilke sağlar. Bu ayar farklıdır `Required Public`, araç zincirinizi gereksiz olduğunu belirlerse bile, genel türler ve üyeler için bu meta veri sağlar. her zaman kullanılabilir.|✓||  
|`PublicAndInternal`|Türe veya üyeye gereksizdir ve bu nedenle kaldırır araç zincirinizi belirler sürece genel ve iç türleri veya üyeleri için ilke sağlar. Bu ayar farklıdır `Required PublicAndInternal`, araç zincirinizi gereksiz olduğunu belirlerse olsa da ortak hem de dahili türler ve üyeler için meta verilerin sağlar her zaman kullanılabilir.|✓||  
|`Required`|Bir üye için ilke etkin ve kullanılacak üye görünse de, meta verilerin kullanılabilir olması gerektiğini belirtir.||✓|  
|`Required Public`|Genel türleri veya üyeleri için ilke sağlar ve genel türler ve üyeler için her zaman kullanılabilir bu meta veri sağlar. Bu ayar farklıdır `Public`, araç zincirinizi genel türler ve üyeler kullanılabilir yalnızca meta verileri getiren gerekli olduğunu belirler.|✓||  
|`Required PublicAndInternal`|Genel ve iç türleri veya üyeleri için ilke sağlar ve ortak hem de dahili türler ve üyeler için her zaman kullanılabilir bu meta veri sağlar. Bu ayar farklıdır `PublicAndInternal`, araç zincirinizi genel ve iç türleri ve üyeleri kullanılabilir yalnızca meta verileri getiren gerekli olduğunu belirler.|✓||  
|`Required All`|Tüm türler ve üyeler olup olmadığını kullanılan ve etkinleştirir İlkesi kendileri için tutmak araç zinciri gerektirir.|✓||  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
