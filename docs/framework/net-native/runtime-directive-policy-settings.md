---
title: Çalışma Zamanı Yönerge İlkesi Ayarları
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
ms.openlocfilehash: 7a8933decaec45e8000f3f3d1717847f333deddd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738496"
---
# <a name="runtime-directive-policy-settings"></a>Çalışma Zamanı Yönerge İlkesi Ayarları

> [!NOTE]
> Bu konu, yayın öncesi yazılım olan .NET Native geliştirici önizlemesine başvurur. Önizlemeyi [Microsoft Connect Web sitesinden](https://go.microsoft.com/fwlink/?LinkId=394611) indirebilirsiniz (kayıt gerekir).

.NET Native çalışma zamanı yönerge ilkesi ayarları, çalışma zamanında türler ve tür üyeleri için meta verilerin kullanılabilirliğini belirlemektir. Gerekli meta veriler olmadan, yansıma, serileştirme ve serisini kullanan işlemler veya .NET Framework türlerinin COM veya Windows Çalışma Zamanı sıralaması başarısız olabilir ve bir özel durum oluşturabilir. En yaygın özel durumlar [MissingMetadataException](missingmetadataexception-class-net-native.md) ve (birlikte çalışabilirlik durumunda) [MissingInteropDataException](missinginteropdataexception-class-net-native.md).

Çalışma zamanı ilke ayarları, bir çalışma zamanı yönergeleri (. RD. xml) dosyası tarafından denetlenir. Her çalışma zamanı yönergesi derleme ( [\<derlemesi >](assembly-element-net-native.md) öğesi), bir tür ( [\<türü >](type-element-net-native.md) öğesi) veya bir yöntemi ( [\<yöntemi](method-element-net-native.md) > öğesi) gibi belirli bir program öğesi için ilkeyi tanımlar. Yönergesi, yansıma ilkesi türlerini, serileştirme ilke türlerini ve sonraki bölümde ele alınan birlikte çalışma ilkesi türlerini tanımlayan bir veya daha fazla öznitelik içerir. Özniteliğin değeri, ilke ayarını tanımlar.

## <a name="policy-types"></a>İlke türleri

Çalışma zamanı yönergeleri dosyaları, ilke türlerinin üç kategorisini tanır: yansıma, serileştirme ve birlikte çalışma.

- Yansıma ilkesi türleri, yansıma için çalışma zamanında hangi meta verilerin kullanılabilir hale getirilceğini belirleme:

  - `Activate`, örneklerin etkinleştirilmesini sağlamak üzere oluşturuculara çalışma zamanına erişimi denetler.

  - program öğeleri hakkında bilgi sorgulama `Browse` denetimler.

  - `Dynamic`, dinamik programlamayı etkinleştirmek için tüm türlere ve üyelere çalışma zamanı erişimini denetler.

  Aşağıdaki tabloda, yansıma ilkesi türleri ve bunların kullanılabileceği program öğeleri listelenmektedir.

  |Öğe|Etkinleştir|Göz at|Dinamik|
  |-------------|--------------|------------|-------------|
  |[\<uygulama >](application-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[Derleme > \<](assembly-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<Attribute>](attributeimplies-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<olayı >](event-element-net-native.md)||✔ ︎|✔ ︎|
  |[\<alan >](field-element-net-native.md)||✔ ︎|✔ ︎|
  |[\<GenericParameter >](genericparameter-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<ımpliestype >](impliestype-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<yöntemi >](method-element-net-native.md)||✔ ︎|✔ ︎|
  |[\<Methodörneklemesi >](methodinstantiation-element-net-native.md)||✔ ︎|✔ ︎|
  |[\<ad alanı >](namespace-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<parametresi >](parameter-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<Özellik >](property-element-net-native.md)||✔ ︎|✔ ︎|
  |[\<alt türleri >](subtypes-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<türü >](type-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<TypeParameter >](typeparameter-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|

- Serileştirme ilke türleri serileştirme ve seri durumundan çıkarma için çalışma zamanında kullanılabilir hale getirilen meta verileri belirleme:

  - `Serialize`, tür örneklerinin Newtonsoft JSON serileştirici gibi üçüncü taraf kitaplıklar tarafından serileştirilmesi için çalışma zamanına, alanlara ve özelliklere yönelik çalışma zamanı erişimini denetler.

  - `DataContractSerializer`, tür örneklerinin <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı tarafından serileştirilmesi için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.

  - `DataContractJsonSerializer`, tür örneklerinin <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sınıfı tarafından serileştirilmesi için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.

  - `XmlSerializer`, tür örneklerinin <xref:System.Xml.Serialization.XmlSerializer> sınıfı tarafından serileştirilmesi için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.

  Aşağıdaki tabloda, serileştirme ilkesi türleri ve bunların kullanılabileceği program öğeleri listelenmektedir.

  |Öğe|Serialize|DataContractSerializer|DataContractJsonSerializer|Çağrılamıyor|
  |-------------|---------------|----------------------------|--------------------------------|-------------------|
  |[\<uygulama >](application-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|✔ ︎|
  |[Derleme > \<](assembly-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|✔ ︎|
  |[\<Attribute>](attributeimplies-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|✔ ︎|
  |[\<olayı >](event-element-net-native.md)|||||
  |[\<alan >](field-element-net-native.md)|✔ ︎||||
  |[\<GenericParameter >](genericparameter-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|✔ ︎|
  |[\<ımpliestype >](impliestype-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|✔ ︎|
  |[\<yöntemi >](method-element-net-native.md)|||||
  |[\<Methodörneklemesi >](methodinstantiation-element-net-native.md)|||||
  |[\<ad alanı >](namespace-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|✔ ︎|
  |[\<parametresi >](parameter-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|✔ ︎|
  |[\<Özellik >](property-element-net-native.md)|✔ ︎||||
  |[\<alt türleri >](subtypes-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|✔ ︎|
  |[\<türü >](type-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|✔ ︎|
  |[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|✔ ︎|
  |[\<TypeParameter >](typeparameter-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|✔ ︎|

- Birlikte çalışma ilkesi türleri, başvuru türlerini, değer türlerini ve işlev işaretçilerini COM 'a ve Windows Çalışma Zamanı geçirmek için çalışma zamanında hangi meta verilerin kullanılabilir hale getirilceğini belirlenir:

  - `MarshalObject`, COM 'a yerel hazırlamayı ve başvuru türleri için Windows Çalışma Zamanı denetler.

  - `MarshalDelegate`, temsilci türlerini işlev işaretçileri olarak yerel olarak hazırlamayı denetler.

  - `MarshalStructure`, COM 'a yerel hazırlamayı ve değer türleri için Windows Çalışma Zamanı denetler.

  Aşağıdaki tabloda birlikte çalışma ilkesi türleri ve bunların kullanılabileceği program öğeleri listelenmektedir.

  |Öğe|MarshalObject|MarshalDelegate|MarshalStructure|
  |-------------|-------------------|---------------------|----------------------|
  |[\<uygulama >](application-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[Derleme > \<](assembly-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<Attribute>](attributeimplies-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<olayı >](event-element-net-native.md)||||
  |[\<alan >](field-element-net-native.md)||||
  |[\<GenericParameter >](genericparameter-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<ımpliestype >](impliestype-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<yöntemi >](method-element-net-native.md)||||
  |[\<Methodörneklemesi >](methodinstantiation-element-net-native.md)||||
  |[\<ad alanı >](namespace-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<parametresi >](parameter-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<Özellik >](property-element-net-native.md)||||
  |[\<alt türleri >](subtypes-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<türü >](type-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|
  |[\<TypeParameter >](typeparameter-element-net-native.md)|✔ ︎|✔ ︎|✔ ︎|

## <a name="policy-settings"></a>İlke ayarları

Her ilke türü, aşağıdaki tabloda listelenen değerlerden birine ayarlanabilir. Tür üyelerini temsil eden öğelerin, farklı bir ilke ayarları kümesini diğer öğelerden desteklediğini unutmayın.

|İlke ayarı|Açıklama|`Assembly`, `Namespace`, `Type`ve `TypeInstantiation` öğeleri|`Event`, `Field`, `Method`, `MethodInstantiation`ve `Property` öğeleri|
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|
|`All`|.NET Native araç zincirinin kaldıramayan tüm türler ve Üyeler için ilkeyi izin vermez.|✔ ︎||
|`Auto`|Bu program öğesinin ilke türü için varsayılan ilkenin kullanılması gerektiğini belirtir. Bu, ilke türü için bir ilkeyi dışarıda bırakarak benzerdir. `Auto`, genellikle ilkenin üst öğeden devralındığını göstermek için kullanılır.|✔ ︎|✔ ︎|
|`Excluded`|İlkenin belirli bir program öğesi için devre dışı bırakıldığını belirtir. Örneğin, çalışma zamanı yönergesi:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> `BusinessClasses.Person` sınıfı için meta verilerin, `Person` nesneleri dinamik olarak örneği oluşturmak veya değiştirmek için kullanılabilir olmadığını belirtir.|✔ ︎|✔ ︎|
|`Included`|Üst tür için meta veriler kullanılabiliyorsa bir ilkeyi etkinleştirilir.||✔ ︎|
|`Public`|Araç zinciri türün veya üyenin gereksiz olduğunu belirtmediği ve bu nedenle onu kaldıran ortak türler veya Üyeler için ilkeyi etkinleştirilir. Bu ayar `Required Public`farklıdır. Bu, araç zinciri gereksiz olduğunu belirlerse bile ortak türler ve Üyeler için meta verilerin her zaman kullanılabilir olmasını sağlar.|✔ ︎||
|`PublicAndInternal`|Araç zinciri tür veya üyenin gereksiz olduğunu belirlerse ve bu nedenle bunu kaldırmadığı takdirde, ortak ve iç türler veya Üyeler için ilkeyi etkinleştirilir. Bu ayar `Required PublicAndInternal`farklıdır. Bu, araç zinciri gereksiz olduğunu belirlerse bile ortak ve iç türlerin ve üyelerin meta verilerinin her zaman kullanılabilir olmasını sağlar.|✔ ︎||
|`Required`|Üye için ilkenin etkinleştirildiğini ve üyenin kullanılması gibi görünse de meta verilerin kullanılabilir olacağını belirtir.||✔ ︎|
|`Required Public`|Genel türler veya Üyeler için ilkeyi sağlar ve genel türler ve Üyeler için meta verilerin her zaman kullanılabilir olmasını sağlar. Bu ayar `Public`farklıdır, bu, ortak türlerin ve üyelerin meta verilerini yalnızca araç zinciri gerekli olduğunu belirlerse kullanılabilir hale getirir.|✔ ︎||
|`Required PublicAndInternal`|Ortak ve iç türler ya da Üyeler için ilkeyi sağlar ve ortak ve iç türlerin ve üyelerin meta verilerinin her zaman kullanılabilir olmasını sağlar. Bu ayar `PublicAndInternal`farklıdır, bu, ortak ve iç tür ve üyelerin meta verilerini yalnızca araç zinciri gerekli olduğunu belirlerse kullanılabilir hale getirir.|✔ ︎||
|`Required All`|, Kullanıldıkları ve kullanılmayacağı tüm türleri ve üyeleri tutmak için araç zinciri gerektirir ve bunlar için ilke sağlar.|✔ ︎||

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
