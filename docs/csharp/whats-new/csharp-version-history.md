---
title: C# - C# Kılavuzu geçmişi
description: Ne dil görünüm erken sürümlerde düşüncelerinizi ve nasıl itibaren gelişmiştir?
keywords: Yenilikler, C#, .NET, .NET Core, C# geçmişi
author: erikdietrich
ms.author: wiwagn
ms.date: 09/20/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 0a24e8cf22bb8350777879a3adfd2757b89cd305
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="the-history-of-c"></a>C# geçmişi #

Ne dil görünüm kendi erken incarnations düşüncelerinizi? Ve nasıl itibaren yıllarda gelişmiştir?

## <a name="c-version-10"></a>C# sürüm 1.0

Geri dönün ve arayın, C# sürüm 1.0 Java gibi çok Aranan. Olarak [belirtilen Tasarım hedeflerini ECMA için parçası](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), bir "basit, modern, genel amaçlı nesne yönelimli dili." olarak aranan  Aynı anda Java anlamına gelir gibi arayan bu erken tasarım hedefleri elde.

Ancak geri C# 1.0 şimdi bakarsanız, kendiniz biraz dizzy bulur. Yerleşik zaman uyumsuz özellikler ve bazı biz verilen ederiz genel türler geçici tıklatmanız işlevlerini olmadığı. Gibi bir matter, gerçekte, bu genel türler tamamen olmadığı.  Ve [LINQ](../linq/index.md)? Mevcut değil henüz. Piyasaya çıkmasını bazı yıl sürer.

C# sürüm 1.0 için bugün karşılaştırıldığında özelliklerinin kırpılmış arama. Kendiniz ayrıntılı biraz kod yazmaya bulur. Ancak henüz bir yere başlatmak gerekir. C# sürüm 1.0 Windows platformunda uygun bir alternatif Java için oluştu.

## <a name="c-version-20"></a>C# sürüm 2.0

Şimdi ilginç almak şeyler başlatın. Bir C# 2005, Visual Studio 2005 ile birlikte yayımlanan 2.0, önemli özelliklerinden bazıları bakalım:

- [Genel Türler](../programming-guide/generics/index.md)
- [Kısmi türler](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Anonim yöntemler](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Boş değer atanabilir türler](../programming-guide/nullable-types/index.md)
- [Yineleyiciler](../programming-guide/concepts/iterators.md)
- [Kovaryans ve kontravaryans](../programming-guide/concepts/covariance-contravariance/index.md)

C# oldukça genel Object-Oriented (OO) dili olarak başlatılmamış olabilir, ancak C# sürüm 2.0, Aceleniz değiştirildi. Bunları altında kendi ayak sahip oldukları sonra bunların bazı önemli Geliştirici kalınan sonra geçti. Ve bunlardan sonra büyük bir biçimde oluştu.

Genel türler ile türleri ve rasgele bir türü hala tür güvenliği korurken çalışabilir yöntemleri vardır. Bu nedenle, örneğin, sahip bir <xref:System.Collections.Generic.List%601> sahip olanak sağlayan `List<string>` veya `List<int>` ve bunları yineleme sırada türü güvenli bu dizeler veya tamsayılar işlemleri. Bu oluşturmaktan daha iyidir `ListInt` notlar veya atama gelen `Object` her işlem için.

C# duruma sürüm 2.0 yineleyiciler. Temellerini koymak için bu, öğelerinde yinelemek sağlar bir `List` (veya diğer numaralandırılabilir türleri) ile bir `foreach` döngü. Bu dil birinci sınıf bir parçası olarak önemli ölçüde sahip dil ve neden kodu hakkında kişilerin yeteneği okunabilirliğini geliştirilmiştir.

Ve henüz, C# biraz Java ile nım çalınmaya devam eder. Java zaten genel türler ve yineleyiciler dahil sürümleri yayımlanan. Ancak, yakında parçalayın gelişmeye devam diller olarak değiştirir.

## <a name="c-version-30"></a>C# 3.0 sürümü

Dil özelliklerinin tam bot gerçekte .NET Framework sürüm 3.5 gelecektir rağmen C# 3.0 sürümü geç 2007'de, Visual Studio 2008 birlikte geldi. Bu sürüm, C# büyümesini önemli bir değişiklik olarak işaretlenmiş. Bu C# kurdu gerçekten formidable bir programlama dili olarak. Bir önemli özelliklerinden bazıları bu sürümde bakalım:

