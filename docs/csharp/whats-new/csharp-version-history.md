---
title: C# tarihi - C# Rehberi
description: Dil ilk versiyonlarında nasıl dı ve o zamandan beri nasıl gelişti?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 9114395a5c6cfd8df5da18024921c35828947e0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399688"
---
# <a name="the-history-of-c"></a>C'nin tarihçesi\#

Bu makalede, C# dilinin her büyük sürümü bir tarihçesi sağlar. C# ekibi yenilik yapmaya ve yeni özellikler eklemeye devam ediyor. Gelecek sürümler için düşünülen özellikler de dahil olmak üzere ayrıntılı dil özelliği durumu, [GitHub'daki dotnet/roslyn deposunda](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) bulunabilir.

> [!IMPORTANT]
> C# dili, C# belirtiminin bazı özellikler için *standart kitaplık* olarak tanımladığı tür ve yöntemlere dayanır. .NET platformu bu tür ve yöntemleri çeşitli paketlerhalinde sunar. Bir örnek özel durum işlemedir. Atılan `throw` nesnenin türetildiğinden emin olmak için <xref:System.Exception>her deyim veya ifade denetlenir. Benzer şekilde, `catch` yakalanan türün <xref:System.Exception>türetilmiş olduğundan emin olmak için her kontrol edilir. Her sürüm yeni gereksinimler ekleyebilir. Eski ortamlardaki en son dil özelliklerini kullanmak için belirli kitaplıklar yüklemeniz gerekebilir. Bu bağımlılıklar, her belirli sürüm için sayfada belgelenmiştir. Bu bağımlılık la ilgili arka plan için [dil ve kitaplık arasındaki ilişkiler](relationships-between-language-and-library.md) hakkında daha fazla bilgi edinebilirsiniz.

C# yapı araçları, en son ana dil sürümünü varsayılan dil sürümünü dikkate alır. Bu bölümdeki diğer makalelerde ayrıntılı olarak ayrıntılı olarak büyük sürümler arasında nokta sürümleri olabilir. Bir nokta sürümündeki en son özellikleri kullanmak için [derleyici dili sürümünü yapılandırmanız](../language-reference/configure-language-version.md) ve sürümü seçmeniz gerekir. C# 7.0'dan bu yana üç nokta açıklaması olmuştur:

- [C# 7.3](csharp-7-3.md):
  - C# 7.3 Visual [Studio 2017 sürüm 15.7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ve [.NET Core 2.1 SDK](../../core/whats-new/dotnet-core-2-1.md)ile başlayan kullanılabilir.
- [C# 7.2](csharp-7-2.md):
  - C# 7.2 Visual [Studio 2017 sürüm 15.5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ve [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md)ile başlayan kullanılabilir.
- [C# 7.1](csharp-7-1.md):
  - C# 7.1 Visual [Studio 2017 sürüm 15.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ve [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md)ile başlayan kullanılabilir.

## <a name="c-version-10"></a>C# sürüm 1.0

Geri dönüp baktığınızda Visual Studio .NET 2002 ile piyasaya sürülen C# sürüm 1.0, Java'ya çok benziyordu. [ECMA için belirtilen tasarım hedeflerinin](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)bir parçası olarak, "basit, modern, genel amaçlı nesne yönelimli bir dil" olmaya çalıştı.  O zaman, Java gibi görünümlü bu erken tasarım hedeflerine ulaşmak anlamına geliyordu.

Ama şimdi C#1.0'a bakarsanız, başınız dönüyor. Bu yerleşik async yetenekleri ve bazı jenerik etrafında kaygan işlevselliği hafife almak yoktu. Aslına bakarsanız, jeneriklerden tamamen yoksundu.  Ve [LINQ?](../linq/index.md) Henüz mevcut değil. Bu eklemelerin çıkması birkaç yıl sürer.

C# sürüm 1.0 bugün ile karşılaştırıldığında, özellikleri elimden görünüyordu. Kendini biraz ayrıntılı kod yazarken bulursun. Ama yine de bir yerden başlamalısın. C# sürüm 1.0 Windows platformunda Java için uygun bir alternatif oldu.

C# 1.0'ın başlıca özellikleri şunlardır:

- [Sınıflar](../programming-guide/classes-and-structs/classes.md)
- [Yapılar](../language-reference/builtin-types/struct.md)
- [Arabirimler](../programming-guide/interfaces/index.md)
- [Olaylar](../events-overview.md)
- [Özellikler](../properties.md)
- [Temsilciler](../delegates-overview.md)
- [İfadeler](../programming-guide/statements-expressions-operators/expressions.md)
- [Deyimler](../programming-guide/statements-expressions-operators/statements.md)
- [Öznitelikler](../programming-guide/concepts/attributes/index.md)

## <a name="c-version-12"></a>C# sürüm 1.2

C# sürüm 1.2 Visual Studio .NET 2003 ile gönderildi. Bu dil için birkaç küçük geliştirmeler içeriyordu. En önemli olan, bu `foreach` sürümden başlayarak, <xref:System.IDisposable.Dispose%2A> bir <xref:System.Collections.IEnumerator> döngü <xref:System.Collections.IEnumerator> içinde <xref:System.IDisposable>oluşturulan kodun uygulandığı zaman çağrılmış olmasıdır.

## <a name="c-version-20"></a>C# sürüm 2.0

Şimdi işler ilginçolmaya başladı. Visual Studio 2005 ile birlikte 2005 yılında piyasaya sürülen C# 2.0'ın bazı önemli özelliklerine bir göz atalım:

- [Genel Türler](../programming-guide/generics/index.md)
- [Kısmi türleri](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Anonim yöntemler](../language-reference/operators/delegate-operator.md)
- [Nullable değer türleri](../language-reference/builtin-types/nullable-value-types.md)
- [Yineleyiciler](../programming-guide/concepts/iterators.md)
- [Kovaryans ve kontravaryans](../programming-guide/concepts/covariance-contravariance/index.md)

Diğer C# 2.0 özellikleri varolan özelliklere özellikler eklendi:

- Getter/ayarlayıcı ayrı erişilebilirlik
- Yöntem grubu dönüşümleri (temsilciler)
- Statik sınıflar
- Temsilci çıkarımı

C# genel bir Nesne Yönelimli (OO) dili olarak başlamış olsa da, C# sürüm 2.0 bunu aceleyle değiştirdi. Bir kez onların altında ayakları vardı, onlar bazı ciddi geliştirici ağrı noktaları sonra gitti. Ve önemli bir şekilde peşlerine düştüler.

Jeneriklerle, türleri ve yöntemleri hala tür güvenliğini korurken rasgele bir tür üzerinde çalışabilir. Örneğin, bu <xref:System.Collections.Generic.List%601> dizeleri `List<string>` veya `List<int>` tamsayılar üzerinde tür güvenli işlemleri gerçekleştirmenize veya bunları gerçekleştirirken izin veren bir işlem yapmak. Jenerik kullanmak, her `ListInt` işlem `ArrayList` `Object` için bu türde veya döküm oluşturmak daha iyidir.

C# sürüm 2.0 yineleyiciler getirdi. Kısa bir şekilde ifade etmek gerekirse, yineleyiciler bir `List` `foreach` döngü ile (veya diğer Sayısal olabilir türleri) tüm öğeleri incelemek sağlar. Dilin birinci sınıf bir parçası olarak yineleyicilere sahip olmak, dilin okunabilirliğini ve insanların kod hakkında muhakeme yeteneğini önemli ölçüde artırmıştır.

Ve yine de, C# Java ile yetişmek biraz oynamaya devam etti. Java zaten jenerik ve yineleyiciler dahil sürümleri yayımladı vardı. Ama diller ayrı gelişmeye devam ettikçe bu durum yakında değişecekti.

## <a name="c-version-30"></a>C# sürüm 3.0

C# sürüm 3.0, Visual Studio 2008 ile birlikte 2007'nin sonlarında geldi, ancak dil özelliklerinin tamamı aslında .NET Framework sürüm 3.5 ile gelecekti. Bu sürüm C# büyümesinde büyük bir değişiklik işaretledi. C#'ı gerçekten müthiş bir programlama dili olarak belirledi. Bu sürümdeki bazı önemli özelliklere bir göz atalım:

- [Otomatik uygulanan özellikler](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Anonim türleri](../programming-guide/classes-and-structs/anonymous-types.md)
- [Sorgu ifadeleri](../linq/query-expression-basics.md)
- [Lambda ifadeleri](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [İfade ağaçları](../expression-trees.md)
- [Uzatma yöntemleri](../programming-guide/classes-and-structs/extension-methods.md)
- [Örtülü olarak yazılan yerel değişkenler](../language-reference/keywords/var.md)
- [Kısmi yöntemler](../language-reference/keywords/partial-method.md)
- [Nesne ve toplama başharfleri](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

Geriye dönüp bakıldığında, bu özelliklerin çoğu hem kaçınılmaz hem de ayrılmaz görünüyor. Hepsi stratejik olarak birbirine uyuyor. Genellikle C# sürümünün öldürücü özelliğinin Dil-Tümleşik Sorgu (LINQ) olarak da bilinen sorgu ifadesi olduğu düşünülmektedir.

Daha nüanslı bir görünüm, linq'in üzerine inşa edildiği temel olarak ifade ağaçlarını, lambda ifadelerini ve anonim türlerini inceler. Ama, her iki durumda da, C # 3.0 devrimci bir kavram sundu. C# 3.0, C#'ı hibrit Nesne Yönelimli / İşlevsel bir dile dönüştürmek için zemin hazırlamaya başlamıştır.

Özellikle, şimdi diğer şeylerin yanı sıra, koleksiyonlar üzerinde işlemleri gerçekleştirmek için SQL tarzı, bildirimsel sorgular yazabilirsiniz. Tamsayılar listesinin ortalamasını hesaplamak için bir `for` döngü yazmak yerine, artık bunu basitçe `list.Average()`. Sorgu ifadeleri ve uzantı yöntemlerinin birleşimi, tamsayılar listesinin çok daha akıllı hale gelmiş gibi görünmesini sağladı.

İnsanların bu kavramı gerçekten kavramaları ve bütünleştirmeleri zaman aldı, ama yavaş yavaş bunu yaptılar. Ve şimdi, yıllar sonra, kod çok daha kısa, basit ve işlevseldir.

## <a name="c-version-40"></a>C# sürüm 4.0

Visual Studio 2010 ile yayımlanan C# sürüm 4.0, sürüm 3.0'ın çığır açan durumuna kadar yaşamakta zorlanmış olurdu. Sürüm 3.0 ile C# dili Java'nın gölgesinden sıkıca çıkarıp öne çıkarmıştı. Dil hızla zarif hale geliyordu.

Sonraki sürümü bazı ilginç yeni özellikler tanıtmak yaptı:

- [Dinamik bağlama](../language-reference/builtin-types/reference-types.md)
- [Adlandırılmış/isteğe bağlı bağımsız değişkenler](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Genel kovariant ve kontravariant](../../standard/generics/covariance-and-contravariance.md)
- [Gömülü interop türleri](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Gömülü interop türleri dağıtım acısını hafifletir. Genel covariance ve kontravariance jenerik kullanmak için daha fazla güç vermek, ama biraz akademik ve muhtemelen en çerçeve ve kütüphane yazarları tarafından takdir konum. Adlandırılmış ve isteğe bağlı parametreler, birçok yöntemin aşırı yüklenmelerini ortadan kaldırmanızı ve kolaylık sağlamanızı sağlar. Ama bu özelliklerin hiçbiri tam olarak paradigma değiştirici değildir.

En önemli özellik `dynamic` anahtar kelimenin tanıtımıydı. `dynamic` Anahtar kelime C# sürüm 4.0'a, derleme zamanı yazmada derleyiciyi geçersiz kılma özelliğine getirilmiştir. Dinamik anahtar sözcüğü kullanarak, JavaScript gibi dinamik olarak yazılmış dillere benzer yapılar oluşturabilirsiniz. Bir tane `dynamic x = "a string"` oluşturup sonra altı tane ekleyebilir ve bundan sonra ne olması gerektiğini sıralamak için çalışma süresine bırakabilirsiniz.

Dinamik bağlama, hata potansiyelinin yanı, aynı zamanda dil içinde büyük bir güç sağlar.

## <a name="c-version-50"></a>C# sürüm 5.0

Visual Studio 2012 ile yayımlanan C# sürüm 5.0, dilin odaklanmış bir versiyonuydu. Bu sürüm için neredeyse tüm çaba başka bir çığır `async` açan `await` dil kavramı gitti: ve model asynchronous programlama için.  İşte önemli özellikler listesi:

- [Eşkron üyeleri](../async.md)
- [Arayan bilgi öznitelikleri](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a>Ayrıca Bkz.

- [Kod Projesi: C# 5.0'da Arayan Bilgi Öznitelikleri](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Arayan bilgi özniteliği, bir ton ortak yansıma koduna başvurmadan çalıştırdığınız bağlam hakkında kolayca bilgi almanızı sağlar. Tanılama ve günlüğe kaydetme görevlerinde birçok kullanımı vardır.

Ama `async` `await` ve bu sürümün gerçek yıldız vardır. Bu özellikler 2012 yılında çıktığında, C# birinci sınıf bir katılımcı olarak dile asynchrony pişirerek oyunu tekrar değiştirdi. Uzun süren operasyonlar ve geri arama ağlarının uygulanması yla uğraştıysanız, muhtemelen bu dil özelliğini beğenmişsinizdir.

## <a name="c-version-60"></a>C# sürüm 6.0

3.0 ve 5.0 sürümleriyle C# nesne yönelimli bir dilde önemli yeni özellikler eklemişti. Visual Studio 2015 ile yayımlanan sürüm 6.0 ile baskın bir katil özelliği yapmaktan uzaklaşacak ve bunun yerine C# programlamayı daha üretken kılan daha küçük birçok özellik yayınlayacaktı. Bunlardan bazıları şunlardır:

- [Statik alma](./csharp-6.md#using-static)
- [Özel durum filtreleri](./csharp-6.md#exception-filters)
- [Otomatik özellik başlangıç layıcıları](./csharp-6.md#auto-property-initializers)
- [İfade gövdeli üyeleri](./csharp-6.md#expression-bodied-function-members)
- [Null propagator](./csharp-6.md#null-conditional-operators)
- [Dize ilişkilendirme](./csharp-6.md#string-interpolation)
- [operatörün adı](./csharp-6.md#the-nameof-expression)
- [Dizin başharfleri](csharp-6.md#extension-add-methods-in-collection-initializers)

Diğer yeni özellikler şunlardır:

- Catch/finally bloklarda bekleyin
- Yalnızca getör özellikleri için varsayılan değerler

Bu özelliklerin her biri kendi başına ilginçtir. Ama onlara tamamen bakarsanız, ilginç bir model görürsünüz. Bu sürümde, C# kodu daha ters ve okunabilir hale getirmek için dil kazan plakaortadan kaldırıldı. Yani temiz, basit kod hayranları için, bu dil sürümü büyük bir galibiyet oldu.

Kendi içinde geleneksel bir dil özelliği olmasa da, bu sürümü ile birlikte başka bir şey yaptı. Onlar [Roslyn bir hizmet olarak derleyici](https://github.com/dotnet/roslyn)yayımladı. C# derleyicisi artık C#ile yazılmıştır ve derleyiciyi programlama çabanızın bir parçası olarak kullanabilirsiniz.

## <a name="c-version-70"></a>C# sürüm 7.0

En son ana versiyonu C# sürüm 7.0, Visual Studio 2017 ile piyasaya sürüldü. Bu sürüm c # 6.0 damar bazı evrimsel ve serin şeyler, ancak bir hizmet olarak derleyici olmadan vardır. Yeni özelliklerden bazıları şunlardır:

- [Çıkış değişkenleri](./csharp-7.md#out-variables)
- [Tuples ve yapısızlaştırma](./csharp-7.md#tuples)
- [Desen eşleştirme](./csharp-7.md#pattern-matching)
- [Yerel işlevler](./csharp-7.md#local-functions)
- [Genişletilmiş ifade gövdeli üyeleri](./csharp-7.md#more-expression-bodied-members)
- [Ref yerlileri ve döner](./csharp-7.md#ref-locals-and-returns)

Diğer özellikler şunlardır:

- [Atılanlar](./csharp-7.md#discards)
- [İkili Edebi ve Basamak Ayırıcılar](./csharp-7.md#numeric-literal-syntax-improvements)
- [Throw ifadeleri](./csharp-7.md#throw-expressions)

Tüm bu özellikler geliştiriciler için serin yeni yetenekler ve her zamankinden daha temiz kod yazmak için fırsat sunuyoruz. Vurgu, anahtar kelimeyle birlikte kullanılacak değişkenlerin `out` bildirimini yoğunlaştırmak ve tuple üzerinden birden çok iade değerine izin vermektir.

Ama C# daha geniş bir kullanıma sokuluyor. .NET Core artık herhangi bir işletim sistemini hedef alıyor ve gözünü bulutta ve taşınabilirliğe dikti.  Bu yeni yetenekler kesinlikle dil tasarımcılarının düşünce ve zaman işgal, yeni özellikler ile geliyor ek olarak.

_Makale_ [_aslında NDepend blogunda yayınlanan_](https://blog.ndepend.com/c-versions-look-language-history/), Erik_Dietrich ve Patrick Smacchia nezaket._
