---
title: Çalışma Zamanı Yönerge İlkesi Ayarları
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
ms.openlocfilehash: 7a8933decaec45e8000f3f3d1717847f333deddd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "76738496"
---
# <a name="runtime-directive-policy-settings"></a>Çalışma Zamanı Yönerge İlkesi Ayarları

> [!NOTE]
> Bu konu, yayın öncesi yazılım olan .NET Native geliştirici önizlemesine başvurur. Önizlemeyi [Microsoft Connect Web sitesinden](https://go.microsoft.com/fwlink/?LinkId=394611) indirebilirsiniz (kayıt gerekir).

.NET Native çalışma zamanı yönerge ilkesi ayarları, çalışma zamanında türler ve tür üyeleri için meta verilerin kullanılabilirliğini belirlemektir. Gerekli meta veriler olmadan, yansıma, serileştirme ve serisini kullanan işlemler veya .NET Framework türlerinin COM veya Windows Çalışma Zamanı sıralaması başarısız olabilir ve bir özel durum oluşturabilir. En yaygın özel durumlar [MissingMetadataException](missingmetadataexception-class-net-native.md) ve (birlikte çalışabilirlik durumunda) [MissingInteropDataException](missinginteropdataexception-class-net-native.md).

Çalışma zamanı ilke ayarları, bir çalışma zamanı yönergeleri (. RD. xml) dosyası tarafından denetlenir. Her çalışma zamanı yönergesi derleme ( [\<Assembly>](assembly-element-net-native.md) öğe), bir tür ( [\<Type>](type-element-net-native.md) öğe) veya bir Yöntem (öğe) gibi belirli bir program öğesi için ilkeyi tanımlar [\<Method>](method-element-net-native.md) . Yönergesi, yansıma ilkesi türlerini, serileştirme ilke türlerini ve sonraki bölümde ele alınan birlikte çalışma ilkesi türlerini tanımlayan bir veya daha fazla öznitelik içerir. Özniteliğin değeri, ilke ayarını tanımlar.

## <a name="policy-types"></a>İlke türleri

Çalışma zamanı yönergeleri dosyaları, ilke türlerinin üç kategorisini tanır: yansıma, serileştirme ve birlikte çalışma.

- Yansıma ilkesi türleri, yansıma için çalışma zamanında hangi meta verilerin kullanılabilir hale getirilceğini belirleme:

  - `Activate`örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.

  - `Browse`program öğeleri hakkında bilgi sorgulama denetimleri.

  - `Dynamic`Dinamik programlamayı etkinleştirmek için tüm türlere ve üyelere çalışma zamanı erişimini denetler.

  Aşağıdaki tabloda, yansıma ilkesi türleri ve bunların kullanılabileceği program öğeleri listelenmektedir.

  |Öğe|Etkinleştir|Gözat|Dinamik|
  |-------------|--------------|------------|-------------|
  |[\<Application>](application-element-net-native.md)|✔️|✔️|✔️|
  |[\<Assembly>](assembly-element-net-native.md)|✔️|✔️|✔️|
  |[\<AttributeImplies>](attributeimplies-element-net-native.md)|✔️|✔️|✔️|
  |[\<Event>](event-element-net-native.md)||✔️|✔️|
  |[\<Field>](field-element-net-native.md)||✔️|✔️|
  |[\<GenericParameter>](genericparameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<ImpliesType>](impliestype-element-net-native.md)|✔️|✔️|✔️|
  |[\<Method>](method-element-net-native.md)||✔️|✔️|
  |[\<MethodInstantiation>](methodinstantiation-element-net-native.md)||✔️|✔️|
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|
  |[\<Parameter>](parameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<Property>](property-element-net-native.md)||✔️|✔️|
  |[\<Subtypes>](subtypes-element-net-native.md)|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeParameter>](typeparameter-element-net-native.md)|✔️|✔️|✔️|

