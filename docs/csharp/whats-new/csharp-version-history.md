---
title: Geçmişini C# - C# Kılavuzu
description: Bu yana nasıl geliştirildiğini ve önceki sürümlerde dil göz ne gibi?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 727f0064ac1de46eb670a366af38cf561e1a1533
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303368"
---
# <a name="the-history-of-c"></a>C geçmişi\#

Bu makalede, her ana sürümüne geçmişini sağlar C# dili. C# Takım etmeden yenilik yapın ve yeni özellikler eklemek. Dil özelliği durum, gelecek sürümlerinde bulunabilir kabul özellikleri dahil olmak üzere ayrıntılı [dotnet/roslyn deposundaki](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) GitHub üzerinde.

> [!IMPORTANT]
> C# Türleri ve yöntemleri hangi dil kullanır C# belirtimi tanımlar olarak bir *standart Kitaplığı* bazı özellikler için. .NET platformu paketleri bir süre içinde bu türleri ve yöntemleri sunar. Özel durum işleme bir örnektir. Her `throw` deyiminin veya ifadesinin işaretli oluşturulan nesne emin olmak için türetilen <xref:System.Exception>. Benzer şekilde, her `catch` yakalandı tür türetilir emin olmak için denetlenir <xref:System.Exception>. Her sürüm, yeni gereksinimler ekleyebilirsiniz. En son dil özelliklerini daha eski ortamlarında kullanmak için belirli kitaplıkları yüklemeniz gerekebilir. Bu bağımlılıklar, her belirli bir sürüm sayfasında belgelenmiştir. Daha fazla bilgi edinebilirsiniz [dil ve kitaplığa arasındaki ilişkileri](relationships-between-language-and-library.md) bu bağımlılık hakkında arka plan bilgileri için.

C# Derleme araçları, varsayılan dil sürümü en son ana dil sürümü düşünün. Bu bölümdeki diğer makalelerinde ayrıntılı ana sürümler arasında nokta sürümleri olabilir. Bir nokta sürümde en son özellikleri kullanmak için yapmanız [derleyici dil sürüm yapılandırma](../language-reference/configure-language-version.md) ve sürüm seçin. Üç nokta sürümleri beri olmuştur C# 7.0:

* [C# 7.3](csharp-7-3.md):
  - C#7.3 sürümünden itibaren kullanılabilir [Visual Studio 2017 sürüm 15.7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ve [.NET Core 2.1 SDK](../../core/whats-new/dotnet-core-2-1.md).
* [C# 7.2](csharp-7-2.md):
  - C#7.2 sürümünden itibaren kullanılabilir [Visual Studio 2017 sürüm 15.5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), ve [.NET Core 2.0 SDK'sını](../../core/whats-new/dotnet-core-2-0.md).
* [C# 7.1](csharp-7-1.md):
  - C#7.1 sürümünden itibaren kullanılabilir [Visual Studio 2017 sürüm 15.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ve [.NET Core 2.0 SDK'sını](../../core/whats-new/dotnet-core-2-0.md).

## <a name="c-version-10"></a>C# sürüm 1.0

Geri dönün ve konum, C# sürüm 1.0 çok Java gibi görünüyordu. Olarak [belirtilen Tasarım hedeflerini ECMA parçası](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), bir "basit, modern, genel amaçlı nesne yönelimli dil." olmasını Aranan  Zaman erken bu tasarım hedefleri, Java desktop'takiler gibi mi arıyorsunuz elde edebilirsiniz.

Ancak geri C# 1.0 artık bakarsanız, kendiniz biraz dizzy bulur. Bu, yerleşik zaman uyumsuz özellikler ve verilen almak için genel türler etrafında bahsettiniz işlevlerinden bazıları koduk. Gibi bir matter, aslında, genel türler tamamen koduk.  Ve [LINQ](../linq/index.md)? Kullanılabilir değil henüz. Bu eklemeler gelecek bazı yıllarda sürecektir.

C# sürüm 1.0 için bugün karşılaştırıldığında özelliklerin kesilmiş arıyordu. Kendinizi ayrıntılı kod yazarken bulur. Ancak henüz bir yere başlatmak gerekir. C# sürüm 1.0 Windows platformunda uygun bir alternatif için Java oluştu.

C# 1.0 önemli özelliklere yer:

- [Sınıflar](../programming-guide/classes-and-structs/classes.md)
- [Yapılar](../programming-guide/classes-and-structs/structs.md)
- [Arabirimler](../programming-guide/interfaces/index.md)
- [Olaylar](../events-overview.md)
- [Özellikler](../properties.md)
- [Temsilciler](../delegates-overview.md)
- [İfadeler](../programming-guide/statements-expressions-operators/expressions.md)
- [Deyimler](../programming-guide/statements-expressions-operators/statements.md)
- [Öznitelikler](../programming-guide/concepts/attributes/index.md)
- [Sabit değerler](../language-reference/keywords/literal-keywords.md)

## <a name="c-version-12"></a>C# sürüm 1.2

C# sürüm 1.2 Visual Studio 2003 ile birlikte gelir. Bu dil için birkaç küçük geliştirmeler içeriyor. Bu sürümden başlayarak en dikkat çeken bir şey ise, oluşturulan kod bir `foreach` adlı döngü <xref:System.IDisposable.Dispose%2A> üzerinde bir <xref:System.Collections.IEnumerator> olduğunda, <xref:System.Collections.IEnumerator> uygulanan <xref:System.IDisposable>.

## <a name="c-version-20"></a>C# sürüm 2.0

Artık ilgi çekici şeyler başlatın. Bir C# 2005, Visual Studio 2005 ile birlikte yayımlanan 2.0, bazı önemli özelliklere göz atalım:

- [Genel Türler](../programming-guide/generics/index.md)
- [Kısmi türler](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Anonim yöntemler](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Boş değer atanabilir tipler](../programming-guide/nullable-types/index.md)
- [Yineleyiciler](../programming-guide/concepts/iterators.md)
- [Kovaryans ve kontravaryans](../programming-guide/concepts/covariance-contravariance/index.md)

Diğer C# 2.0 özellikleri Özellikler mevcut özellikleri ekledik:

- Alıcı/ayarlayıcı ayrı erişilebilirlik
- Yöntem grubu dönüştürmeler (temsilcileri)
- Statik sınıflar
- Temsilci çıkarma

C# genel bir Object-Oriented (Paylaşımlarınızda) dili olarak başlatılmamış olabilir, ancak C# sürüm 2.0, Aceleniz değiştirildi. Bunları altında kendi ayak sahip oldukları sonra bazı önemli Geliştirici sorunlu noktaları sonra sorun oluştu. ' İ tıklatın ve sonra bunları belirgin bir şekilde geçti.

Genel türler ile türleri ve yöntemleri hala tür güvenliğini korurken rastgele bir tür üzerinde çalışabilir. Örneğin, sahip bir <xref:System.Collections.Generic.List%601> olması sayesinde `List<string>` veya `List<int>` ve bunlar içerisinde yineleme yapmanızı sırada bu dize veya tamsayı tür açısından güvenli işlemler gerçekleştirin. Genel türler kullanarak oluşturmak yerine daha iyi `ListInt` türetilen `ArrayList` veya atama gelen `Object` her işlem için.

C# sürüm 2.0 duruma yineleyiciler. Temellerini koymak için yineleyiciler tüm öğeleri incelemenize olanak bir `List` (veya diğer numaralandırılabilir türleri) ile bir `foreach` döngü. Yineleyiciler dil birinci sınıf bir parçası olarak önemli ölçüde olması neden kodu hakkında daha fazla insana olanağı ile dil ve okunabilirliği iyileştirdik.

Ve henüz, C# biraz yakalama ayarlamasından Java ile oynamaya devam eder. Java zaten genel türler ve yineleyiciler sürümleri yayımlanan. Ancak, yakında parçalayın gelişmeye devam dilleri değiştirmeniz gerekir.

## <a name="c-version-30"></a>C# 3.0 sürümü

Dil özelliklerinin tam bot gerçekten .NET Framework sürüm 3.5 gelecektir ancak C# 3.0 sürümü Visual Studio 2008 ile birlikte geç 2007 geldi. Bu sürüm, C# büyümesi büyük bir değişiklik işaretlenmiş. Bunu C# kuruldu gerçekten formidable bir programlama dili olarak. Bu sürümde bazı önemli özelliklere göz atalım:

- [Otomatik uygulanan özellikler](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Anonim türler](../programming-guide/classes-and-structs/anonymous-types.md)
- [Sorgu ifadeleri](../linq/query-expression-basics.md)
- [Lambda ifadeleri](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [İfade ağaçları](../expression-trees.md)
- [Genişletme yöntemleri](../programming-guide/classes-and-structs/extension-methods.md)
- [Örtük olarak yazılan yerel değişkenler](../language-reference/keywords/var.md)
- [Kısmi yöntemler](../language-reference/keywords/partial-method.md)
- [Nesne ve koleksiyon başlatıcıları](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

Geriye dönüp, bu özelliklerin birçoğuna kaçınılmaz ve inseparable gibi görünüyor. Tüm bunların birlikte stratejik sığdırır. Bu genellikle C# sürümün harika özellik sorgu ifadesi olarak da bilinen dil ile tümleşik sorgu (LINQ) olduğunu düşündüğünüz.

İfade ağaçları, lambda ifadeleri ve anonim türler, durumunun daha ayrıntılı bir görünüm temellendirildiği LINQ oluşturulan temeli inceler. Ancak, her iki durumda da, C# 3.0 devrim niteliğinde bir kavram sunulur. C# 3.0 için C# karma nesne yönelimli / işlevsel dil kapatma nuspec'te başlamış.

Özellikle, artık SQL stili, başka şeylerin yanında, koleksiyonlar üzerinde işlem gerçekleştirmek için bildirim temelli sorgular yazabilirsiniz. Yazma yerine bir `for` tamsayı listesi ortalamasını hesaplamak için döngüsünde, bunu şimdi basit yapabilirsiniz olarak `list.Average()`. Sorgu ifadeleri ve genişletme yöntemleri birleşimi, tamsayı listesi çok daha akıllı edinmiş ancak gibi görünmesini yapıldı.

Sürdü kişilerin gerçekten kavrayın ve kavramı tümleştirmek, ancak aşamalı olarak vermedi. Ve artık, yıl, kodu çok daha kısa, basit ve işlev.

## <a name="c-version-40"></a>C# 4.0 sürümü

C# 4.0 sürümü için sürüm 3.0 çığır açan durumunu yaşayan zor bir süre beklendiğinden. Sürüm 3.0 ile C# dili metz'in out teklifleriyle içine ve Java gölge taşınmıştır. Dil hızla Zarif haline gelmişti.

Sonraki sürümü bazı ilgi çekici yeni özellikleri tanıtan:

- [Dinamik bağlama](../language-reference/keywords/dynamic.md)
- [Adlı/isteğe bağlı bağımsız değişkenler](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Genel değişken ve değişken karşıtı](../../standard/generics/covariance-and-contravariance.md)
- [Gömülü birlikte çalışma türleri](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Gömülü birlikte çalışma türleri dağıtım sorunlu alleviated. Genel Kovaryans ve kontravaryans, genel türler kullanmak için daha fazla güç sağlar, ancak biraz akademik ve büyük olasılıkla en takdir framework ve kitaplık yazarlar tarafından. Adlandırılmış ve isteğe bağlı parametreler, birçok yöntem aşırı yüklemeleri ortadan kaldırabilir ve kolaylık sağlayan olanak tanır. Ancak, bu özellikleri hiçbiri tam olarak paradigma değiştirme.

Önemli özellik kullanıma sunulması oldu `dynamic` anahtar sözcüğü. `dynamic` Anahtar sözcüğü sunulan C# diline sürüm 4.0 derleyici, derleme zamanı yazarak üzerinde geçersiz kılma olanağı. Dynamic anahtar sözcüğü kullanarak, yapıları benzer şekilde dinamik olarak yazılan diller JavaScript gibi oluşturabilirsiniz. Oluşturabileceğiniz bir `dynamic x = "a string"` ve altı için çalışma zamanının sonraki gerçekleşmesi gereken kullanıma sıralama kadar bırakarak ekleyin.

Dinamik bağlama, hatalar, ancak ayrıca dil içinde harika power olası sunar.

## <a name="c-version-50"></a>C# sürüm 5.0

C# sürüm 5.0 odaklanmış bir dil sürümünü oluştu. Neredeyse tüm bu sürüm için çaba başka bir çığır açan bir dil kavramını oluştu: `async` ve `await` zaman uyumsuz programlama için model.  Büyük özelliklerin listesi aşağıda verilmiştir:

- [Zaman uyumsuz üyeler](../async.md)
- [Arayan bilgileri öznitelikleri](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a>Ayrıca Bkz.

* [Kod projesi: Arayan bilgisi öznitelikleri içinde C# 5.0](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Çağıran bilgisi özniteliği kolayca sarmalayıcımızı yazdık ortak yansıma kod başvurmadan çalıştırıyorsanız bağlamıyla ilgili bilgileri almak olanak tanır. Bu, tanılama ve günlüğe kaydetme görevleri pek çok kullanımı vardır.

Ancak `async` ve `await` bu yayının gerçek yıldız olan. 2012'de bu özellikler ortaya çıktığında, C# oyunu yeniden birinci sınıf bir katılımcı olarak dile faaliyetler saklanacağı tarafından değiştirildi. Şimdiye kadar uzun süre çalışan işlemleri ve geri çağırmalar Web uygulaması ile ele, büyük olasılıkla bu dil özelliğinin sevdiği.

## <a name="c-version-60"></a>C# sürüm 6.0

3.0 ve 5.0 sürümleri ile C# önemli yeni özellikleri bir nesne yönelimli dil eklenen. Sürüm 6.0, baskın harika bir özellik yapılması uzağa gidin ve bunun yerine yapılan C# programlama daha üretken ve daha küçük birçok özellik sürüm. Bunlardan bazıları şunlardır:

- [Statik içeri aktarmalar](./csharp-6.md#using-static)
- [Özel durum filtreleri](./csharp-6.md#exception-filters)
- [Otomatik-özellik başlatıcıları](./csharp-6.md#auto-property-initializers)
- [İfade bodied üyeleri](./csharp-6.md#expression-bodied-function-members)
- [Null yayılması](./csharp-6.md#null-conditional-operators)
- [Dize ilişkilendirme](./csharp-6.md#string-interpolation)
- [nameof işleci](./csharp-6.md#the-nameof-expression)
- [Dizin başlatıcılar](csharp-6.md#extension-add-methods-in-collection-initializers)

Diğer yeni özellikler şunları içerir:

- Catch/finally bloklarında await
- Salt okuyucu özellikler için varsayılan değerler

Bu özelliklerin her biri kendi sağ ilginçtir. Ancak onları tamamen bakarsanız, ilgi çekici bir düzen görürsünüz. Bu sürümde, C# kod daha kısa ve okunabilir hale getirmek için ortak dil ortadan kalkar. Bu nedenle için fanlar temiz, basit kod, bu dil sürümü büyük bir kazanç oluştu.

Kendi içinde bir geleneksel dil özelliği olmasa da bu sürüm ile birlikte başka bir şey menülerin. Yayınlanmadan [Roslyn derleyici bir hizmet olarak](https://github.com/dotnet/roslyn). C# derleyicisi artık C# dilinde yazılmıştır ve derleyici, programlama çalışmalarınızın bir parçası olarak kullanabilirsiniz.

## <a name="c-version-70"></a>C# 7.0 sürümü

En son ana sürüm C# 7.0 sürümü var. Bu sürüm bazı gelişime ve harika şeyler damarlı C# 6.0, ancak derleyicinin bir hizmet olarak sahiptir. Yeni özelliklerden bazıları şunlardır:

- [Değişkenleri](./csharp-7.md#out-variables)
- [Diziler ve ayrıştırma](./csharp-7.md#tuples)
- [Desen eşleştirme](./csharp-7.md#pattern-matching)
- [Yerel işlevler](./csharp-7.md#local-functions)
- [Genişletilmiş ifade bodied üyeleri](./csharp-7.md#more-expression-bodied-members)
- [Ref yerel değerleri ve dönüşleri](./csharp-7.md#ref-locals-and-returns)

Diğer özellikler dahil:

- [Atar](./csharp-7.md#discards)
- [İkili sabit değerler ve basamak ayırıcılar](./csharp-7.md#numeric-literal-syntax-improvements)
- [Throw ifadeleri](./csharp-7.md#throw-expressions)

Tüm bu özellikler, geliştiricilerin ve hiç olmadığı kadar bile daha temiz bir kod yazma olanağı için harika yeni özellikleri sağlar. Bir Vurgu, bildirimi ile kullanılacak değişkenleri condensing `out` anahtar sözcüğü ve birden çok değer tanımlama grubu aracılığıyla sağlayarak.

Ancak, C# her zamankinden daha geniş kullanımına yerine koyulan. .NET core artık herhangi bir işletim sistemini hedefleyen ve taşınabilirlik ve bulut üzerinde kendi gözler sıkıca sahip.  Bu yeni özellikler, dil tasarımcıları düşüncelerinizi ve yeni özellikler yakında yanı sıra zaman kesinlikle kaplar.

_Makale_ [ _NDepend blogda ilk yayımlandığı_](https://blog.ndepend.com/c-versions-look-language-history/)_, Erik Dietrich ve Patrick Smacchia'nın._
