---
title: .NET Turu
description: .NET'in öne çıkan özelliklerinden bazıları arasında rehberli bir tur.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: 61d4792b1f1b92dd59442ee38810da96c6cf63bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241149"
---
# <a name="tour-of-net"></a>.NET Turu

.NET genel amaçlı bir geliştirme platformudur. Birden çok programlama dili desteği, eşzamanlı ve eşzamanlı programlama modelleri ve birden çok platformda çok çeşitli senaryolar sağlayan yerel birlikte çalışabilirlik gibi çeşitli temel özelliklere sahiptir.

Bu makalede, .NET'in bazı temel özellikleri arasında rehberli bir tur sunulmaktadır. .NET'in mimari parçaları ve ne için kullanıldıkları hakkında bilgi edinmek için [.NET Mimari Bileşenler](components.md) konusuna bakın.

## <a name="how-to-run-the-code-samples"></a>Kod örnekleri nasıl çalıştırılabilen

Kod örneklerini çalıştırmak için bir geliştirme ortamının nasıl ayarlan gerektiğini öğrenmek için [Başlarken](get-started.md) konusuna bakın. Bu sayfadaki kod örneklerini yürütmek için ortamınıza kopyalayın ve yapıştırın.

## <a name="programming-languages"></a>Programlama dilleri

.NET birden çok programlama dilini destekler. .NET uygulamaları, diğer şeylerin yanı sıra dilden bağımsız çalışma süresi ve dil birlikte çalışabilirliği belirten [Ortak Dil Altyapısını (CLI)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)uygular. Bu, .NET'te uygulama ve hizmet oluşturmak için herhangi bir .NET dilini seçtiğiniz anlamına gelir.

Microsoft, C#, F#ve Visual Basic olmak üzere üç .NET dili etkin bir şekilde geliştirir ve destekler.

* C# basit, güçlü, tür güvenli ve nesne yönelimli, C tarzı dillerin ifade ve zarafetini korurken. C ve benzeri dillere aşina olan herkes C#'a uyum sağlamada birkaç sorun bulur. C# hakkında daha fazla bilgi edinmek için [C# Kılavuzu'na](../csharp/index.yml) göz atın.

* F# aynı zamanda geleneksel nesne yönelimli ve zorunlu programlama destekleyen bir çapraz platform, işlevsel-ilk programlama dilidir. F# hakkında daha fazla bilgi edinmek için [F# Kılavuzu'na](../fsharp/index.yml) göz atın.

* Visual Basic, .NET'te çalışan çeşitli uygulamalar oluşturmak için kullandığınızı öğrenmek için kolay bir dildir. .NET dilleri arasında Visual Basic'in sözdizimi sıradan insan diline en yakın dildir ve bu da yazılım geliştirmeye yeni katılan kişilerin işini kolaylaştırır.

## <a name="automatic-memory-management"></a>Otomatik bellek yönetimi

.NET, programlar için otomatik bellek yönetimi sağlamak için [çöp toplama (GC)](garbage-collection/index.md) kullanır. GC bellek yönetimi için tembel bir yaklaşım üzerinde çalışır, bellek hemen toplama uygulama iş kısmını tercih. .NET GC hakkında daha fazla bilgi edinmek için [çöp toplamanın temellerine (GC)](garbage-collection/fundamentals.md)göz atın.

Aşağıdaki iki satır her ikisi de bellek ayırır:

