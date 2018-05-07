---
title: .NET turu
description: Kılavuzlu Tur .NET belirgin özelliklerinden bazıları aracılığıyla.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: b1925397fb7cad5e55f992feaa5be2e2d837aac8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="tour-of-net"></a>.NET turu

.NET genel amaçlı geliştirme platformudur. Birden fazla programlama dilleri, zaman uyumsuz ve eş zamanlı programlama modelleri ve yerel birlikte çalışabilirliği, birden çok platform genelinde kadar çeşitli senaryoları etkinleştirmek için destek gibi çeşitli önemli özellikler vardır.

Bu makalede Kılavuzlu Tur .NET önemli özelliklerinden bazıları aracılığıyla sunulur. Bkz: [.NET Mimari Bileşenleri](components.md) .NET ve kullanıldıkları mimari parçalarını hakkında bilgi edinmek için konu.

## <a name="how-to-run-the-code-samples"></a>Kod örnekleri çalıştırma

Kod örnekleri çalıştırmak için bir geliştirme ortamını ayarlama hakkında bilgi edinmek için bkz: [Başlarken](get-started.md) konu. Kopyalayın ve bunları yürütmek için ortamınıza kod örnekleri bu sayfadan yapıştırın. 

## <a name="programming-languages"></a>Programlama dilleri

.NET birden fazla programlama dili destekler. .NET uygulamaları uygulamak [ortak dil altyapısı (CLI)](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/), başka şeylerin bir dilden bağımsız çalışma zamanı ve dil birlikte çalışabilirliği belirtir. Başka bir deyişle, .NET uygulamaları ve hizmetleri oluşturmak için herhangi bir .NET dil seçin.

Microsoft etkin şekilde geliştirir ve üç .NET dilleri desteklemektedir: C#, F # ve Visual Basic (VB). 

* C# C stili dillerin şıklık ve anlamlılık korurken basit, güçlü, tür kullanımı uyumlu, nesne yönelimli ise. C ve benzer dillerle tanıdık herkes, birkaç sorunları C# uyarlama içinde bulur. Kullanıma [C# Kılavuzu](../csharp/index.md) C# hakkında daha fazla bilgi için.

* F # de Geleneksel nesne yönelimli ve kesinlik temelli programlama destekleyen bir platformlar arası, ilk programlama dilidir. Kullanıma [F # Kılavuzu](../fsharp/index.md) F # hakkında daha fazla bilgi için.

* Visual Basic .NET üzerinde çalışan uygulamalar, çeşitli oluşturmak için kullandığınız öğrenmek için kolay bir dildir. .NET dillerinden arasında VB sözdizimi genellikle kişiler için yazılım geliştirme için yeni kolaylaştırarak sıradan İnsan dil en yakın olan.

## <a name="automatic-memory-management"></a>Otomatik bellek yönetimi

.NET kullanan [çöp toplama (GC)](garbagecollection/index.md) programları için otomatik bellek yönetimi sağlamak için. Bellek yönetimi, yavaş bir yaklaşım uygulama işleme bellek hemen koleksiyona tercih ederek GC çalıştırır. .NET GC hakkında daha fazla bilgi için kullanıma [çöp toplama (GC) Temelleri](garbagecollection/fundamentals.md).

Aşağıdaki iki satırı hem bellek:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Ne zaman atık toplayıcı zamanlanmış çalıştırılmasında aracılığıyla bellek kaldırsa ayırmayı otomatik olarak gerçekleştirilir gibi bellek XML'deki ayırmak için benzer anahtar sözcük yoktur.

Çöp toplayıcı sağlamaya yardımcı olmak Hizmetleri biri *bellek güvenliği*. Bellek eriştiği güvenli yalnızca bellek tahsis bir programdır. Örneğin, bir uygulama bir dizi sınırlarının ayrılmamış belleğe erişim değil çalışma zamanı sağlar.

Aşağıdaki örnekte, çalışma zamanı oluşturur bir `InvalidIndexException` bellek güvenliği zorlamak için özel durum:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Yönetilmeyen kaynaklar ile çalışma

Bazı nesneler başvuru *yönetilmeyen kaynakları*. Yönetilmeyen kaynaklar .NET çalışma zamanı tarafından otomatik olarak korunmaz kaynaklardır. Örneğin, bir dosya tanıtıcısı yönetilmeyen bir kaynaktır. A <xref:System.IO.FileStream> nesnesi yönetilen bir nesnedir, ancak yönetilmeyen bir dosya tanıtıcısı başvuruyor. Bitirdiğinizde kullanarak <xref:System.IO.FileStream>, dosya tanıtıcısı sürüm gerekir.