- [Otomatik uygulanan özellikler](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Anonim türler](../programming-guide/classes-and-structs/anonymous-types.md)
- [Sorgu ifadeleri](../linq/query-expression-basics.md)
- [lambda ifadesi](https://www.daedtech.com/introduction-to-c-lambda-expressions/)
- [İfade ağaçları](https://blogs.msdn.microsoft.com/charlie/2008/01/31/expression-tree-basics/)
- [Genişletme yöntemleri](https://www.codeproject.com/Tips/709310/Extension-Method-In-Csharp)

Baktýðýmýzda, bu özelliklerin çoğunu kaçınılmaz ve inseparable gibi görünüyor. Bunların tümü birlikte stratejik uygun. Bu genellikle C# sürümün geliştirilen müthiş özelliği sorgu ifadesi olarak da bilinen dil ile tümleşik sorgu (LINQ) olan düşünüldüğü.

Daha fazla nuanced görünüm bağlı LINQ oluşturulan temel olarak ifade tress, lambda ifadeleri ve anonim türler inceler. Ancak, her iki durumda da, C# 3.0 devrim niteliğinde bir kavram sunulur. C# 3.0 başlamış C# nesne yönelimli karma kapatma için önlemlerini / işlevsel dili.

Özellikle, artık SQL stili, başka şeylerin koleksiyonlar üzerinde işlem gerçekleştirmek için bildirim temelli sorgular yazabilirsiniz. Yazma yerine bir `for` tamsayı listesi ortalamayı hesaplamak için döngü, artık, olabildiğince basit bir şekilde yapabilirsiniz, olarak `list.Average()`. Sorgu ifadeleri ve genişletme yöntemleri birleşimi tamsayılar listesini tüm çok daha akıllı onayınızı ancak gibi görünmesi yapılan.

Gerçekten kavramak ve kavram tümleştirmek kişiler için zaman aldı, ancak aşamalı olarak menülerin. Ve artık yıl daha sonra çok daha kısa, basit ve işlevsel kodudur.

## <a name="c-version-40"></a>C# sürüm 4.0

Ve C# sürüm 4.0 sürüm 3.0 temel durumuna yaşayan zor bir süre beklendiğinden. Sürüm 3.0 C# dili sıkıca out Java ve teklifleriyle içine gölge taşınmıştır. Dil hızla Zarif olma.

Bir sonraki sürümünün ilginç bazı yeni özellikler tanıtmaktadır:

- [Dinamik bağlama](../language-reference/keywords/dynamic.md)
- [Adlı/isteğe bağlı bağımsız değişkenler](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Genel eşdeğişken ve karşıtı](../../standard/generics/covariance-and-contravariance.md)
- [Katıştırılmış birlikte çalışma türleri](https://stackoverflow.com/questions/20514240/whats-the-difference-setting-embed-interop-types-true-and-false-in-visual-studi)

Katıştırılmış birlikte çalışma türlerini dağıtım sorunları alleviated. Genel türlerde Kovaryans ve kontravaryans genel türler kullanmak için daha fazla güç sağlar, ancak biraz akademik ve büyük olasılıkla en takdir framework ve kitaplık yazarlar tarafından. Adlandırılmış ve isteğe bağlı parametreleri, birçok yöntemi aşırı ortadan kaldırmak ve kolaylık sağlamak olanak tanır. Ancak bu özellikleri hiçbiri tam olarak kip değiştirme.

Önemli özellik sunulması oldu `dynamic` anahtar sözcüğü. `dynamic` Anahtar sözcüğü sunulan C# diline sürüm 4.0 derleme zamanı yazarak üzerinde derleyici geçersiz kılma yeteneği. Dynamic anahtar kullanarak, yapıları JavaScript gibi dinamik olarak yazılan diller için benzer oluşturabilirsiniz. Oluşturabileceğiniz bir `dynamic x = "a string"` ve altı, sonraki yapılması gerekenleri çıkışı sıralamak için çalışma zamanı kadar bırakarak ekleyin.

Bu, olası hatalar, ancak aynı zamanda dil içinde harika güç sağlar.

## <a name="c-version-50"></a>C# sürüm 5.0

C# sürüm 5.0 çok odaklanmış bir dil sürümünü oluştu. Neredeyse tüm çaba bu sürüm için başka bir temel dil kavram geçti.  Önemli özelliklerin listesi aşağıda verilmiştir:

- [Zaman uyumsuz üyeleri](../async.md)
- [Arayan bilgileri öznitelikleri](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Arayan bilgileri özniteliğinin kolayca Demirbaş yansıma kod ton için başvurmadan çalıştırıyorsanız bağlamı hakkında bilgi almak olanak sağlar. Tanılama ve günlük görevlerini birçok kullanımı vardır.

Ancak `async` ve `await` bu sürümü gerçek yıldız şunlardır. 2012'de bu özellikler ortaya çıktığında, C# oyunu yeniden birinci sınıf Katılımcısı olarak dile asynchrony fırında tarafından pişirme değiştirildi. Şimdiye kadar uzun süre çalışan işlemleri ve geri çağırmaları webs uyarlamasını ele varsa, bu dil özelliği'de severek.

## <a name="c-version-60"></a>C# sürüm 6.0

3.0 ve 5.0 sürümleri ile C# etkileyici bazı özellikleri bir nesne yönelimli dilde eklenen. Sürüm 6.0, baskın geliştirilen müthiş bir özellik yapılması uzağa doğru gidin ve bunun yerine dil kullanıcılarının mutlu birçok özellik sürüm. Bunlardan bazıları şunlardır:

- [Statik içeri aktarmalar](../language-reference/keywords/using-static.md)
- [Özel durum filtreleri](https://www.thomaslevesque.com/2015/06/21/exception-filters-in-c-6/)
- [Özellik başlatıcıları](http://geekswithblogs.net/WinAZ/archive/2015/06/30/whatrsquos-new-in-c-6.0-auto-property-initializers.aspx)
- [İfade bodied üyeleri](https://lostechies.com/jimmybogard/2015/12/17/c-6-feature-review-expression-bodied-function-members/)
- [Null yayılması](https://davefancher.com/2014/08/14/c-6-0-null-propagation-operator/)
- [Dize ilişkilendirme](../language-reference/tokens/interpolated.md)
- [nameof işleci](https://stackoverflow.com/questions/31695900/what-is-the-purpose-of-nameof)
- [Sözlük Başlatıcı](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md)

Bu özelliklerin her biri kendi sağ ilginç olacaktır. Ancak onları tamamen bakarsanız, ilginç bir desen görürsünüz. Bu sürümde, C# dili Demirbaş kod daha kısa ve okunabilir hale ortadan. Bu nedenle için fanlar temiz, basit kod, bu dil sürümü büyük kazanım oluştu.

Kendi içinde bir geleneksel dil özelliği olmasa da bu sürüm ile birlikte bir diğer şey menülerin. Bunlar serbest [Roslyn bir hizmet olarak derleyici](https://github.com/dotnet/roslyn). C# Derleyici şimdi C# dilinde yazılmıştır ve derleyici programlama çabalarınız bir parçası olarak kullanabilirsiniz.

## <a name="c-version-70"></a>C# sürüm 7.0

C# sürüm 7.0 son ana sürümle olur. Bu sürüm bazı Açılım ve seyrek erişimli stuff C# 6. 0, ancak derleyici damarlı bir hizmet olarak sahiptir. Yeni özelliklerden bazıları şunlardır:

- [Değişkenleri](http://www.c-sharpcorner.com/article/out-variables-in-c-sharp-7-0/)
- [Diziler ve deconstruction](https://www.thomaslevesque.com/2016/08/23/tuple-deconstruction-in-c-7/)
- [Desen eşleştirme](./csharp-7.md#pattern-matching)
- [Yerel işlevler](http://www.infoworld.com/article/3182416/application-development/c-7-in-depth-exploring-local-functions.html)
- [Genişletilmiş ifade bodied üyeleri](./csharp-7.md#more-expression-bodied-members)
- [Ref Yereller ve döndürür](./csharp-7.md#ref-locals-and-returns)

Bu özelliklerin tümü, geliştiriciler ve zamankinden bile temizleyici kod yazmak için Fırsat için harika yeni özellikler sunar. Vurgu ile kullanılacak değişkenleri bildirimi condensing `out` anahtar sözcüğü ve tanımlama grubu aracılığıyla birden çok dönüş değerleri sağlayarak.

Ancak, C# her zamankinden daha geniş kullanmak koyulmuş. .NET core artık herhangi bir işletim sistemini hedefleyen ve onun gözler sıkıca taşınabilirlik ve bulut üzerinde sahiptir.  Bu kesinlikle dil tasarımcıları düşüncelerinizi ve yeni özelliklerle yaklaşan yanı sıra zaman kaplar.

_Makale_ [ _ilk NDepend blogunda yayımlandığı_](https://blog.ndepend.com/c-versions-look-language-history/)_, Erik Dietrich ve Can Smacchia'nın._
