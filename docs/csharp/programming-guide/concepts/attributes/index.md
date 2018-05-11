---
title: Öznitelikler (C#)
ms.date: 04/26/2018
ms.openlocfilehash: fe94f0ee778f14581fd7949f705cc22f12058b27
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="attributes-c"></a>Öznitelikler (C#)

Öznitelikler meta verileri veya tanımlayıcı bilgileri (derleme, türleri, yöntemler, özellikler ve benzeri) kodu ile ilişkilendirme için güçlü bir yöntem sağlar. Öznitelik bir program varlıkla ilişkilendirilen sonra öznitelik çalışma zamanında adlı bir yöntemi kullanarak sorgulanabilir *yansıma*. Daha fazla bilgi için bkz: [yansıma (C#)](../reflection.md).

Öznitelikler, aşağıdaki özelliklere sahiptir:

- Öznitelikleri programınıza meta veri ekleyin. *Meta veri* bir programda tanımlanan türleri hakkındaki bilgilerdir. Tüm .NET derlemelerini belirlenen türleri ve derlemede tanımlanan tür üyeleri açıklayan meta veriler içeriyor. Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz. Daha fazla bilgi için bkz: [özel öznitelikler oluşturma (C#)](creating-custom-attributes.md).
- Tüm derlemeler, modüller veya daha küçük program öğeleri sınıfları ve özellikleri gibi bir veya daha fazla öznitelik uygulayabilirsiniz.
- Öznitelikler, yöntemleri ve özellikleri aynı şekilde bağımsız değişkenleri kabul edebilir.
- Programınızı kendi meta verileri veya diğer programları meta yansıma kullanarak inceleyebilirsiniz. Daha fazla bilgi için bkz: [yansıma (C#) kullanarak erişme özniteliklerle](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Öznitelikleri kullanma

Belirli bir özniteliği, geçerli olduğu bildirimleri türlerini kısıtlayacak ancak öznitelikleri pek çok bildiriminde, yerleştirilebilir. C# ' ta, bir öznitelik geçerli olduğu varlık bildiriminin üstüne köşeli parantez ([]) içine özniteliğinin adı girerek belirtin.

Bu örnekte, <xref:System.SerializableAttribute> özniteliği bir sınıf için belirli bir karakteristik uygulamak için kullanılır:

[!code-csharp[Using the serializable attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Öznitelik bir yöntemle <xref:System.Runtime.InteropServices.DllImportAttribute> aşağıdaki gibi bildirilmiş:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Birden fazla özniteliği aşağıdaki örnekte gösterildiği gibi bir bildirimde yerleştirilebilir:

[!code-csharp[Including the interop namespace](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir. Multiuse bir öznitelik örneğidir <xref:System.Diagnostics.ConditionalAttribute>:

[!code-csharp[Using the conditional attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Kurala göre bunları .NET kitaplıklarına diğer öğeler ayırmak için "özniteliği" word tüm öznitelik adları bitemez. Ancak, öznitelikler kodda kullanırken özniteliği soneki belirtmek gerekmez. Örneğin, `[DllImport]` eşdeğerdir `[DllImportAttribute]`, ancak `DllImportAttribute` .NET Framework Sınıf Kitaplığı'nda özniteliğin gerçek adıdır.

### <a name="attribute-parameters"></a>Öznitelik parametreleri

Konumsal, adlandırılmamış veya adlandırılmış parametreleri birçok özniteliklere sahiptir. Konumsal parametreleri belirli bir sırada belirtilmeli ve atlanmış olamaz. Adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir. Konumsal parametreler ilk belirtildi. Örneğin, bu üç özniteliğin eşdeğerdir:

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

İlk parametre, DLL adı konumsal ve her zaman ilk gelir; diğer olarak adlandırılır. Bu durumda, kullanıcılar atlanabilir şekilde her ikisi de false, parametreleri varsayılan adı. Konumsal parametreler öznitelik oluşturucunun parametrelerinin karşılık gelir. Adlandırılmış ya da isteğe bağlı parametre özellikleri veya öznitelik alanları için karşılık gelir. Varsayılan parametre değerleri hakkında bilgi için tek tek özniteliğin belgelerine bakın.

### <a name="attribute-targets"></a>Öznitelik hedefleri

*Hedef* bir öznitelik geçerli olduğu varlık özniteliğidir. Örneğin, bir öznitelik, bir sınıf, belirli bir yöntemi veya tüm derleme için geçerli olabilir. Varsayılan olarak, bir öznitelik yakalanması öğesine uygulanır. Ancak bir öznitelik bir yöntem veya onun parametresi veya dönüş değeri uygulanıp uygulanmayacağını, aynı zamanda açıkça, örneğin, tanımlayabilirsiniz.

Açıkça bir öznitelik hedefini belirlemek için aşağıdaki sözdizimini kullanın:

```csharp
[target : attribute-list]
```

Olası listesi `target` değerleri aşağıdaki tabloda gösterilmiştir.

|Hedef değer|Uygulandığı öğe:|
|------------------|----------------|
|`assembly`|Tüm derleme|
|`module`|Geçerli derleme Modülü|
|`field`|Bir sınıf veya yapı alanında|
|`event`|Olay|
|`method`|Yöntem veya `get` ve `set` özellik erişimcisi|
|`param`|Yöntem parametreleri veya `set` özellik erişimcisi parametreleri|
|`property`|Özellik|
|`return`|Yöntemi, özelliği dizin oluşturucu, değeri döndürür veya `get` özelliği erişimcisi|
|`type`|Yapısı, sınıf, arabirim, numaralandırma veya temsilci|

Belirtirsiniz `field` bir öznitelik için yedekleme alanı uygulamak için hedef değer oluşturulan bir [otomatik uygulanan özelliği](../../../properties.md).

Aşağıdaki örnek, derlemeler ve modüller öznitelikleri uygulanacak gösterilmiştir. Daha fazla bilgi için bkz: [ortak öznitelikler (C#)](common-attributes.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

Aşağıdaki örnekte, yöntem, yöntem parametreleri, öznitelikleri uygulamak gösterilmiştir ve yöntemi dönüş değerleri C# '.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Hedefler, bağımsız olarak `ValidatedContract` geçerli olması için tanımlanan `return` hedef sahip belirtilmesi bile `ValidatedContract` yalnızca dönüş değerleri uygulamak için tanımlanmış. Diğer bir deyişle, derleyici kullanmaz `AttributeUsage` bilgileri belirsiz öznitelik hedefleri çözümlemek için. Daha fazla bilgi için bkz: [AttributeUsage (C#)](attributeusage.md).

## <a name="common-uses-for-attributes"></a>Öznitelikler için ortak kullanımlar

Aşağıdaki öznitelikler'ın yaygın kullanımları bazılarını kod içerir:

- Yöntemlerini kullanarak işaretleme `WebMethod` yöntemi SOAP protokolü üzerinden aranabilir olması gerektiğini belirtmek için Web Hizmetleri içinde öznitelik. Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.
- Yerel kod ile birlikte çalışırken yöntem parametreleri sıralamakta nasıl açıklayan. Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.
- Sınıfları, yöntemleri ve arabirimleri COM özelliklerini açıklayan.
- Yönetilmeyen çağırma kullanarak kod <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfı.
- Başlık, sürüm, açıklama veya ticari marka bakımından derlemenizi açıklayan.
- Kalıcılığını serileştirmek için bir sınıf hangi üyelerinin açıklayan.
- Sınıf üyeleri ve XML serileştirme için XML düğümler arasında eşleme açıklayan.
- Yöntemleri için güvenlik gereksinimleri açıklanır.
- Güvenlik uygulamak için kullanılan özellikleri belirleme.
- Böylece kodu hata ayıklamak kolay tam zamanında (JIT) derleyici tarafından iyileştirmeleri denetleme.
- Arayan bir yöntemi hakkında bilgi edinme.

## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için bkz.:

- [Özel öznitelikler (C#) oluşturma](creating-custom-attributes.md)  
- [Yansıma (C#) kullanarak özniteliklere erişme](accessing-attributes-by-using-reflection.md)  
- [Nasıl yapılır: öznitelikleri (C#) kullanarak C/C++ birleşimi oluşturma](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Ortak öznitelikler (C#)](common-attributes.md)  
- [Arayan bilgileri (C#)](../caller-information.md)  

## <a name="see-also"></a>Ayrıca bkz.

 [C# Programlama Kılavuzu](../../index.md)  
 [Yansıma (C#)](../reflection.md)  
 [Öznitelikler](../../../../standard/attributes/index.md)  
 [Öznitelikleri C# ile kullanma](../../../tutorials/attributes.md)  