Yönetilmeyen kaynakları başvuru nesneleri, .NET uygulama <xref:System.IDisposable> arabirimi. Bitirdiğinizde nesnesini kullanarak, nesnenin çağrı <xref:System.IDisposable.Dispose> yönetilmeyen kaynakları serbest bırakma için sorumlu yöntemi. .NET dillerinden sağlamak kullanışlı `using` sözdizimi aşağıdaki örnekte gösterildiği gibi bu tür nesneleri için:

[!code-csharp[UnmanagedResources](../../samples/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

Bir kez `using` bloğu tamamlandıktan, .NET çalışma zamanı otomatik olarak çağırır `stream` nesnenin <xref:System.IDisposable.Dispose> dosya tanıtıcısı serbest yöntemi. Çalışma zamanı, bir özel denetim bloğu bırakın neden olursa da yapar.

Daha fazla ayrıntı için aşağıdaki konulara bakın:

* C# için bkz: [using deyimi (C# Başvurusu)](../csharp/language-reference/keywords/using-statement.md) konu.
* F # için bkz: [kaynak yönetimi: use anahtar sözcüğü](../fsharp/language-reference/resource-management-the-use-keyword.md).
* VB için bkz: [kullanarak deyimi (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) konu.

## <a name="type-safety"></a>Tür güvenliği

Bir nesne, belirli bir türde bir örneğidir. Belirli bir nesne için izin verilen tek işlem türü birimleridir. A `Dog` türü olabilir `Jump` ve `WagTail` yöntemleri dışında bir `SumTotal` yöntemi. Bir programı yalnızca belirli bir türde ait olan yöntemleri çağırır. Derleme zamanı hatası veya bir çalışma zamanı özel diğer tüm çağrıları neden (dinamik özelliklerini kullanarak durumunda veya `object`).

Nesne odaklı temel ve türetilmiş sınıflarının hiyerarşileri ile .NET dillerini. .NET çalışma zamanı, yalnızca bir nesne atamalar ve nesne hiyerarşisiyle Hizala çağrıları'izin verir. Herhangi bir .NET dilinde tanımlanan her tür taban türetilen unutmayın <xref:System.Object> türü.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Tür güvenliği erişimcisi anahtar sözcükleri kalitesini güvence altına almak kapsülleme uygulanmasına yardımcı olmak için de kullanılır. Erişimci anahtar sözcükleri başka bir kod tarafından belirli bir türde üyelerine erişimi denetleyen ürünleridir. Bunlar genellikle davranışını yönetmek için kullanılan veri türünde çeşitli türleri için kullanılır.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, VB ve F # yerel destek *türü çıkarımı*. Tür çıkarımı derleyici sağ taraftaki ifadesinden sol taraftaki ifade türü deduces anlamına gelir. Bu tür güvenliği bozuk veya kaçınılması anlamına gelmez. Elde edilen türü gelir güçlü bir tür olan her şeyi sahip. Önceki örnekten `dog` ve `cat` tür çıkarımı tanıtmak için yazılır ve örnek geri kalanı değiştirilmemiştir:

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F # daha türü çıkarımı özellikleri C# ve vb bulunan yöntemi yerel türü çıkarımı daha vardır Daha fazla bilgi için bkz: [tür çıkarımı](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Temsilciler ve lambdas

Bir temsilci yöntemi imza ile temsil edilir. Bu imzaya sahip herhangi bir yöntemini temsilciye atanmış olması ve temsilci çağrıldığında yürütülür.

Temsilciler türü güvenli olup olmadıklarını dışında C++ işlev işaretçileri gibi demektir. Bağlantısı kesilmiş yöntemi CLR tür sistemi içinde bir tür olup olmadıklarını. Normal yöntemleri bir sınıfa bağlı olan ve yalnızca statik veya örnek arama doğrudan aranabilir kuralları.

.NET ile olay işleyicileri, zaman uyumsuz işlemleri tanımlamakta ve LINQ taşlarıdır lambda ifadeleri temsilciler yaygın olarak kullanılır. Daha fazla bilgi edinin [Temsilciler ve Lambda'lar](delegates-lambdas.md) konu.

## <a name="generics"></a>Genel Türler

Genel türler izin tanıtmak Programcı bir *tür parametresi* tür parametresi yerine kullanılacak tam türünü belirtmek için istemci kodu (tür kullanıcılar) sağlayan kendi sınıfları tasarlarken.

Genel türler, genel veri yapılarını uygulamak programcıları yardımcı olmak için eklenmiştir. Kendi varış gibi bir tür için sırayla önce `List` genel olarak yazın, bu iş türü olan öğeleri ile gerekirdi `object`. Bu, çeşitli performans ve olası Zarif çalışma zamanı hataları birlikte anlam sorunları oluştu. İkincisi, en notorious veri yapısı, örneğin, tamsayı ve dizeler içerdiğinde bir ise `InvalidCastException` listenin üyeleri ile çalışma hakkında atılır.

Aşağıdaki örnek, bir örneği kullanılarak bir temel programın çalışmasını gösterir <xref:System.Collections.Generic.List%601> türleri:

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

Daha fazla bilgi için bkz: [genel türleri (genel türler) genel bakış](generics.md) konu.

## <a name="async-programming"></a>Zaman uyumsuz programlama

Zaman uyumsuz programlama bir birinci sınıf içinde .NET framework kitaplıkları, çalışma zamanında zaman uyumsuz desteğiyle kavramıdır ve .NET dil oluşturur. Dahili olarak, bunlar nesnelere bağlı (gibi `Task`), hangi avantajından g/Ç-bağlı işleri mümkün olduğunca verimli bir şekilde gerçekleştirmek için işletim sistemi.

. NET'te zaman uyumsuz programlama hakkında daha fazla bilgi için başlayın [zaman uyumsuz genel bakış](async.md) konu.

## <a name="language-integrated-query-linq"></a>Dil ile tümleşik sorgu (LINQ)

LINQ verilerine işletim için basit ve bildirim temelli kod yazmanıza izin özellik C# ve VB için güçlü bir kümesidir. Veriler (örneğin, bellek içi nesneler, bir SQL veritabanı veya bir XML belgesi) pek çok biçimde olabilir, ancak genellikle yazma LINQ kod veri kaynağı tarafından farklı değil.

Daha fazla bilgi edinmek ve bazı örnekler görmek için bkz: [LINQ (dil ile tümleşik sorgu)](using-linq.md) konu.

## <a name="native-interoperability"></a>Yerel birlikte çalışabilirliği

Her işletim sistemi sistem hizmetleri sağlayan bir uygulama programlama arabirimi (API) içerir. .NET bu API'leri çağırmak için çeşitli yöntemler sağlar.

Yerel birlikte çalışabilirliği yapmak için ana "platform çağırma" ya da P/Invoke ile Linux ve Windows platformlarında desteklenen kısaca yoludur. Yerel birlikte çalışabilirliği yapılması, yalnızca Windows yolu "çalışmak için kullanılan COM birlikte çalışma," olarak bilinen [COM bileşenlerini](/cpp/atl/introduction-to-com) yönetilen kod. P/Invoke altyapısının üzerinde oluşturulmuştur, ancak dilden çok az farklı şekilde çalışır.

Java ve Objective-C Mono'nın (ve dolayısıyla Xamarin'ın) birlikte çalışabilirlik desteği çoğunu benzer şekilde oluşturulur, diğer bir deyişle, bunlar aynı ilkeleri kullanın.

Bunun hakkında daha fazla bilgiyi yerel birlikte çalışabilirlik [yerel birlikte çalışabilirliği](native-interop.md) konu.

## <a name="unsafe-code"></a>Güvenli olmayan kod

Dil desteği bağlı olarak, CLR erişmenize yerel bellek ve işaretçi aritmetiği aracılığıyla yapmak olanak tanır `unsafe` kodu. Bu işlemler belirli algoritmaları ve sistem birlikte çalışabilirlik için gereklidir. Birlikte çalışabilirlik sistemi API'leri için gerekli olan veya en verimli algoritma uygulayan sürece güçlü rağmen güvenli olmayan kod kullanımı önerilmez. Güvenli olmayan kod aynı şekilde farklı ortamlarda yürütülmeyebilir ve ayrıca bir atık toplayıcısını ve tür güvenliği avantajları kaybeder. Bunu sınırlamak ve mümkün olduğunca güvenli olmayan kod merkezileştirmek ve bu kodu sınamanız önerilir.

Aşağıdaki örnek, değiştirilmiş bir sürümüdür `ToString()` yönteminden `StringBuilder` sınıfı. Bunu gösterilmektedir nasıl kullanarak `unsafe` kod verimli bir şekilde uygulayabilirsiniz bir algoritma bellek öbekleri doğrudan taşıyarak:

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Sonraki adımlar

C# özelliklerini bir turu düşünüyorsanız kullanıma [Tur, C#](../csharp/tour-of-csharp/index.md).

F # özelliklerinin bir tur ilginizi çekiyorsa bkz [Tur, F #](../fsharp/tour.md).

Kendi ziyaret kod yazmaya başlamak istiyorsanız [Başlarken](get-started.md).

.NET önemli bileşenleri hakkında bilgi edinmek için kullanıma [.NET Mimari Bileşenleri](components.md).
