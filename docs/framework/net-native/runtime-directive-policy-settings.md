---
title: Çalışma Zamanı Yönerge İlkesi Ayarları
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33253c249842824a529f4e8b24d4ca4228733041
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049211"
---
# <a name="runtime-directive-policy-settings"></a>Çalışma Zamanı Yönerge İlkesi Ayarları

> [!NOTE]
> Bu konu, yayın öncesi yazılım olan .NET Native geliştirici önizlemesine başvurur. Önizlemeyi [Microsoft Connect Web sitesinden](https://go.microsoft.com/fwlink/?LinkId=394611) indirebilirsiniz (kayıt gerekir).

.NET Native çalışma zamanı yönerge ilkesi ayarları, çalışma zamanında türler ve tür üyeleri için meta verilerin kullanılabilirliğini belirlemektir. Gerekli meta veriler olmadan, yansıma, serileştirme ve serisini kullanan işlemler veya .NET Framework türlerinin COM veya Windows Çalışma Zamanı sıralaması başarısız olabilir ve bir özel durum oluşturabilir. En yaygın özel durumlar [MissingMetadataException](missingmetadataexception-class-net-native.md) ve (birlikte çalışabilirlik durumunda) [MissingInteropDataException](missinginteropdataexception-class-net-native.md).

Çalışma zamanı ilke ayarları, bir çalışma zamanı yönergeleri (. RD. xml) dosyası tarafından denetlenir. Her çalışma zamanı yönergesi derleme ( [ \<derleme >](assembly-element-net-native.md) öğesi), [ \<](type-element-net-native.md) bir tür (tür > öğesi) veya bir Yöntem ( [ \<Yöntem >](method-element-net-native.md) gibi belirli bir program öğesi için ilkeyi tanımlar. öğesi). Yönergesi, yansıma ilkesi türlerini, serileştirme ilke türlerini ve sonraki bölümde ele alınan birlikte çalışma ilkesi türlerini tanımlayan bir veya daha fazla öznitelik içerir. Özniteliğin değeri, ilke ayarını tanımlar.

## <a name="policy-types"></a>İlke türleri

Çalışma zamanı yönergeleri dosyaları, ilke türlerinin üç kategorisini tanır: yansıma, serileştirme ve birlikte çalışma.

- Yansıma ilkesi türleri, yansıma için çalışma zamanında hangi meta verilerin kullanılabilir hale getirilceğini belirleme:

  - `Activate`örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.

  - `Browse`program öğeleri hakkında bilgi sorgulama denetimleri.

  - `Dynamic`Dinamik programlamayı etkinleştirmek için tüm türlere ve üyelere çalışma zamanı erişimini denetler.

  Aşağıdaki tabloda, yansıma ilkesi türleri ve bunların kullanılabileceği program öğeleri listelenmektedir.

  |Öğe|etkinleştir|Ata|Dinamik|
  |-------------|--------------|------------|-------------|
  |[\<Uygulama >](application-element-net-native.md)|✓|✓|✓|
  |[\<Bütünleştirilmiş kod >](assembly-element-net-native.md)|✓|✓|✓|
  |[\<Attribute>](attributeimplies-element-net-native.md)|✓|✓|✓|
  |[\<Olay >](event-element-net-native.md)||✓|✓|
  |[\<Alan >](field-element-net-native.md)||✓|✓|
  |[\<GenericParameter >](genericparameter-element-net-native.md)|✓|✓|✓|
  |[\<Impliestype >](impliestype-element-net-native.md)|✓|✓|✓|
  |[\<Yöntem >](method-element-net-native.md)||✓|✓|
  |[\<Methodörneklemesi >](methodinstantiation-element-net-native.md)||✓|✓|
  |[\<Ad alanı >](namespace-element-net-native.md)|✓|✓|✓|
  |[\<Parametre >](parameter-element-net-native.md)|✓|✓|✓|
  |[\<Özellik >](property-element-net-native.md)||✓|✓|
  |[\<Alt türler >](subtypes-element-net-native.md)|✓|✓|✓|
  |[\<Tür >](type-element-net-native.md)|✓|✓|✓|
  |[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|✓|✓|✓|
  |[\<TypeParameter >](typeparameter-element-net-native.md)|✓|✓|✓|

- Serileştirme ilke türleri serileştirme ve seri durumundan çıkarma için çalışma zamanında kullanılabilir hale getirilen meta verileri belirleme:

  - `Serialize`tür örneklerinin, Newtonsoft JSON seri hale getirici gibi üçüncü taraf kitaplıklar tarafından serileştirilmesi için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.

  - `DataContractSerializer`tür örneklerinin <xref:System.Runtime.Serialization.DataContractSerializer> sınıf tarafından serileştirilmesine olanak tanımak için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.

  - `DataContractJsonSerializer`tür örneklerinin <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sınıf tarafından serileştirilmesine olanak tanımak için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.

  - `XmlSerializer`tür örneklerinin <xref:System.Xml.Serialization.XmlSerializer> sınıf tarafından serileştirilmesine olanak tanımak için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.

  Aşağıdaki tabloda, serileştirme ilkesi türleri ve bunların kullanılabileceği program öğeleri listelenmektedir.

  |Öğe|Serialize|DataContractSerializer|DataContractJsonSerializer|Çağrılamıyor|
  |-------------|---------------|----------------------------|--------------------------------|-------------------|
  |[\<Uygulama >](application-element-net-native.md)|✓|✓|✓|✓|
  |[\<Bütünleştirilmiş kod >](assembly-element-net-native.md)|✓|✓|✓|✓|
  |[\<Attribute>](attributeimplies-element-net-native.md)|✓|✓|✓|✓|
  |[\<Olay >](event-element-net-native.md)|||||
  |[\<Alan >](field-element-net-native.md)|✓||||
  |[\<GenericParameter >](genericparameter-element-net-native.md)|✓|✓|✓|✓|
  |[\<Impliestype >](impliestype-element-net-native.md)|✓|✓|✓|✓|
  |[\<Yöntem >](method-element-net-native.md)|||||
  |[\<Methodörneklemesi >](methodinstantiation-element-net-native.md)|||||
  |[\<Ad alanı >](namespace-element-net-native.md)|✓|✓|✓|✓|
  |[\<Parametre >](parameter-element-net-native.md)|✓|✓|✓|✓|
  |[\<Özellik >](property-element-net-native.md)|✓||||
  |[\<Alt türler >](subtypes-element-net-native.md)|✓|✓|✓|✓|
  |[\<Tür >](type-element-net-native.md)|✓|✓|✓|✓|
  |[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|✓|✓|✓|✓|
  |[\<TypeParameter >](typeparameter-element-net-native.md)|✓|✓|✓|✓|

- Birlikte çalışma ilkesi türleri, başvuru türlerini, değer türlerini ve işlev işaretçilerini COM 'a ve Windows Çalışma Zamanı geçirmek için çalışma zamanında hangi meta verilerin kullanılabilir hale getirilceğini belirlenir:

  - `MarshalObject`COM 'a yerel hazırlamayı ve başvuru türleri için Windows Çalışma Zamanı denetler.

  - `MarshalDelegate`temsilci türlerinin işlev işaretçileri olarak yerel sıralamasını denetler.

  - `MarshalStructure`COM 'a yerel hazırlamayı ve değer türleri için Windows Çalışma Zamanı denetler.

  Aşağıdaki tabloda birlikte çalışma ilkesi türleri ve bunların kullanılabileceği program öğeleri listelenmektedir.

  |Öğe|MarshalObject|MarshalDelegate|MarshalStructure|
  |-------------|-------------------|---------------------|----------------------|
  |[\<Uygulama >](application-element-net-native.md)|✓|✓|✓|
  |[\<Bütünleştirilmiş kod >](assembly-element-net-native.md)|✓|✓|✓|
  |[\<Attribute>](attributeimplies-element-net-native.md)|✓|✓|✓|
  |[\<Olay >](event-element-net-native.md)||||
  |[\<Alan >](field-element-net-native.md)||||
  |[\<GenericParameter >](genericparameter-element-net-native.md)|✓|✓|✓|
  |[\<Impliestype >](impliestype-element-net-native.md)|✓|✓|✓|
  |[\<Yöntem >](method-element-net-native.md)||||
  |[\<Methodörneklemesi >](methodinstantiation-element-net-native.md)||||
  |[\<Ad alanı >](namespace-element-net-native.md)|✓|✓|✓|
  |[\<Parametre >](parameter-element-net-native.md)|✓|✓|✓|
  |[\<Özellik >](property-element-net-native.md)||||
  |[\<Alt türler >](subtypes-element-net-native.md)|✓|✓|✓|
  |[\<Tür >](type-element-net-native.md)|✓|✓|✓|
  |[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|✓|✓|✓|
  |[\<TypeParameter >](typeparameter-element-net-native.md)|✓|✓|✓|

## <a name="policy-settings"></a>İlke ayarları

Her ilke türü, aşağıdaki tabloda listelenen değerlerden birine ayarlanabilir. Tür üyelerini temsil eden öğelerin, farklı bir ilke ayarları kümesini diğer öğelerden desteklediğini unutmayın.

|İlke ayarı|Açıklama|`Assembly`, `Namespace`, `Type`, ve `TypeInstantiation` öğeleri|`Event`, `Field` ,`Method`, ve`Property` öğeleri `MethodInstantiation`|
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|
|`All`|.NET Native araç zincirinin kaldıramayan tüm türler ve Üyeler için ilkeyi izin vermez.|✓||
|`Auto`|Bu program öğesinin ilke türü için varsayılan ilkenin kullanılması gerektiğini belirtir. Bu, ilke türü için bir ilkeyi dışarıda bırakarak benzerdir. `Auto`genellikle ilkenin bir üst öğeden devralındığını belirtmek için kullanılır.|✓|✓|
|`Excluded`|İlkenin belirli bir program öğesi için devre dışı bırakıldığını belirtir. Örneğin, çalışma zamanı yönergesi:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> sınıfa ait meta verilerin, `BusinessClasses.Person` nesneleri dinamik olarak oluşturmak veya değiştirmek `Person` için kullanılabilir olmadığını belirtir.|✓|✓|
|`Included`|Üst tür için meta veriler kullanılabiliyorsa bir ilkeyi etkinleştirilir.||✓|
|`Public`|Araç zinciri türün veya üyenin gereksiz olduğunu belirtmediği ve bu nedenle onu kaldıran ortak türler veya Üyeler için ilkeyi etkinleştirilir. Bu ayar öğesinden `Required Public`farklıdır, bu, araç zinciri gereksiz olduğunu belirlerse bile ortak türler ve Üyeler için meta verilerin her zaman kullanılabilir olmasını sağlar.|✓||
|`PublicAndInternal`|Araç zinciri tür veya üyenin gereksiz olduğunu belirlerse ve bu nedenle bunu kaldırmadığı takdirde, ortak ve iç türler veya Üyeler için ilkeyi etkinleştirilir. Bu ayar öğesinden `Required PublicAndInternal`farklıdır, bu, araç zinciri gereksiz olduğunu belirlerse bile ortak ve iç türlerin ve üyelerin meta verilerinin her zaman kullanılabilir olmasını sağlar.|✓||
|`Required`|Üye için ilkenin etkinleştirildiğini ve üyenin kullanılması gibi görünse de meta verilerin kullanılabilir olacağını belirtir.||✓|
|`Required Public`|Genel türler veya Üyeler için ilkeyi sağlar ve genel türler ve Üyeler için meta verilerin her zaman kullanılabilir olmasını sağlar. Bu ayar öğesinden `Public`farklıdır, bu, ortak türlerin ve üyelerin meta verilerini yalnızca araç zinciri gerekli olduğunu belirlerse kullanılabilir hale getirir.|✓||
|`Required PublicAndInternal`|Ortak ve iç türler ya da Üyeler için ilkeyi sağlar ve ortak ve iç türlerin ve üyelerin meta verilerinin her zaman kullanılabilir olmasını sağlar. Bu ayar öğesinden `PublicAndInternal`farklıdır, bu, ortak ve iç türlerin ve üyelerin meta verilerini yalnızca araç zinciri gerekli olduğunu belirlerse kullanılabilir hale getirir.|✓||
|`Required All`|, Kullanıldıkları ve kullanılmayacağı tüm türleri ve üyeleri tutmak için araç zinciri gerektirir ve bunlar için ilke sağlar.|✓||

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
