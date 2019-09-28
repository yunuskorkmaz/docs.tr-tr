---
title: C# Kılavuz geçmişi C#
description: Dil en eski sürümlerinde ne şekilde görünür ve bu tarihten sonra nasıl gelişmiştir?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: e8bf39716482eb94e5686c1a150667be9f8ef620
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71391955"
---
# <a name="the-history-of-c"></a>C geçmişi\#

Bu makalede, C# dilin her bir ana sürümünün geçmişi sağlanmaktadır. C# Takım yenilik yapın ve yeni özellikler eklemeye devam etmektedir. Gelecek sürümler için kabul edilen özellikler dahil olmak üzere ayrıntılı dil özelliği durumu GitHub 'daki [DotNet/Roslyn deposunda](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) bulunabilir.

> [!IMPORTANT]
> C# Dil, C# belirtimin bazı özellikler için *standart kitaplık* olarak tanımladığı tür ve yöntemlere dayanır. .NET platformu bu türleri ve yöntemleri bir dizi pakete sunar. Özel durum işleme bir örnektir. Oluşturulan `throw` nesnenin<xref:System.Exception>türetildiğinden emin olmak için her deyim veya ifade denetlenir. Benzer şekilde, `catch` yakalanan türün <xref:System.Exception>türediğinden emin olmak için her ikisi de denetlenir. Her sürümde yeni gereksinimler eklenebilir. Eski ortamlarda en son dil özelliklerini kullanmak için, belirli kitaplıkları yüklemeniz gerekebilir. Bu bağımlılıklar, her belirli sürüm için sayfasında belgelenmiştir. Bu bağımlılıkta arka plan için [dil ve kitaplık arasındaki ilişkiler](relationships-between-language-and-library.md) hakkında daha fazla bilgi edinebilirsiniz.

C# Yapı araçları, varsayılan dil sürümü olan en son ana dil sürümünü göz önünde bulundurun. Bu bölümdeki diğer makalelerde ayrıntılı olarak açıklanan ana yayınlar arasında nokta yayınları olabilir. En son özellikleri bir nokta sürümünde kullanmak için, [Derleyici dil sürümünü yapılandırmanız](../language-reference/configure-language-version.md) ve sürümü seçmeniz gerekir. 7,0 sonrasında C# üç nokta yayını vardı:

- [ C# 7,3](csharp-7-3.md):
  - C#7,3, [Visual Studio 2017 sürüm 15,7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ve [.NET Core 2,1 SDK](../../core/whats-new/dotnet-core-2-1.md)ile başlayarak kullanılabilir.
- [ C# 7,2](csharp-7-2.md):
  - C#7,2, [Visual Studio 2017 sürüm 15,5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)ve [.NET Core 2,0 SDK](../../core/whats-new/dotnet-core-2-0.md)ile başlayarak kullanılabilir.
- [ C# 7,1](csharp-7-1.md):
  - C#7,1, [Visual Studio 2017 sürüm 15,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ve [.NET Core 2,0 SDK](../../core/whats-new/dotnet-core-2-0.md)ile başlayarak kullanılabilir.

## <a name="c-version-10"></a>C#sürüm 1,0

Geri dönerek Visual Studio.net 2002 ile yayınlanan C# sürüm 1,0, Java gibi çok sayıda görünür. [ECMA için belirtilen tasarım hedeflerinin bir parçası](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)olarak, "basit, modern, genel amaçlı nesne yönelimli bir dil" olarak arar.  Bu sırada, Java gibi, bu erken tasarım hedefleri elde ettiği anlamına gelir.

Ancak şimdi C# 1,0 ' ye geri bakarsanız, kendinizi biraz daha bulabilirsiniz. Yerleşik zaman uyumsuz özellikleri ve izin verilen genel türler etrafında bulunan bazı nesnelerin bazı nesnelerin bazı özelliklerini ele alır. Aslında, genel türleri tamamen ele edindi.  Ve [LINQ](../linq/index.md)? Henüz kullanılamıyor. Bu eklemelerin gelmesi birkaç yıl sürer.

C#sürüm 1,0, bugün ile karşılaştırıldığında özelliklerden çıkarılır. Kendinize bazı ayrıntılı kodlar yazmaktır. Ancak yine de bir yere başlamanız gerekir. C#sürüm 1,0, Windows platformunda Java için önemli bir alternatiftir.

1,0 'nin C# önemli özellikleri dahildir:

- [Sınıflar](../programming-guide/classes-and-structs/classes.md)
- [Yapılar](../programming-guide/classes-and-structs/structs.md)
- [Arabirimler](../programming-guide/interfaces/index.md)
- [Olaylar](../events-overview.md)
- [Özellikler](../properties.md)
- [Temsilciler](../delegates-overview.md)
- [İfadeler](../programming-guide/statements-expressions-operators/expressions.md)
- [Deyimler](../programming-guide/statements-expressions-operators/statements.md)
- [Öznitelikler](../programming-guide/concepts/attributes/index.md)

## <a name="c-version-12"></a>C#sürüm 1,2

C#sürüm 1,2, Visual Studio 2003 ile birlikte gönderilir. Dilde birkaç küçük geliştirmeler vardı. Çoğu önemli, `foreach` Bu sürümden başlayarak, <xref:System.Collections.IEnumerator> uygulandığında <xref:System.IDisposable>bir <xref:System.IDisposable.Dispose%2A> <xref:System.Collections.IEnumerator> döngüsünde oluşturulan bir döngüde oluşturulan kod.

## <a name="c-version-20"></a>C#sürüm 2,0

Şimdi ilginç şeyler almaya başlamıştır. Visual Studio 2005 ile birlikte 2005 ' de yayınlanan bazı C# önemli 2,0 özelliklere göz atalım:

- [Genel Türler](../programming-guide/generics/index.md)
- [Kısmi türler](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Anonim Yöntemler](../language-reference/operators/delegate-operator.md)
- [Null yapılabilir değer türleri](../programming-guide/nullable-types/index.md)
- [Yineleyiciler](../programming-guide/concepts/iterators.md)
- [Kovaryans ve değişken sapması](../programming-guide/concepts/covariance-contravariance/index.md)

Diğer C# 2,0 özellikleri mevcut özelliklere özellikler eklemiştir:

- Alıcı/ayarlayıcı ayrı erişilebilirlik
- Yöntem grubu dönüştürmeleri (Temsilciler)
- Statik sınıflar
- Temsilci çıkarımı

C# Genel bir nesne YÖNELIMLI (OO) dil olarak başlamışsa, sürüm 2,0, C# bir acelendeki olarak değiştirilmiştir. Bunların altındaysa, önemli geliştirici sorun noktalarından sonra gitirler. Ve bunları önemli bir şekilde yaptıktan sonra.

Genel türler ile türler ve Yöntemler, tür güvenliğini korurken rastgele bir tür üzerinde çalışabilir. Örneğin, bir <xref:System.Collections.Generic.List%601> uygulamasına `List<string>` `List<int>` sahip olma, bu dizeler veya tamsayılar üzerinde yineleme yaparken tür kullanımı güvenli işlemleri gerçekleştirmenize izin verir. Genel türleri kullanmak, her işlem `ListInt` için kaynağından `ArrayList` veya kümeden `Object` türeten daha iyidir.

C#sürüm 2,0, yineleyiciler tarafından getirildi. Yineleyiciler, succinctly koymak için bir `List` (veya diğer sıralanabilir türler) içindeki tüm öğeleri bir `foreach` döngüyle incelemenizi sağlar. Dilin birinci sınıf parçası olarak yineleyiciler olması, dilin okunabilirliğini ve kişilerin kod hakkında neden olma yeteneğini önemli ölçüde geliştirmiştir.

Ancak, C# Java ile biraz catch oynamaya devam eder. Java, genel türler ve yineleyiciler içeren sürümleri zaten yayımlamıştır. Ancak yakında gelişmeye devam eden diller olarak değişir.

## <a name="c-version-30"></a>C#sürüm 3,0

C#sürüm 3,0, Visual Studio 2008 ile birlikte 2007 geldi, ancak dil özelliklerinin tam bot 'ı .NET Framework sürüm 3,5 ile gelmiş olabilir. Bu sürüm, büyümesi için büyük bir değişiklik işaretledi C#. Gerçekten anlaşılabilir C# programlama dili olarak oluşturulmuştur. Bu sürümdeki bazı önemli özelliklere göz atalım:

- [Otomatik uygulanan özellikler](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Anonim türler](../programming-guide/classes-and-structs/anonymous-types.md)
- [Sorgu ifadeleri](../linq/query-expression-basics.md)
- [Lambda ifadeleri](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [İfade ağaçları](../expression-trees.md)
- [Uzantı yöntemleri](../programming-guide/classes-and-structs/extension-methods.md)
- [Örtük olarak yazılan yerel değişkenler](../language-reference/keywords/var.md)
- [Kısmi Yöntemler](../language-reference/keywords/partial-method.md)
- [Nesne ve koleksiyon başlatıcıları](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

Geriye dönük olarak, bu özelliklerin çoğu hem kaçınılmazdır hem de ınseparablegörünmektedir. Hepsi stratejik olarak bir araya gelerek. Genellikle C# sürümün Killer özelliğinin, dil Ile tümleşik sorgu (LINQ) olarak da bilinen sorgu ifadesi olması düşünüldük.

Daha fazla kızılmış bir görünüm, LINQ 'ın oluşturulduğu temel olarak ifade ağaçları, lambda ifadeleri ve anonim türler inceler. Ancak her iki durumda da 3,0 C# , Devrim niteliğinde bir kavram olarak sunulur. C#3,0, bir karma nesne odaklı/işlevsel dili açmak C# için ön hazırlıkları başlattık 'un düzenlenmesine başlamıştır.

Özellikle, koleksiyonlar üzerinde işlemler gerçekleştirmek için diğer şeyler arasında SQL stili, bildirime dayalı sorgular yazabilirsiniz. Bir tamsayılar listesinin ortalamasını `for` hesaplamak için bir döngü yazmak yerine, artık bunu gibi `list.Average()`yapabilirsiniz. Sorgu ifadelerinin ve genişletme yöntemlerinin birleşimi, tam olarak çok daha akıllı bir şekilde kullanıma sunulacaktır.

İnsanların gerçekten bir kavram ve kavramı tümleştirmeleri için zaman sürdü, ancak bu, yavaş yavaş bir şekilde yapılır. Şimdi, daha sonra kod daha kısa, basit ve işlevsel.

## <a name="c-version-40"></a>C#sürüm 4,0

C#Visual Studio 2010 ile yayınlanan sürüm 4,0, sürüm 3,0 çığır durumuna kadar zor bir zamana sahip olurdu. Sürüm 3,0 ile, C# dili Java 'nın gölgimiyle ve belirgin bir şekilde daha sıkıca taşımıştı. Dil hızlı bir şekilde şık hale geliyor.

Sonraki sürümde bazı ilginç yeni özellikler tanıtıldı:

- [Dinamik bağlama](../language-reference/keywords/dynamic.md)
- [Adlandırılmış/isteğe bağlı bağımsız değişkenler](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Genel birlikte değişken ve değişken karşıtı](../../standard/generics/covariance-and-contravariance.md)
- [Gömülü birlikte çalışma türleri](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Gömülü birlikte çalışma türleri bir dağıtım sorun alleviated. Genel Kovaryans ve değişken Varyans, genel türler kullanmak için daha fazla güç sunar, ancak bu, büyük olasılıkla çerçeve ve kitaplık yazarları tarafından en çok teşekkürler. Adlandırılmış ve isteğe bağlı parametreler birçok yöntem aşırı yüklemesini ortadan kaldırmanıza ve kolaylık sağlamanıza olanak tanır. Ancak bu özelliklerden hiçbiri tam olarak paradigma değiştirme değildir.

Ana Özellik, `dynamic` anahtar sözcüğünün sunumiydi. Sürüm 4,0 ' de tanıtılan anahtarsözcük,derlemezamanıyazmasırasındaderleyiciyigeçersizkılabilmeözelliği.`dynamic` C# Dinamik anahtar sözcüğünü kullanarak JavaScript gibi dinamik olarak belirlenmiş dillere benzer yapılar oluşturabilirsiniz. Bir oluşturup daha sonra `dynamic x = "a string"` ne olması gerektiğini sıralamak için bu bir tane oluşturabilir ve ardından çalışma zamanına kadar bırakabilirsiniz.

Dinamik bağlama, hataları olası ve ayrıca dil dahilinde harika bir güç sağlar.

## <a name="c-version-50"></a>C#sürüm 5,0

C#Visual Studio 2012 ile yayınlanan sürüm 5,0, dilin odaklanmış bir sürümüdür. Bu sürüm için neredeyse tüm çaba başka bir çığır dil kavramıyla karşılaştık: `async` zaman uyumsuz programlama için ve `await` modeli.  Ana özellikler listesi aşağıda verilmiştir:

- [Zaman uyumsuz Üyeler](../async.md)
- [Arayan bilgileri öznitelikleri](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a>Ayrıca Bkz.

- [Kod projesi: 5,0 ' de C# çağıran bilgi öznitelikleri](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Çağıran bilgileri özniteliği, bir çok ortak yansıma kodu için kod olmadan çalıştırdığınız bağlam hakkındaki bilgileri kolayca almanızı sağlar. Tanılama ve günlüğe kaydetme görevlerinde birçok kullanımı vardır.

Ancak `async`, bu sürümün gerçek yıldızları da vardır.`await` Bu özellikler 2012 ' de geldiğinde, C# ilk sınıf katılımcı olarak dile zaman uyumlu hale getirerek oyunu yeniden değiştirdi. Uzun süre çalışan işlemlerle ve geri çağırmaların Web 'leri uygulamasına sahip olduğunuzda, büyük olasılıkla bu dil özelliğini sevtiniz.

## <a name="c-version-60"></a>C#sürüm 6,0

3,0 ve 5,0 sürümleriyle, C# nesne yönelimli bir dile önemli yeni özellikler ekledik. Visual Studio 2013 ile yayınlanan sürüm 6,0 ile, baskın bir çıkarıcı Özellik yapmaktan sonra daha üretken bir şekilde programlama yapan C# daha küçük birçok özellik yayımlayacaktır. Bunlardan bazıları şunlardır:

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

Bu özelliklerin her biri kendi sağında ilginç olur. Ancak bunları tamamen gözden geçirin, ilginç bir model görürsünüz. Bu sürümde, C# kodu daha terse ve okunabilir hale getirmek için dilin ortak olduğunu ortadan kaldırdık. Bu nedenle, temiz ve basit kod fanları için bu dil sürümü çok büyük bir kazanmıştı.

Bunlar, kendi kendine geleneksel bir dil özelliği olmasa da, bu sürümle birlikte başka bir şey gerçekleştirmektedir. [Hizmet olarak derleyicisini](https://github.com/dotnet/roslyn)serbest bırakılanlar. C# Derleyici artık ' de C#yazılmıştır ve bu derleyicisini programlama çabalarınızın bir parçası olarak kullanabilirsiniz.

## <a name="c-version-70"></a>C#sürüm 7,0

En son ana sürüm, Visual C# Studio 2017 ile yayınlanan sürüm 7,0 ' dir. Bu sürümde, 6,0 ' de, ancak hizmet olarak derleyici olmayan bir dizi C# ve seyrek şey vardır. Yeni özelliklerden bazıları şunlardır:

- [Out değişkenleri](./csharp-7.md#out-variables)
- [Tanımlama grupları ve ayrıştırma](./csharp-7.md#tuples)
- [Desen eşleştirme](./csharp-7.md#pattern-matching)
- [Yerel işlevler](./csharp-7.md#local-functions)
- [Genişletilmiş ifade gövdeli Üyeler](./csharp-7.md#more-expression-bodied-members)
- [Ref Yereller ve geri dönüşler](./csharp-7.md#ref-locals-and-returns)

Dahil edilen diğer özellikler:

- [Atılanlar](./csharp-7.md#discards)
- [İkili sabit değerler ve basamak ayırıcıları](./csharp-7.md#numeric-literal-syntax-improvements)
- [Throw ifadeleri](./csharp-7.md#throw-expressions)

Bu özelliklerin tümü, geliştiriciler için seyrek erişimli yeni özellikler sunar ve her zamankinden sonra bile temizleyici kodu yazma fırsatına sahiptir. Vurgu, `out` anahtar sözcükle birlikte kullanılacak değişkenlerin bildirimini ve kayıt düzeni aracılığıyla birden çok dönüş değerine izin vererek bir vurgulanmasını sağlar.

Ancak C# , daha geniş bir kullanıma yerleştirmekte. .NET Core artık herhangi bir işletim sistemini hedeflemiştir ve bu durumda, hem bulutta hem de taşınabilirlik konusunda gözleriniz vardır.  Bu yeni özellikler, yeni özelliklerle birlikte gelmenin yanı sıra dil tasarımcıları 'nın düşüncelerini ve zamanını tamamen kaplar.

_Makale_ [_ilk olarak nbağlı blogda yayımlandı_](https://blog.ndepend.com/c-versions-look-language-history/) _, Erik Dietrich ve Patrick Smacchia._