[!code-csharp[MemoryManagement](../../samples/snippets/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Çöp toplayıcısı zamanlanan çalışmasıyla belleği geri aldığında ayırma yı otomatik olarak gerçekleştiğinden, belleği ayırmayı ayırmak için benzer bir anahtar kelime yoktur.

Çöp toplayıcı bellek *güvenliğini*sağlamaya yardımcı olan hizmetlerden biridir. Program, yalnızca ayrılmış belleğe erişiyorsa bellek teredir. Örneğin, çalışma süresi, bir uygulamanın bir dizi sınırlarının ötesinde tahsis edilmemiş belleğe erişmemesini sağlar.

Aşağıdaki örnekte, çalışma zamanı bellek <xref:System.IndexOutOfRangeException> güvenliğini zorlamak için bir özel durum atar:

[!code-csharp[MemoryManagement](../../samples/snippets/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Yönetilmeyen kaynaklarla çalışma

Bazı nesneler *yönetilmeyen kaynaklara*başvurur. Yönetilmeyen kaynaklar, .NET çalışma zamanı tarafından otomatik olarak korunmayan kaynaklardır. Örneğin, dosya işlemiş, yönetilmeyen bir kaynaktır. Nesne <xref:System.IO.FileStream> yönetilen bir nesnedir, ancak yönetilmeyen bir dosya işlemesi başvurur. <xref:System.IO.FileStream>'yi kullanmayı bitirdiğinizde, dosya tutamacını serbest bırakmanız gerekir.

.NET'te, yönetilmeyen kaynaklara başvuran <xref:System.IDisposable> nesneler arabirimi uygular. Nesneyi kullanmayı bitirdiğinizde, yönetilmeyen kaynakları serbest <xref:System.IDisposable.Dispose> bırakmakla sorumlu olan nesnenin yöntemini çağırırsınız. .NET dilleri, [ `using` ](../csharp/language-reference/keywords/using.md) aşağıdaki örnekte gösterildiği gibi, bu tür nesneler için uygun bir ifade sağlar:

[!code-csharp[UnmanagedResources](../../samples/snippets/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

Blok tamamlandıktan sonra,.NET çalışma süresi otomatik `stream` olarak <xref:System.IDisposable.Dispose> nesnenin dosya tutamacını serbest bırakan yöntemini çağırır. `using` Bir özel durum denetimin bloktan ayrılmasına neden oluyorsa çalışma zamanı da bunu yapar.

Daha fazla bilgi için aşağıdaki konulara bakın:

* C# [için, kullanarak Deyim (C# Reference)](../csharp/language-reference/keywords/using-statement.md) konusuna bakın.
* F# için kaynak [yönetimi: Anahtar kelimeyi kullanın.](../fsharp/language-reference/resource-management-the-use-keyword.md)
* Visual Basic [için, Kullanma Bildirimi (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) konusuna bakın.

## <a name="type-safety"></a>Tip güvenliği

Nesne, belirli bir türörneğidir. Belirli bir nesne için izin verilen işlemler yalnızca türünden işlemlerdir. Bir `Dog` tür `Jump` ve `WagTail` yöntemler olabilir, ancak bir `SumTotal` yöntem. Program yalnızca belirli bir türe ait yöntemleri çağırır. Diğer tüm aramalar derleme zamanı hatası na veya çalışma süresi özel durumuyla sonuçlanır `object`(dinamik özellikler kullanılması veya kullanılması durumunda).

.NET dilleri taban ve türemiş sınıfların hiyerarşileri ile nesne yönelimli. .NET çalışma süresi yalnızca nesne dökümlerine ve nesne hiyerarşisiyle hizalayan çağrılara izin verir. Herhangi bir .NET dilinde tanımlanan her türün <xref:System.Object> temel türden türediğini unutmayın.

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Tür güvenliği, erişimci anahtar kelimelerin doğruluklarını garanti ederek kapsüllemenin uygulanmasına yardımcı olmak için de kullanılır. Erişimveya anahtar kelimeler, belirli bir türün üyelerine diğer kodlara göre erişimi kontrol eden yapılardır. Bunlar genellikle davranışını yönetmek için kullanılan bir tür içinde çeşitli veri türleri için kullanılır.

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, Visual Basic ve F# yerel *tür çıkarımlarını*destekler. Tür çıkarımı, derleyicinin sol taraftaki ifadetürünü sağ taraftaki ifadeden çıkardığı anlamına gelir. Bu, tür güvenliğinin kırıldığı veya kaçındığı anlamına gelmez. Ortaya çıkan tür ima her şeyi ile güçlü bir türü var. Önceki örnekten, `dog` tür çıkarımını tanıtmak için yeniden yazılır ve örneğin geri kalanı değişmeden:

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F# C# ve Visual Basic'te bulunan yöntem-yerel tür çıkarımLarından daha fazla tür çıkarımı yeteneğine sahiptir. Daha fazla bilgi için Bkz. [Tür Çıkarımı.](../fsharp/language-reference/type-inference.md)

## <a name="delegates-and-lambdas"></a>Temsilciler ve lambda ifadeleri

Bir temsilci yöntem imzasıyla temsil edilir. Bu imzaile herhangi bir yöntem temsilciatanabilir ve temsilci çağrıldığınızda yürütülür.

Temsilciler, yazının güvenli olması dışında C++ işlev işaretçileri gibidir. CLR tipi sistemde bir tür bağlantısız yöntem. Düzenli yöntemler bir sınıfa eklenir ve yalnızca statik veya örnek çağrı kuralları aracılığıyla doğrudan çağrılabilir.

.NET'te, temsilciler genellikle olay işleyicilerinde, asenkron işlemleri tanımlamada ve LINQ'un temel taşı olan lambda ifadelerinde kullanılır. Delegeler ve [lambdas](delegates-lambdas.md) konusu hakkında daha fazla bilgi edinin.

## <a name="generics"></a>Genel Türler

Genel ler, programcının sınıflarını tasarlarken istemci kodunun (türdeki kullanıcılar) tür parametresi yerine tam olarak kullanılacak türü belirtmesine olanak tanıyan bir *tür parametresi* tanıtmasına olanak tanır.

Programcıların genel veri yapılarını uygulamasına yardımcı olmak için genel bilgiler eklendi. Gelmelerinden önce, `List` tür gibi bir tür gibi bir tür için genel olması için, `object`türü olan öğelerle çalışması gerekir. Bu çeşitli performans ve anlamsal sorunlar, birlikte olası ince çalışma zamanı hataları vardı. Ortak bir çalışma zamanı hatası, bir veri yapısının örneğin, hem tamsayılar hem <xref:System.InvalidCastException> de dizeleri içerdiği ve listenin üyelerini işlerken bir atTırışolmasıdır.

Aşağıdaki örnek, türlerin bir örneğini <xref:System.Collections.Generic.List%601> kullanarak çalışan temel bir programı gösterir:

[!code-csharp[GenericsShort](../../samples/snippets/csharp/snippets/tour/GenericsShort.csx)]

Daha fazla bilgi için [Genel türler (Genel Bilgiler) genel bakış](generics.md) konusuna bakın.

## <a name="async-programming"></a>Async programlama

Async programlama çalışma zamanı, çerçeve kitaplıkları ve .NET dil yapıları async desteği ile .NET içinde birinci sınıf bir kavramdır. Dahili olarak, G/Ç'ye bağlı `Task`işleri mümkün olduğunca verimli bir şekilde gerçekleştirmek için işletim sisteminden yararlanan nesnelere (örneğin) dayanırlar.

.NET'te async programlama hakkında daha fazla bilgi edinmek için [Async genel bakış](async.md) konusuyla başlayın.

## <a name="language-integrated-query-linq"></a>Dil ile Tümleşik Sorgu (LINQ)

LINQ, C# ve Visual Basic için, verileri işletmek için basit, bildirimsel kod yazmanızı sağlayan güçlü bir özellik kümesidir. Veriler birçok formda (bellek nesneleri, SQL veritabanı veya XML belgesi gibi) olabilir, ancak yazdığınız LINQ kodu genellikle veri kaynağına göre farklılık gösterir.

Daha fazla bilgi edinmek ve bazı örnekleri görmek için [LINQ (Language Integrated Query)](using-linq.md) konusuna bakın.

## <a name="native-interoperability"></a>Native ile birlikte çalışma

Her işletim sistemi, sistem hizmetleri sağlayan bir uygulama programlama arabirimi (API) içerir. .NET, bu API'leri aramak için çeşitli yollar sağlar.

Yerel birlikte çalışabilirlik yapmanın ana yolu, Linux ve Windows platformlarında desteklenen "platform invoke" veya kısaca P/Invoke üzerinden dir. Yerel birlikte çalışabilirlik yapmanın yalnızca Windows'a özgü bir yolu, yönetilen koddaki [COM bileşenleriyle](/cpp/atl/introduction-to-com) çalışmak için kullanılan "COM interop" olarak bilinir. P/Invoke altyapısının üzerine inşa edilmiştir, ancak kurnazca farklı şekillerde çalışır.

Mono's (ve böylece Xamarin's) Java ve Objective-C için birlikte çalışabilirlik desteği çoğu benzer inşa edilmiştir, yani, onlar aynı ilkeleri kullanın.

Yerel birlikte çalışabilirlik hakkında daha fazla bilgi için Yerel [birlikte çalışabilirlik](native-interop/index.md) makalesine bakın.

## <a name="unsafe-code"></a>Güvenli olmayan kod

Dil desteğine bağlı olarak, CLR yerel belleğe erişmenizi `unsafe` ve kod aracılığıyla işaretçi aritmetik yapmanızı sağlar. Bu işlemler belirli algoritmalar ve sistem birlikte çalışabilirliği için gereklidir. Güçlü olmasına rağmen, sistem API'leri ile interop veya en verimli algoritmauygulamak için gerekli olmadığı sürece güvenli olmayan kod kullanımı önerilmez. Güvenli olmayan kod farklı ortamlarda aynı şekilde yürütülmeyebilir ve çöp toplayıcısı ve tür güvenliğinin avantajlarını da kaybeder. Güvenli olmayan kodu mümkün olduğunca sınırlamak ve merkezileştirmek ve bu kodu iyice test etmek önerilir.

Aşağıdaki örnek, `ToString()` `StringBuilder` yöntemin sınıftan değiştirilmiş bir sürümüdür. Kod kullanmanın, `unsafe` bellek yığınları arasında doğrudan hareket ederek bir algoritmayı nasıl verimli bir şekilde uygulayabileceğini gösterir:

[!code-csharp[Unsafe](../../samples/snippets/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Sonraki adımlar

C# özelliklerinin bir turuyla ilgileniyorsanız, [Tour of C# bölümüne](../csharp/tour-of-csharp/index.md)göz atın.

F# özellikleriyle dolu bir turla ilgileniyorsanız, [F# Turu'na](../fsharp/tour.md)bakın.

Kendi kodunuzu yazmaya başlamak istiyorsanız, [Başlarken'i](get-started.md)ziyaret edin.

.NET'in önemli bileşenleri hakkında bilgi edinmek için [.NET Mimari Bileşenlerbölümüne](components.md)göz atın.
