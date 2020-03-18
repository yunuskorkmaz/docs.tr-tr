---
title: Öznitelikler (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 2a07035ea97bb0ff1a8f4793fe8a30d3a42c34a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399751"
---
# <a name="attributes-c"></a>Öznitelikler (C#)

Öznitelikler, meta verileri veya bildirimsel bilgileri kodla (derlemeler, türler, yöntemler, özellikler vb.) ilişkilendirme güçlü bir yöntem sağlar. Bir öznitelik bir program varlığı ile ilişkilendirildikten sonra, öznitelik *yansıma*adı verilen bir teknik kullanılarak çalışma zamanında sorgulanabilir. Daha fazla bilgi için [Yansıma (C#)](../reflection.md)'ye bakın.

Özniteliklerin aşağıdaki özellikleri vardır:

- Öznitelikler programınıza meta veri ekler. *Meta veriler,* bir programda tanımlanan türler hakkında bilgidir. Tüm .NET derlemeleri, derlemede tanımlanan tür ve tür üyelerini açıklayan belirli bir meta veri kümesi içerir. Gerekli olan ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz. Daha fazla bilgi için bkz: [Özel Öznitelikler oluşturma (C#)](creating-custom-attributes.md).
- Sınıflar ve özellikler gibi tüm derlemelere, modüllere veya daha küçük program öğelerine bir veya daha fazla öznitelik uygulayabilirsiniz.
- Öznitelikler, bağımsız değişkenleri yöntem ve özelliklerle aynı şekilde kabul edebilir.
- Programınız yansımayı kullanarak kendi meta verilerini veya diğer programlardaki meta verileri inceleyebilir. Daha fazla bilgi için bkz: [Yansıma (C#) kullanarak Özniteliklere Erişim.](accessing-attributes-by-using-reflection.md)

## <a name="using-attributes"></a>Öznitelikleri kullanma

Öznitelikler çoğu bildirime yerleştirilebilir, ancak belirli bir öznitelik geçerli olduğu bildirim türlerini kısıtlayabilir. C#'da, öznitelik adını kare ayraçlarla ([]) uygulandığı varlığın bildiriminin üzerine koyarak bir öznitelik belirtirsiniz.

Bu örnekte, <xref:System.SerializableAttribute> öznitelik bir sınıfa belirli bir özellik uygulamak için kullanılır:

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Öznitelik <xref:System.Runtime.InteropServices.DllImportAttribute> içeren bir yöntem aşağıdaki örnek gibi bildirilir:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Aşağıdaki örnekte görüldüğü gibi bir bildirime birden fazla öznitelik yerleştirilebilir:

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir. Böyle bir çok kullanımlı öznitelik bir <xref:System.Diagnostics.ConditionalAttribute>örnek:

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Kural kuralına göre, tüm öznitelik adları .NET kitaplıklarındaki diğer öğelerden ayırt etmek için "Öznitelik" sözcüğüyle sona erer. Ancak, kodözleri kullanırken öznitelik soneki belirtmeniz gerekmez. Örneğin, `[DllImport]` `[DllImportAttribute]`.NET `DllImportAttribute` Framework Class Kitaplığı'ndaki özniteliğin gerçek adıdır.

### <a name="attribute-parameters"></a>Öznitelik parametreleri

Birçok öznitelik, konumsal, adsız veya adlandırılmış parametrelere sahiptir. Herhangi bir konumsal parametreler belirli bir sırada belirtilmelidir ve atlanamaz. Adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir. Önce pozisyonparametreleri belirtilir. Örneğin, bu üç öznitelik eşdeğerdir:

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

İlk parametre, DLL adı, konumsal ve her zaman önce gelir; diğerleri ne adlandırılmış. Bu durumda, her iki adlandırılmış parametre varsayılan false, bu yüzden atlanabilir. Konumsal parametreler öznitelik oluşturucu parametrelerine karşılık gelir. Adlandırılmış veya isteğe bağlı parametreler özniteliğin özelliklerine veya alanlarına karşılık gelir. Varsayılan parametre değerleri hakkında bilgi almak için tek tek özniteliğin belgelerine bakın.

### <a name="attribute-targets"></a>Öznitelik hedefleri

Bir özniteliğin *hedefi,* özniteliğin uygulandığı varlıktır. Örneğin, bir öznitelik bir sınıf, belirli bir yöntem veya tüm derleme için geçerli olabilir. Varsayılan olarak, onu izleyen öğeye bir öznitelik uygulanır. Ancak, örneğin bir öznitelik bir yönteme mi, parametresine mi yoksa geri dönüş değerine mi uygulandığını açıkça belirleyebilirsiniz.

Bir öznitelik hedefini açıkça tanımlamak için aşağıdaki sözdizimini kullanın:

```csharp
[target : attribute-list]
```

Olası `target` değerlerin listesi aşağıdaki tabloda gösterilmiştir.

|Hedef değer|Uygulandığı öğe:|
|------------------|----------------|
|`assembly`|Tüm montaj|
|`module`|Geçerli montaj modülü|
|`field`|Bir sınıftaki veya yapıdaki alan|
|`event`|Olay|
|`method`|Yöntem `get` veya `set` özellik erişime erişim|
|`param`|Yöntem parametreleri veya `set` özellik aksesuar parametreleri|
|`property`|Özellik|
|`return`|Yöntemin, özellik dizinicisinin `get` veya özellik erişime erişiminin iade değeri|
|`type`|Yapı, sınıf, arayüz, enum veya temsilci|

Otomatik olarak `field` uygulanan bir özellik için oluşturulan destek alanına bir öznitelik uygulamak için hedef değeri [belirtirsiniz.](../../../properties.md)

Aşağıdaki örnek, öznitelikleri derlemelere ve modüllere nasıl uygulayacağımızı gösterir. Daha fazla bilgi için [Ortak Öznitelikler (C#)](common-attributes.md)'ye bakın.

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

Aşağıdaki örnek, C#'daki yöntemlere, yöntem parametrelerine ve yöntem döndürme değerlerine öznitelikleri nasıl uygulanacağı gösterilmektedir.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Geçerli olarak tanımlanan hedeflere `ValidatedContract` bakılmaksızın, yalnızca `return` döndürme değerleri için uygulanacak `ValidatedContract` şekilde tanımlanmış olsa bile hedefin belirtilmesi gerekir. Başka bir deyişle, derleyici `AttributeUsage` belirsiz öznitelik hedeflerini çözmek için bilgileri kullanmaz. Daha fazla bilgi için [Bkz. AttributeUsage (C#)](attributeusage.md).

## <a name="common-uses-for-attributes"></a>Öznitelikler için ortak kullanımlar

Aşağıdaki liste, koddaki özniteliklerin ortak kullanımlarından birkaçını içerir:

- Yöntemin SOAP `WebMethod` protokolü üzerinden çağrılabilir olması gerektiğini belirtmek için Web hizmetlerinde özniteliği kullanarak işaretleme yöntemleri. Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.
- Yerel kodla birlikte çalışırken yöntem parametrelerinin nasıl sıralanır olduğunu açıklar. Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.
- Sınıflar, yöntemler ve arabirimler için COM özelliklerini açıklayan.
- <xref:System.Runtime.InteropServices.DllImportAttribute> Sınıfı kullanarak yönetilmeyen kodu çağırma.
- Derlemenizi başlık, sürüm, açıklama veya ticari marka açısından açıklama.
- Bir sınıfın hangi üyelerinin kalıcılık için seri hale getirmek için açıklanması.
- XML serileştirme için sınıf üyeleri ve XML düğümleri arasında nasıl eşleneceklerini açıklar.
- Yöntemler için güvenlik gereksinimlerini açıklayan.
- Güvenliği zorlamak için kullanılan özellikleri belirtme.
- Kodun hata ayıklanması kolay kalması için optimizasyonları tam zamanında (JIT) derleyicitarafından denetler.
- Bir yönteme arayan hakkında bilgi edinme.

## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için bkz.

- [Özel Öznitelikler oluşturma (C#)](creating-custom-attributes.md)  
- [Yansıma (C#) kullanarak Özniteliklere Erişim](accessing-attributes-by-using-reflection.md)  
- [Öznitelikleri kullanarak C/C++ birleşimoluşturma (C#)](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Ortak Öznitelikler (C#)](common-attributes.md)  
- [Arayan Bilgileri (C#)](../caller-information.md)  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../index.md)
- [Yansıma (C#)](../reflection.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [C'de Öznitelikleri Kullanma #](../../../tutorials/attributes.md)
