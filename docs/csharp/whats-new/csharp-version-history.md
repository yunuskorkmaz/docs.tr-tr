---
title: C# ' nin geçmişi-c# Kılavuzu
description: Dil en eski sürümlerinde ne şekilde görünür ve bu tarihten sonra nasıl gelişmiştir?
author: erikdietrich
ms.date: 04/08/2020
ms.openlocfilehash: 349f2cfbe0fc93060eb6927ee8c3528c16b99aca
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805095"
---
# <a name="the-history-of-c"></a>C geçmişi\#

Bu makalede, C# dilinin her ana sürümünün geçmişi sağlanmaktadır. C# ekibi yenilik yapın 'e devam ediyor ve yeni özellikler ekleyecek. Gelecek sürümler için kabul edilen özellikler dahil olmak üzere ayrıntılı dil özelliği durumu GitHub 'daki [DotNet/Roslyn deposunda](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) bulunabilir.

> [!IMPORTANT]
> C# dili, C# belirtiminin bazı özelliklerden *Standart bir kitaplık* olarak tanımladığı tür ve yöntemlere dayanır. .NET platformu bu türleri ve yöntemleri bir dizi pakete sunar. Özel durum işleme bir örnektir. `throw`Oluşturulan nesnenin türetildiğinden emin olmak için her deyim veya ifade denetlenir <xref:System.Exception> . Benzer şekilde, `catch` yakalanan türün türediğinden emin olmak için her ikisi de denetlenir <xref:System.Exception> . Her sürümde yeni gereksinimler eklenebilir. Eski ortamlarda en son dil özelliklerini kullanmak için, belirli kitaplıkları yüklemeniz gerekebilir. Bu bağımlılıklar, her belirli sürüm için sayfasında belgelenmiştir. Bu bağımlılıkta arka plan için [dil ve kitaplık arasındaki ilişkiler](relationships-between-language-and-library.md) hakkında daha fazla bilgi edinebilirsiniz.

C# derleme araçları, varsayılan dil sürümü olan en son ana dil sürümünü göz önünde bulundurun. Bu bölümdeki diğer makalelerde ayrıntılı olarak açıklanan ana yayınlar arasında nokta yayınları olabilir. En son özellikleri bir nokta sürümünde kullanmak için, [Derleyici dil sürümünü yapılandırmanız](../language-reference/configure-language-version.md) ve sürümü seçmeniz gerekir. C# 7,0 sonrasında üç noktalı yayınlar vardır:

- C# 7,3:
  - C# 7,3, [Visual Studio 2017 sürüm 15,7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ve [.NET Core 2,1 SDK](../../core/whats-new/dotnet-core-2-1.md)ile başlayarak kullanılabilir.
- C# 7,2:
  - C# 7,2, [Visual Studio 2017 sürüm 15,5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ve [.NET Core 2,0 SDK](../../core/whats-new/dotnet-core-2-0.md)ile başlayarak kullanılabilir.
- C# 7,1:
  - C# 7,1, [Visual Studio 2017 sürüm 15,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ve [.NET Core 2,0 SDK](../../core/whats-new/dotnet-core-2-0.md)ile başlayarak kullanılabilir.

## <a name="c-version-10"></a>C# sürüm 1,0

Geri dönerek Visual Studio .NET 2002 ile yayınlanan C# sürüm 1,0, Java gibi çok sayıda görünür. [ECMA için belirtilen tasarım hedeflerinin bir parçası](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)olarak, "basit, modern, genel amaçlı nesne yönelimli bir dil" olarak arar.  Bu sırada, Java gibi, bu erken tasarım hedefleri elde ettiği anlamına gelir.

Ancak C# 1,0 ' de şimdi geri bakarsanız, kendinizi biraz daha bulabilirsiniz. Yerleşik zaman uyumsuz özellikleri ve izin verilen genel türler etrafında bulunan bazı nesnelerin bazı nesnelerin bazı özelliklerini ele alır. Aslında, genel türleri tamamen ele edindi.  Ve [LINQ](../linq/index.md)? Henüz kullanılamıyor. Bu eklemelerin gelmesi birkaç yıl sürer.

C# sürüm 1,0, bugün ile karşılaştırıldığında özelliklerden çıkarılır. Kendinize bazı ayrıntılı kodlar yazmaktır. Ancak yine de bir yere başlamanız gerekir. C# sürüm 1,0, Windows platformunda Java için önemli bir alternatiftir.

