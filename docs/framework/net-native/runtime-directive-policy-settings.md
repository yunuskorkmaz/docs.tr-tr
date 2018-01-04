---
title: "Çalışma Zamanı Yönerge İlkesi Ayarları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 698e8ef926740f33f8a0a192680b5cebb45c9d79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-directive-policy-settings"></a>Çalışma Zamanı Yönerge İlkesi Ayarları
> [!NOTE]
>  Bu konu, .NET yerel geliştirici yayın öncesi yazılımı olan Önizleme, ifade eder. Önizlemesi'nden indirebilirsiniz [Microsoft Connect Web](http://go.microsoft.com/fwlink/?LinkId=394611) (kayıt gerektirir).  
  
 .NET yerel için çalışma zamanı yönerge İlkesi ayarları çalışma zamanında meta veri türleri ve tür üyeleri için kullanılabilirliğini belirler. Yansıma, seri hale getirme ve seri durumdan çıkarma veya COM veya Windows çalışma zamanı için .NET Framework türlerinin hazırlama Bel işlemleri gerekli meta veriler başarısız ve bir özel durum. En sık karşılaşılan özel durumlar [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ve (durumunda birlikte çalışabilirliği) [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md).  
  
 Çalışma zamanı ilke ayarları, bir çalışma zamanı yönergeleri tarafından denetlenir (. rd.xml) dosyası. Her çalışma zamanı yönerge İlkesi bütünleştirilmiş gibi bir belirli bir program öğesi için tanımlar ( [ \<derleme >](../../../docs/framework/net-native/assembly-element-net-native.md) öğesi), bir tür ( [ \<türü >](../../../docs/framework/net-native/type-element-net-native.md) öğesi), ya da bir yöntemi ( [ \<yöntemi >](../../../docs/framework/net-native/method-element-net-native.md) öğesi). Yönergesi yansıma ilke türleri, seri hale getirme ilke türleri ve sonraki bölümde açıklanan birlikte çalışma ilke türlerini tanımlayan bir veya daha fazla özniteliklerini içerir. Öznitelik değeri ilke ayarını tanımlar.  
  
## <a name="policy-types"></a>İlke türleri  
 Çalışma zamanı yönergeleri dosyalarını tanıyacak ilke türlerinden üç kategoride: yansıma, seri hale getirme ve birlikte çalışabilirlik.  
  
-   Yansıma ilke türleri, hangi meta verilerini yansıma için çalışma zamanında sunulacağını belirleyin:  
  
    -   `Activate`örneklerinin etkinleştirmesi Oluşturucular, çalışma zamanı erişimi kontrol eder.  
  
    -   `Browse`denetimleri hakkında bilgi için sorgulama öğeleri program.  
  
    -   `Dynamic`programlama tüm türleri ve üyeleri dinamik etkinleştirmek için çalışma zamanı erişimi kontrol eder.  
  
     Aşağıdaki tabloda, yansıma ilke türleri ve hangi kullanılabilmesi için program öğeleri listeler.  
  
    |Öğe|Etkinleştirme|Gözat|Dinamik|  
    |-------------|--------------|------------|-------------|  
    |[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<Attributeımplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)||✓|✓|  
    |[\<Alanı >](../../../docs/framework/net-native/field-element-net-native.md)||✓|✓|  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)||✓|✓|  
    |[\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||✓|✓|  
    |[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parametresi >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)||✓|✓|  
    |[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<Türü >](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
-   Seri hale getirme ilke türleri, hangi meta verileri seri hale getirme ve seri durumundan çıkarma için çalışma zamanında sunulacağını belirleyin:  
  
    -   `Serialize`Oluşturucular, alanları ve üçüncü taraf kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından sıralanmasına türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.  
  
    -   `DataContractSerializer`Oluşturucular, alanları ve türü örnekleri tarafından seri hale etkinleştirmek için özellikleri, çalışma zamanı erişimi denetleyen <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı.  
  
    -   `DataContractJsonSerializer`Oluşturucular, alanları ve türü örnekleri tarafından seri hale etkinleştirmek için özellikleri, çalışma zamanı erişimi denetleyen <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sınıfı.  
  
    -   `XmlSerializer`Oluşturucular, alanları ve türü örnekleri tarafından seri hale etkinleştirmek için özellikleri, çalışma zamanı erişimi denetleyen <xref:System.Xml.Serialization.XmlSerializer> sınıfı.  
  
     Aşağıdaki tabloda, serileştirme ilke türleri ve hangi kullanılabilmesi için program öğeleri listeler.  
  
    |Öğe|Serileştirme|DataContractSerializer|DataContractJsonSerializer|XmlSerializer|  
    |-------------|---------------|----------------------------|--------------------------------|-------------------|  
    |[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Attributeımplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)|||||  
    |[\<Alanı >](../../../docs/framework/net-native/field-element-net-native.md)|✓||||  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)|||||  
    |[\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|||||  
    |[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Parametresi >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)|✓||||  
    |[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Türü >](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|✓|  
  
-   Birlikte çalışma ilke türleri, hangi meta verilerin zamanında başvuruları türleri, değer türleri ve işlev işaretçileri COM ve Windows çalışma zamanı geçirmek için kullanılabilir hale getirileceğini belirleyin:  
  
    -   `MarshalObject`COM ve başvuru türleri için Windows çalışma zamanı için yerel hazırlama denetler.  
  
    -   `MarshalDelegate`işlev işaretçileri olarak temsilci türleri yerel hazırlama denetler.  
  
    -   `MarshalStructure`COM ve Windows çalışma zamanı değer türleri için yerel hazırlama denetler.  
  
     Aşağıdaki tabloda birlikte çalışabilirlik ilke türleri ve hangi kullanılabilmesi için program öğeleri listeler.  
  
    |Öğe|MarshalObject|MarshalDelegate|MarshalStructure|  
    |-------------|-------------------|---------------------|----------------------|  
    |[\<Uygulama >](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<Derleme >](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<Attributeımplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Olay >](../../../docs/framework/net-native/event-element-net-native.md)||||  
    |[\<Alanı >](../../../docs/framework/net-native/field-element-net-native.md)||||  
    |[\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<Impliestype >](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<Yöntem >](../../../docs/framework/net-native/method-element-net-native.md)||||  
    |[\<Methodınstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||||  
    |[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parametresi >](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<Özellik >](../../../docs/framework/net-native/property-element-net-native.md)||||  
    |[\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<Türü >](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<Typeınstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
## <a name="policy-settings"></a>İlke ayarları  
 Her ilke türü, aşağıdaki tabloda listelenen değerlerden birini ayarlanabilir. Tür üyeleri temsil eden öğe diğer öğeleri İlkesi ayarlarından farklı bir kümesini desteklediğini unutmayın.  
  
|İlke ayarı|Açıklama|`Assembly`, `Namespace`, `Type`, ve `TypeInstantiation` öğeleri|`Event`, `Field`, `Method`, `MethodInstantiation`, ve `Property` öğeleri|  
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|`All`|İlke tüm türleri ve .NET yerel araç zinciri kaldırmaz üyeleri için etkinleştirir.|✓||  
|`Auto`|Bu program öğesi için ilke türü için varsayılan ilke kullanılması gerektiğini belirtir. Bu, bu ilke türü için bir ilke atlama için aynıdır. `Auto`genellikle ilkeyi bir üst öğeden devralındı belirtmek için kullanılır.|✓|✓|  
|`Excluded`|İlkenin belirli bir program öğesi için devre dışı olduğunu belirtir. Örneğin, çalışma zamanı yönerge:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> Bu meta verileri için belirtir `BusinessClasses.Person` sınıfı değil ya da göz atmak için veya dinamik olarak oluşturmak ve değiştirmek kullanılabilir `Person` nesneleri.|✓|✓|  
|`Included`|Üst türü için meta verileri varsa bir ilke etkinleştirir.||✓|  
|`Public`|Tür veya üye gerekli değildir ve bu nedenle kaldırır ve aracı zincir belirler sürece genel türleri veya üyeler için ilke sağlar. Bu ayar farklıdır `Required Public`, araç zinciri gereksiz olduğunu belirlerse bile, bu meta veri genel türleri ve üyeleri için sağlar her zaman kullanılabilir olur.|✓||  
|`PublicAndInternal`|Tür veya üye gerekli değildir ve bu nedenle kaldırır ve aracı zincir belirler sürece genel ve iç türleri veya üyeler için ilke sağlar. Bu ayar farklıdır `Required PublicAndInternal`, araç zinciri gereksiz olduğunu belirlerse bile, ortak ve iç türleri ve üyeleri için bu meta veri sağlar her zaman kullanılabilir olur.|✓||  
|`Required`|Üyesi için ilke etkinleştirilir ve üye kullanılacak görünse bile bu meta verinin kullanılabilir olacağını belirtir.||✓|  
|`Required Public`|Genel türler veya üyeler için ilke etkinleştirir ve genel türler ve üyeleri için her zaman kullanılabilir bu meta veri sağlar. Bu ayar farklıdır `Public`, hangi ortak türleri ve üyeleri kullanılabilir yalnızca meta verilerini araç zinciri yapar gerekli olduğunu belirler.|✓||  
|`Required PublicAndInternal`|Genel ve iç türler veya üyeler için ilke etkinleştirir ve ortak ve iç türleri ve üyeleri için her zaman kullanılabilir bu meta veri sağlar. Bu ayar farklıdır `PublicAndInternal`, hangi ortak ve iç türleri ve üyeleri kullanılabilir yalnızca meta verilerini araç zinciri yapar gerekli olduğunu belirler.|✓||  
|`Required All`|Aracı zincir tüm türleri ve üyeleri desteklemediğini kullanılan ve etkinleştirir ilkesi için kalmasını gerektirir.|✓||  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)