- Serileştirme ilke türleri serileştirme ve seri durumundan çıkarma için çalışma zamanında kullanılabilir hale getirilen meta verileri belirleme:

  - `Serialize`tür örneklerinin, Newtonsoft JSON seri hale getirici gibi üçüncü taraf kitaplıklar tarafından serileştirilmesi için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.

  - `DataContractSerializer`tür örneklerinin sınıf tarafından serileştirilmesine olanak tanımak için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler <xref:System.Runtime.Serialization.DataContractSerializer> .

  - `DataContractJsonSerializer`tür örneklerinin sınıf tarafından serileştirilmesine olanak tanımak için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .

  - `XmlSerializer`tür örneklerinin sınıf tarafından serileştirilmesine olanak tanımak için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler <xref:System.Xml.Serialization.XmlSerializer> .

  Aşağıdaki tabloda, serileştirme ilkesi türleri ve bunların kullanılabileceği program öğeleri listelenmektedir.

  |Öğe|Serialize|DataContractSerializer|DataContractJsonSerializer|Çağrılamıyor|
  |-------------|---------------|----------------------------|--------------------------------|-------------------|
  |[\<Application>](application-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Assembly>](assembly-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<AttributeImplies>](attributeimplies-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Event>](event-element-net-native.md)|||||
  |[\<Field>](field-element-net-native.md)|✔️||||
  |[\<GenericParameter>](genericparameter-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<ImpliesType>](impliestype-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Method>](method-element-net-native.md)|||||
  |[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|||||
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Parameter>](parameter-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Property>](property-element-net-native.md)|✔️||||
  |[\<Subtypes>](subtypes-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|✔️|
  |[\<TypeParameter>](typeparameter-element-net-native.md)|✔️|✔️|✔️|✔️|

- Birlikte çalışma ilkesi türleri, başvuru türlerini, değer türlerini ve işlev işaretçilerini COM 'a ve Windows Çalışma Zamanı geçirmek için çalışma zamanında hangi meta verilerin kullanılabilir hale getirilceğini belirlenir:

  - `MarshalObject`COM 'a yerel hazırlamayı ve başvuru türleri için Windows Çalışma Zamanı denetler.

  - `MarshalDelegate`temsilci türlerinin işlev işaretçileri olarak yerel sıralamasını denetler.

  - `MarshalStructure`COM 'a yerel hazırlamayı ve değer türleri için Windows Çalışma Zamanı denetler.

  Aşağıdaki tabloda birlikte çalışma ilkesi türleri ve bunların kullanılabileceği program öğeleri listelenmektedir.

  |Öğe|MarshalObject|MarshalDelegate|MarshalStructure|
  |-------------|-------------------|---------------------|----------------------|
  |[\<Application>](application-element-net-native.md)|✔️|✔️|✔️|
  |[\<Assembly>](assembly-element-net-native.md)|✔️|✔️|✔️|
  |[\<AttributeImplies>](attributeimplies-element-net-native.md)|✔️|✔️|✔️|
  |[\<Event>](event-element-net-native.md)||||
  |[\<Field>](field-element-net-native.md)||||
  |[\<GenericParameter>](genericparameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<ImpliesType>](impliestype-element-net-native.md)|✔️|✔️|✔️|
  |[\<Method>](method-element-net-native.md)||||
  |[\<MethodInstantiation>](methodinstantiation-element-net-native.md)||||
  |[\<Namespace>](namespace-element-net-native.md)|✔️|✔️|✔️|
  |[\<Parameter>](parameter-element-net-native.md)|✔️|✔️|✔️|
  |[\<Property>](property-element-net-native.md)||||
  |[\<Subtypes>](subtypes-element-net-native.md)|✔️|✔️|✔️|
  |[\<Type>](type-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|✔️|✔️|✔️|
  |[\<TypeParameter>](typeparameter-element-net-native.md)|✔️|✔️|✔️|

## <a name="policy-settings"></a>İlke ayarları

Her ilke türü, aşağıdaki tabloda listelenen değerlerden birine ayarlanabilir. Tür üyelerini temsil eden öğelerin, farklı bir ilke ayarları kümesini diğer öğelerden desteklediğini unutmayın.

|İlke ayarı|Açıklama|`Assembly`, `Namespace` , `Type` , ve `TypeInstantiation` öğeleri|`Event`, `Field` , `Method` , `MethodInstantiation` ve `Property` öğeleri|
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|
|`All`|.NET Native araç zincirinin kaldıramayan tüm türler ve Üyeler için ilkeyi izin vermez.|✔️||
|`Auto`|Bu program öğesinin ilke türü için varsayılan ilkenin kullanılması gerektiğini belirtir. Bu, ilke türü için bir ilkeyi dışarıda bırakarak benzerdir. `Auto`genellikle ilkenin bir üst öğeden devralındığını belirtmek için kullanılır.|✔️|✔️|
|`Excluded`|İlkenin belirli bir program öğesi için devre dışı bırakıldığını belirtir. Örneğin, çalışma zamanı yönergesi:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> sınıfa ait meta verilerin, `BusinessClasses.Person` nesneleri dinamik olarak oluşturmak veya değiştirmek için kullanılabilir olmadığını belirtir `Person` .|✔️|✔️|
|`Included`|Üst tür için meta veriler kullanılabiliyorsa bir ilkeyi etkinleştirilir.||✔️|
|`Public`|Araç zinciri türün veya üyenin gereksiz olduğunu belirtmediği ve bu nedenle onu kaldıran ortak türler veya Üyeler için ilkeyi etkinleştirilir. Bu ayar öğesinden farklıdır `Required Public` , bu, araç zinciri gereksiz olduğunu belirlerse bile ortak türler ve Üyeler için meta verilerin her zaman kullanılabilir olmasını sağlar.|✔️||
|`PublicAndInternal`|Araç zinciri tür veya üyenin gereksiz olduğunu belirlerse ve bu nedenle bunu kaldırmadığı takdirde, ortak ve iç türler veya Üyeler için ilkeyi etkinleştirilir. Bu ayar öğesinden farklıdır `Required PublicAndInternal` , bu, araç zinciri gereksiz olduğunu belirlerse bile ortak ve iç türlerin ve üyelerin meta verilerinin her zaman kullanılabilir olmasını sağlar.|✔️||
|`Required`|Üye için ilkenin etkinleştirildiğini ve üyenin kullanılması gibi görünse de meta verilerin kullanılabilir olacağını belirtir.||✔️|
|`Required Public`|Genel türler veya Üyeler için ilkeyi sağlar ve genel türler ve Üyeler için meta verilerin her zaman kullanılabilir olmasını sağlar. Bu ayar öğesinden farklıdır `Public` , bu, ortak türlerin ve üyelerin meta verilerini yalnızca araç zinciri gerekli olduğunu belirlerse kullanılabilir hale getirir.|✔️||
|`Required PublicAndInternal`|Ortak ve iç türler ya da Üyeler için ilkeyi sağlar ve ortak ve iç türlerin ve üyelerin meta verilerinin her zaman kullanılabilir olmasını sağlar. Bu ayar öğesinden farklıdır `PublicAndInternal` , bu, ortak ve iç türlerin ve üyelerin meta verilerini yalnızca araç zinciri gerekli olduğunu belirlerse kullanılabilir hale getirir.|✔️||
|`Required All`|, Kullanıldıkları ve kullanılmayacağı tüm türleri ve üyeleri tutmak için araç zinciri gerektirir ve bunlar için ilke sağlar.|✔️||

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
