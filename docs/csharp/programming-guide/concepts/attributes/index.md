---
title: 'Öznitelikler (C#)'
ms.date: 04/26/2018
---
# <a name="attributes-c"></a>Öznitelikler (C#)

Öznitelikler (derlemeler, türler, yöntemler, özellikler ve benzeri) koduyla ilişkili bir meta veriler ya da tanımlayıcı bilgileri, güçlü bir yöntem sağlar. Öznitelik, bir program varlıkla ilişkilendirilen sonra öznitelik çalışma zamanında olarak adlandırılan tekniği kullanarak sorgulanabilir *yansıma*. Daha fazla bilgi için [yansıma (C#)](../reflection.md).

Öznitelik, aşağıdaki özelliklere sahiptir:

- Öznitelik meta verileri programınıza ekleyin. *Meta veri* bir programda tanımlanan türleri hakkındaki bilgilerdir. Tüm .NET derlemeleri derlemede tanımlanan tür üyeleri ve türleri açıklayan meta veriler belirtilen bir kümesini içerir. Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz. Daha fazla bilgi için bkz: [özel öznitelikler oluşturma (C#)](creating-custom-attributes.md).
- Tüm derlemeler, modüller veya daha küçük program öğelerini sınıfları ve özellikleri gibi bir veya daha fazla öznitelikleri uygulayabilirsiniz.
- Öznitelikleri yöntemleri ve özellikleri aynı şekilde bağımsız değişkenleri kabul edebilir.
- Programınızı kendi meta veriler ya da diğer programları meta verilerde yansıma kullanarak inceleyebilirsiniz. Daha fazla bilgi için [yansıma (C#) kullanarak erişen özniteliklerle](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Öznitelikleri kullanma

Belirli bir öznitelik bildirimleri, geçerli olduğu türlerini kısıtlamak ancak öznitelikleri pek çok bildiriminde yerleştirilebilir. İçinde C#, bir öznitelik adı köşeli ayraç ([]) içine özniteliği yerleştirerek, geçerli varlık bildiriminin üstüne belirttiğiniz.

Bu örnekte, <xref:System.SerializableAttribute> özniteliği, belirli bir özellik için bir sınıf uygulamak için kullanılır:

[!code-csharp[Using the serializable attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

Özniteliğine sahip metot <xref:System.Runtime.InteropServices.DllImportAttribute> aşağıdaki gibi bildirilir:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Birden fazla özniteliği aşağıdaki örnekte gösterildiği gibi bildiriminde yerleştirilebilir:

[!code-csharp[Including the interop namespace](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Bazı öznitelikleri kereden fazla belirli bir varlık için belirtilebilir. Multiuse bir öznitelik örneğidir <xref:System.Diagnostics.ConditionalAttribute>:

[!code-csharp[Using the conditional attribute](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Kural gereği, tüm öznitelik adları .NET kitaplıklarına diğer öğelerden bunları ayırt etmek için "özniteliği" sözcüğü ile biter. Ancak, öznitelikler kodda kullanıldığında özniteliği soneki belirtmek gerekmez. Örneğin, `[DllImport]` eşdeğerdir `[DllImportAttribute]`, ancak `DllImportAttribute` .NET Framework Sınıf Kitaplığı'nda özniteliğin gerçek adıdır.

### <a name="attribute-parameters"></a>Öznitelik parametreleri

Konumsal, adlandırılmamış veya adlandırılmış parametreleri fazla öznitelik var. Konumsal parametreleri, belirli bir sırayla belirtilmelidir ve atlanamaz. Adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir. Konumsal parametreler ilk belirtilir. Örneğin, bu üç özniteliğin eşdeğerdir:

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

İlk parametre, DLL adı konumsal ve her zaman ilk gelir; diğerleri olarak adlandırılır. Bu durumda, döngülerinden çıkarılabilir şekilde her ikisi de false olarak parametreleri varsayılan adı. Konumsal parametreler öznitelik oluşturucunun parametrelere karşılık gelir. Adlandırılmış ya da isteğe bağlı parametre için özellikler veya alanları özniteliğinin karşılık gelir. Varsayılan parametre değerleri hakkında bilgi için tek bir özniteliğin belgelerine bakın.

### <a name="attribute-targets"></a>Öznitelik hedefleri

*Hedef* özniteliği öznitelik uygulandığı varlıktır. Örneğin, bir öznitelik, bir sınıf, belirli bir yöntemi veya tüm derleme geçerli olabilir. Varsayılan olarak, kendisinden öğe için bir özniteliğini uygular. Ancak, bir yöntem veya, parametre veya dönüş değeri bir öznitelik uygulanmış olup olmadığını açıkça, örneğin, belirleyebilirsiniz.

Bir öznitelik hedefi açıkça tanımlamak için aşağıdaki sözdizimini kullanın:

```csharp
[target : attribute-list]
```

Olası listesini `target` değerleri aşağıdaki tabloda gösterilmiştir.

|Hedef değer|Uygulandığı öğe:|
|------------------|----------------|
|`assembly`|Tüm derleme|
|`module`|Geçerli derleme Modülü|
|`field`|Bir sınıf veya yapı alanı|
|`event`|Olay|
|`method`|Yöntem veya `get` ve `set` özellik erişimcileri|
|`param`|Yöntem parametreleri veya `set` özelliği erişimcisi parametreleri|
|`property`|Özellik|
|`return`|Bir yöntem, özellik dizinleyicisi, değeri döndürür veya `get` özellik erişimcisi|
|`type`|Yapı, sınıf, arabirim, enum veya temsilci|

Belirtirsiniz `field` destek alanı için bir öznitelik uygulamak için hedef değer için oluşturulan bir [otomatik uygulanan özellik](../../../properties.md).

Aşağıdaki örnek, derlemeler ve modüller için öznitelik uygulayın gösterilmektedir. Daha fazla bilgi için [ortak öznitelikler (C#)](common-attributes.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

Aşağıdaki örnekte, yöntem, yöntem parametreleri, öznitelikleri uygulamak gösterilmiştir ve yöntem dönüş değerleri C# dilinde.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> Hedeflerde bakılmaksızın `ValidatedContract` geçerli olması için tanımlanan `return` hedef sahip belirtilmesi bile `ValidatedContract` yalnızca dönüş değerleri uygulamak için tanımlanmadı. Diğer bir deyişle, derleyici kullanmaz `AttributeUsage` bilgileri belirsiz öznitelik hedefleri çözümlemek için. Daha fazla bilgi için [AttributeUsage (C#)](attributeusage.md).

## <a name="common-uses-for-attributes"></a>Öznitelikler için yaygın kullanımları

Aşağıdaki liste, kod öznitelikleri'nın yaygın kullanımları birkaçını içerir:

- Yöntemlerini kullanarak işaretleme `WebMethod` Web Hizmetleri yöntemi SOAP protokolü üzerinden çağrılabilmelidir belirtmek için özniteliği. Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.
- Yerel kod ile birlikte çalışırken yöntem parametreleri'ı sıralama nasıl açıklayan. Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.
- Sınıfları, yöntemleri ve arabirimleri için COM özelliklerini açıklayan.
- Yönetilmeyen çağırma kod kullanarak <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfı.
- Başlık, sürüm, açıklama veya ticari marka açısından derlemenizi açıklayan.
- Kalıcılık için seri hale getirmek için bir sınıfın hangi üyelerinin açıklayan.
- Sınıf üyeleri için XML serileştirme XML düğümler arasındaki eşlemeyle ilgili bilgi açıklayan.
- Güvenlik gereksinimleri yöntemleri için açıklama.
- Güvenliği zorlamak için kullanılan özellikleri belirleme.
- Kod hatalarını ayıklamak kolay kalır. böylece en iyi duruma getirme just-in-time (JIT) derleyici tarafından denetleniyor.
- Bir yöntemin arayanı hakkında bilgi edinme.

## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için bkz.:

- [Özel öznitelikler (C#) oluşturma](creating-custom-attributes.md)  
- [Yansıma (C#) kullanarak özniteliklere erişme](accessing-attributes-by-using-reflection.md)  
- [Nasıl yapılır: Öznitelikleri kullanarak C/C++ birleşimi oluşturma (C#)](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Ortak öznitelikler (C#)](common-attributes.md)  
- [Arayan bilgileri (C#)](../caller-information.md)  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../index.md)
- [Yansıma (C#)](../reflection.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Öznitelikleri kullanarak C#](../../../tutorials/attributes.md)