C# 1,0 'nin başlıca özellikleri dahildir:

- [Sınıflar](../programming-guide/classes-and-structs/classes.md)
- [Yapılar](../language-reference/builtin-types/struct.md)
- [Arabirimler](../programming-guide/interfaces/index.md)
- [Olayları](../events-overview.md)
- [Özellikler](../properties.md)
- [Temsilciler](../delegates-overview.md)
- [İşleçler ve ifadeler](../language-reference/operators/index.md)
- [Deyimler](../programming-guide/statements-expressions-operators/statements.md)
- [Öznitelikler](../programming-guide/concepts/attributes/index.md)

## <a name="c-version-12"></a>C# sürüm 1,2

C# sürüm 1,2, Visual Studio .NET 2003 ile birlikte gönderilir. Dilde birkaç küçük geliştirmeler vardı. Çoğu önemli, bu sürümden başlayarak, `foreach` uygulandığında bir döngüsünde oluşturulan bir döngüde oluşturulan kod <xref:System.IDisposable.Dispose%2A> <xref:System.Collections.IEnumerator> <xref:System.Collections.IEnumerator> <xref:System.IDisposable> .

## <a name="c-version-20"></a>C# sürüm 2,0

Şimdi ilginç şeyler almaya başlamıştır. Visual Studio 2005 ile birlikte 2005 ' de yayınlanan C# 2,0 ' nin bazı önemli özelliklerine göz atalım:

- [Genel Türler](../programming-guide/generics/index.md)
- [Kısmi türler](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Anonim Yöntemler](../language-reference/operators/delegate-operator.md)
- [Boş değer atanabilen değer türleri](../language-reference/builtin-types/nullable-value-types.md)
- [Yineleyiciler](../programming-guide/concepts/iterators.md)
- [Kovaryans ve kontravaryans](../programming-guide/concepts/covariance-contravariance/index.md)

Diğer C# 2,0 özellikleri varolan özelliklere özellikler eklemiştir:

- Alıcı/ayarlayıcı ayrı erişilebilirlik
- Yöntem grubu dönüştürmeleri (Temsilciler)
- Statik sınıflar
- Temsilci çıkarımı

C# genel nesne yönelimli (OO) dil olarak başlatılmış olsa da, bir acede C# sürüm 2,0 değiştirilmiştir. Bunların altındaysa, önemli geliştirici sorun noktalarından sonra gitirler. Ve bunları önemli bir şekilde yaptıktan sonra.

Genel türler ile türler ve Yöntemler, tür güvenliğini korurken rastgele bir tür üzerinde çalışabilir. Örneğin, bir uygulamasına sahip olma, <xref:System.Collections.Generic.List%601> `List<string>` `List<int>` Bu dizeler veya tamsayılar üzerinde yineleme yaparken tür kullanımı güvenli işlemleri gerçekleştirmenize izin verir. Genel türleri kullanmak, `ListInt` `ArrayList`  her işlem için kaynağından veya kümeden türeten daha iyidir `Object` .

C# sürüm 2,0 yineleyiciler tarafından getirildi. Yineleyiciler, succinctly koymak için bir `List` (veya diğer sıralanabilir türler) içindeki tüm öğeleri bir `foreach` döngüyle incelemenizi sağlar. Dilin birinci sınıf parçası olarak yineleyiciler olması, dilin okunabilirliğini ve kişilerin kod hakkında neden olma yeteneğini önemli ölçüde geliştirmiştir.

Ancak, C#, Java ile biraz catch oynamaya devam eder. Java, genel türler ve yineleyiciler içeren sürümleri zaten yayımlamıştır. Ancak yakında gelişmeye devam eden diller olarak değişir.

## <a name="c-version-30"></a>C# sürüm 3,0

C# sürüm 3,0, Visual Studio 2008 ile birlikte 2007 geldi, ancak dil özelliklerinin tam bot 'ı .NET Framework sürüm 3,5 ile gelmiş olabilir. Bu sürüm, C# büyümesi için büyük bir değişiklik işaretledi. Bu, gerçek anlamda anlaşılır programlama dili olarak C# kurdu. Bu sürümdeki bazı önemli özelliklere göz atalım:

- [Otomatik uygulanan özellikler](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Anonim türler](../programming-guide/classes-and-structs/anonymous-types.md)
- [Sorgu ifadeleri](../linq/query-expression-basics.md)
- [Lambda ifadeleri](../language-reference/operators/lambda-expressions.md)
- [İfade ağaçları](../expression-trees.md)
- [Genişletme yöntemleri](../programming-guide/classes-and-structs/extension-methods.md)
- [Örtük olarak yazılan yerel değişkenler](../language-reference/keywords/var.md)
- [Kısmi Yöntemler](../language-reference/keywords/partial-method.md)
- [Nesne ve koleksiyon başlatıcıları](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

Geriye dönük olarak, bu özelliklerin çoğu hem kaçınılmazdır hem de ınseparablegörünmektedir. Hepsi stratejik olarak bir araya gelerek. Genellikle C# sürümünün Killer özelliğinin, dil ile tümleşik sorgu (LINQ) olarak da bilinen sorgu ifadesi olması düşünüldük.

Daha fazla kızılmış bir görünüm, LINQ 'ın oluşturulduğu temel olarak ifade ağaçları, lambda ifadeleri ve anonim türler inceler. Ancak her iki durumda da C# 3,0, Devrim niteliğinde bir kavram olarak sunulur. C# 3,0, C# ' ın karma nesne odaklı/Işlevsel bir dile dönmesini sağlamak için groundişini düzenleme ile başlamıştır.

Özellikle, koleksiyonlar üzerinde işlemler gerçekleştirmek için diğer şeyler arasında SQL stili, bildirime dayalı sorgular yazabilirsiniz. `for`Bir tamsayılar listesinin ortalamasını hesaplamak için bir döngü yazmak yerine, artık bunu gibi yapabilirsiniz `list.Average()` . Sorgu ifadelerinin ve genişletme yöntemlerinin birleşimi, tam olarak çok daha akıllı bir şekilde kullanıma sunulacaktır.

İnsanların gerçekten bir kavram ve kavramı tümleştirmeleri için zaman sürdü, ancak bu, yavaş yavaş bir şekilde yapılır. Şimdi, daha sonra kod daha kısa, basit ve işlevsel.

## <a name="c-version-40"></a>C# sürüm 4,0

Visual Studio 2010 ile yayınlanan C# sürüm 4,0, sürüm 3,0 çığır durumuna zorlaştırıyor. Sürüm 3,0 ile C#, dili Java 'nın gölgimiyle ve belirgin bir şekilde daha sıkıca taşımıştı. Dil hızlı bir şekilde şık hale geliyor.

Sonraki sürümde bazı ilginç yeni özellikler tanıtıldı:

- [Dinamik bağlama](../language-reference/builtin-types/reference-types.md)
- [Adlandırılmış/isteğe bağlı bağımsız değişkenler](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Genel birlikte değişken ve değişken karşıtı](../../standard/generics/covariance-and-contravariance.md)
- [Gömülü birlikte çalışma türleri](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Gömülü birlikte çalışma türleri bir dağıtım sorun alleviated. Genel Kovaryans ve değişken Varyans, genel türler kullanmak için daha fazla güç sunar, ancak bu, büyük olasılıkla çerçeve ve kitaplık yazarları tarafından en çok teşekkürler. Adlandırılmış ve isteğe bağlı parametreler birçok yöntem aşırı yüklemesini ortadan kaldırmanıza ve kolaylık sağlamanıza olanak tanır. Ancak bu özelliklerden hiçbiri tam olarak paradigma değiştirme değildir.

Ana Özellik, `dynamic` anahtar sözcüğünün sunumiydi. `dynamic`C# sürüm 4,0 ' de tanıtılan anahtar sözcük, derleme zamanı yazma sırasında derleyiciyi geçersiz kılabilme özelliği. Dinamik anahtar sözcüğünü kullanarak JavaScript gibi dinamik olarak belirlenmiş dillere benzer yapılar oluşturabilirsiniz. Bir oluşturup `dynamic x = "a string"` daha sonra ne olması gerektiğini sıralamak için bu bir tane oluşturabilir ve ardından çalışma zamanına kadar bırakabilirsiniz.

Dinamik bağlama, hataları olası ve ayrıca dil dahilinde harika bir güç sağlar.

## <a name="c-version-50"></a>C# sürüm 5,0

Visual Studio 2012 ile yayınlanan C# sürüm 5,0, dilin odaklanmış bir sürümüdür. Bu sürüm için neredeyse tüm çaba başka bir çığır dil kavramıyla karşılaştık: `async` `await` zaman uyumsuz programlama için ve modeli.  Ana özellikler listesi aşağıda verilmiştir:

- [Zaman uyumsuz Üyeler](../async.md)
- [Arayan bilgileri öznitelikleri](../language-reference/attributes/caller-information.md)

### <a name="see-also"></a>Ayrıca Bkz.

- [Kod projesi: C# 5,0 ' de çağıran bilgi öznitelikleri](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Çağıran bilgileri özniteliği, bir çok ortak yansıma kodu için kod olmadan çalıştırdığınız bağlam hakkındaki bilgileri kolayca almanızı sağlar. Tanılama ve günlüğe kaydetme görevlerinde birçok kullanımı vardır.

Ancak `async` , `await` Bu sürümün gerçek yıldızları da vardır. Bu özellikler 2012 ' de geldiğinde, C#, ilk sınıf katılımcı olarak dile eşitlemeyi bir kez daha inceleyerek oyunu tekrar değiştirdi. Uzun süre çalışan işlemlerle ve geri çağırmaların Web 'leri uygulamasına sahip olduğunuzda, büyük olasılıkla bu dil özelliğini sevtiniz.

## <a name="c-version-60"></a>C# sürüm 6,0

C#, 3,0 ve 5,0 sürümleriyle, nesne yönelimli bir dilde önemli yeni özellikler eklemiştir. Visual Studio 2015 ile yayınlanan sürüm 6,0 ' de, baskın bir Killer özelliği yapmaktan sonra C# programlama daha üretken hale getirilen daha küçük birçok özellik yayımlayacaktır. Bunlardan bazıları şunlardır:

- [Statik içeri aktarmalar](./csharp-6.md#using-static)
- [Özel durum filtreleri](./csharp-6.md#exception-filters)
- [Otomatik Özellik başlatıcıları](./csharp-6.md#auto-property-initializers)
- [İfade gövdeli Üyeler](./csharp-6.md#expression-bodied-function-members)
- [Null yayıcı](./csharp-6.md#null-conditional-operators)
- [Dize ilişkilendirme](./csharp-6.md#string-interpolation)
- [NameOf işleci](./csharp-6.md#the-nameof-expression)
- [Dizin başlatıcıları](csharp-6.md#extension-add-methods-in-collection-initializers)

Diğer yeni özellikler şunlardır:

- Catch/finally bloklarında await
- Yalnızca alıcı özellikleri için varsayılan değerler

Bu özelliklerin her biri kendi sağında ilginç olur. Ancak bunları tamamen gözden geçirin, ilginç bir model görürsünüz. Bu sürümde C#, kodu daha terse ve okunabilir hale getirmek için ortak bir dil olarak eledi. Bu nedenle, temiz ve basit kod fanları için bu dil sürümü çok büyük bir kazanmıştı.

Bunlar, kendi kendine geleneksel bir dil özelliği olmasa da, bu sürümle birlikte başka bir şey gerçekleştirmektedir. [Hizmet olarak derleyicisini](https://github.com/dotnet/roslyn)serbest bırakılanlar. C# derleyicisi artık C# dilinde yazılmıştır ve derleyici, programlama çabalarınızın bir parçası olarak kullanılabilir.

## <a name="c-version-70"></a>C# sürüm 7,0

C# sürüm 7,0, Visual Studio 2017 ile yayınlanmıştır. Bu sürüm, C# 6,0 ' de, ancak hizmet olarak derleyici olmadan bazı evminte ve seyrek bulunan bilgiler içerir. Yeni özelliklerden bazıları şunlardır:

- [Out değişkenleri](./csharp-7.md#out-variables)
- [Tanımlama grupları ve ayrıştırma](./csharp-7.md#tuples-and-discards)
- [Model eşleştirme](./csharp-7.md#pattern-matching)
- [Yerel işlevler](./csharp-7.md#local-functions)
- [Genişletilmiş ifade gövdeli Üyeler](./csharp-7.md#more-expression-bodied-members)
- [Ref Yereller ve geri dönüşler](./csharp-7.md#ref-locals-and-returns)

Dahil edilen diğer özellikler:

- [Atılanlar](./csharp-7.md#tuples-and-discards)
- [İkili sabit değerler ve basamak ayırıcıları](./csharp-7.md#numeric-literal-syntax-improvements)
- [Throw ifadeleri](./csharp-7.md#throw-expressions)

Bu özelliklerin tümü, geliştiriciler için seyrek erişimli yeni özellikler sunar ve her zamankinden sonra bile temizleyici kodu yazma fırsatına sahiptir. Vurgu, anahtar sözcükle birlikte kullanılacak değişkenlerin bildirimini `out` ve kayıt düzeni aracılığıyla birden çok dönüş değerine izin vererek bir vurgulanmasını sağlar.

Ancak C#, daha geniş bir kullanıma yerleştirmekte. .NET Core artık herhangi bir işletim sistemini hedeflemiştir ve bu durumda, hem bulutta hem de taşınabilirlik konusunda gözleriniz vardır.  Bu yeni özellikler, yeni özelliklerle birlikte gelmenin yanı sıra dil tasarımcıları 'nın düşüncelerini ve zamanını tamamen kaplar.

## <a name="c-version-71"></a>C# sürüm 7,1

C#, c# 7,1 ile *nokta sürümlerini* serbest bırakma işlemi başlattı. Bu sürüm, [dil sürümü seçimi](../language-reference/configure-language-version.md) yapılandırma öğesini, üç yeni dil özelliğini ve yeni derleyici davranışını ekledi.

Bu sürümdeki yeni dil özellikleri şunlardır:

- [`async``Main`yöntemi](./csharp-7.md#async-main)
  - Bir uygulama için giriş noktası değiştiriciye sahip olabilir `async` .
- [`default` değişmez değer ifadeleri](./csharp-7.md#default-literal-expressions)
  - Hedef türü çıkarsanamıyor varsayılan değer ifadelerinde varsayılan değişmez ifadeleri kullanabilirsiniz.
- [Gösterilen demet öğesi adları](./csharp-7.md#tuples-and-discards)
  - Kayıt düzeni öğelerinin adları, birçok durumda demet başlatmasıyla çıkarsanamıyor.
- [Genel tür parametrelerinde model eşleştirme](./csharp-7.md#pattern-matching)
  - Türü genel bir tür parametresi olan değişkenlerde model eşleşme ifadeleri kullanabilirsiniz.

Son olarak, derleyici iki seçeneğe sahiptir `-refout` ve `-refonly` Bu, [Başvuru derleme üretimini](./csharp-7.md#reference-assembly-generation)denetler.

## <a name="c-version-72"></a>C# sürüm 7,2

C# 7,2 birkaç küçük dil özelliği ekledi:

- [Güvenli verimli kod yazma teknikleri](./csharp-7.md#enabling-more-efficient-safe-code)
  - Başvuru semantiğinin kullanıldığı değer türleriyle çalışmayı sağlayan sözdizimi geliştirmelerinden oluşan bir bileşim.
- [Girintili olmayan adlandırılmış bağımsız değişkenler](./csharp-7.md#non-trailing-named-arguments)
  - Adlandırılmış bağımsız değişkenlerin ardından konumsal bağımsız değişkenler gelebilir.
- [Sayısal sabit değerlerde önde gelen alt çizgiler](./csharp-7.md#numeric-literal-syntax-improvements)
  - Sayısal değişmez değerler artık, yazdırılan rakamlardan önce önde gelen alt çizgileri olabilir.
- [`private protected` erişim değiştiricisi](./csharp-7.md#private-protected-access-modifier)
  - `private protected`Erişim değiştiricisi aynı derlemede türetilmiş sınıflar için erişim imkanı sunar.
- [Koşullu `ref` ifadeler](./csharp-7.md#conditional-ref-expressions)
  - Koşullu ifadenin ( `?:` ) sonucu artık bir başvuru olabilir.

## <a name="c-version-73"></a>C# sürüm 7,3

C# 7,3 sürümünün iki ana teması vardır. Bir tema, güvenli kodun güvenli olmayan kod olarak performans sağlamak için gereken özellikler sağlar. İkinci tema, mevcut özelliklerle artımlı iyileştirmeler sağlar. Ayrıca, bu yayına yeni derleyici seçenekleri eklenmiştir.

Aşağıdaki yeni özellikler, güvenli kod için daha iyi performans temasını destekler:

- [Sabitlemeden sabit alanlara erişebilirsiniz.](csharp-7.md#indexing-fixed-fields-does-not-require-pinning)
- [`ref`Yerel değişkenleri yeniden atayabilirsiniz.](csharp-7.md#enabling-more-efficient-safe-code)
- [Dizilerde başlatıcıları kullanabilirsiniz `stackalloc` .](csharp-7.md#stackalloc-arrays-support-initializers)
- [`fixed`Deyimlerini, bir kalıbı destekleyen herhangi bir türle birlikte kullanabilirsiniz.](csharp-7.md#more-types-support-the-fixed-statement)
- [Ek genel kısıtlamalar kullanabilirsiniz.](csharp-7.md#enhanced-generic-constraints)

Mevcut özelliklerde aşağıdaki geliştirmeler yapılmıştır:

- `==` `!=` Kayıt düzeni türlerini test edebilirsiniz.
- İfade değişkenlerini daha fazla konumda kullanabilirsiniz.
- Otomatik uygulanan özelliklerin yedekleme alanına öznitelikler iliştirebilirsiniz.
- Bağımsız değişkenler farklı olduğunda yöntem çözümlemesi `in` geliştirildi.
- Aşırı yükleme çözümlemesi artık daha az belirsiz durum içeriyor.

Yeni derleyici seçenekleri şunlardır:

- `-publicsign` Açık kaynak yazılım (OSS) derlemelerinin imzalanmasını etkinleştirmek için.
- `-pathmap` Kaynak dizinlere eşleme sağlamak için.

## <a name="c-version-80"></a>C# sürüm 8,0

C# 8,0, .NET Core 'un özel olarak hedeflediği ilk önemli C# sürümüdür. Bazı özellikler yeni CLR özelliklerine dayanır, diğer bir deyişle kitaplık türlerindeki bazıları yalnızca .NET Core 'a eklenir. C# 8,0, C# diline aşağıdaki özellikleri ve geliştirmeleri ekler:

- [Salt okunur Üyeler](./csharp-8.md#readonly-members)
- [Varsayılan arabirim metotları](./csharp-8.md#default-interface-methods)
- [Desenler eşleşen geliştirmeler](./csharp-8.md#more-patterns-in-more-places):
  - [Anahtar ifadeleri](./csharp-8.md#switch-expressions)
  - [Özellik desenleri](./csharp-8.md#property-patterns)
  - [Demet desenleri](./csharp-8.md#tuple-patterns)
  - [Konumsal desenler](./csharp-8.md#positional-patterns)
- [Bildirimleri kullanma](./csharp-8.md#using-declarations)
- [Statik yerel işlevler](./csharp-8.md#static-local-functions)
- [Atılabilir ref yapıları](./csharp-8.md#disposable-ref-structs)
- [Boş değer atanabilir başvuru türleri](../language-reference/builtin-types/nullable-reference-types.md)
- [Zaman uyumsuz akışlar](./csharp-8.md#asynchronous-streams)
- [Dizinler ve aralıklar](./csharp-8.md#indices-and-ranges)
- [Null birleştirme ataması](./csharp-8.md#null-coalescing-assignment)
- [Yönetilmeyen oluşturulmuş türler](./csharp-8.md#unmanaged-constructed-types)
- [İç içe ifadelerde stackalloc](./csharp-8.md#stackalloc-in-nested-expressions)
- [Ara değerli tam dizelerin geliştirilmesi](./csharp-8.md#enhancement-of-interpolated-verbatim-strings)

Varsayılan arabirim üyeleri CLR 'de geliştirmeler gerektirir. Bu özellikler .NET Core 3,0 için CLR 'ye eklenmiştir. Aralıklar ve dizinler ve zaman uyumsuz akışlar, .NET Core 3,0 kitaplıklarında yeni türler gerektirir. Bağımsız değişken ve dönüş değerlerinin NULL durumu ile ilgili anlam bilgilerini sağlamak üzere, derleyicide uygulanan null yapılabilir başvuru türleri, kitaplıklar açıklandığında çok daha yararlıdır. Bu ek açıklamalar .NET Core kitaplıklarına ekleniyor.

İlk olarak_Nıdidıetrich ve Patrick Smacchia,_ [_nbağlı blog 'da yayımlanan_](https://blog.ndepend.com/c-versions-look-language-history/) _Makale_ .
