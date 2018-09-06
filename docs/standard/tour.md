---
title: .NET turu
description: Bazı .NET tanınmış özellikleri aracılığıyla Kılavuzlu bir turu.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: f9b4e3d885725afc4181256e02e3b174318e3ece
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723931"
---
# <a name="tour-of-net"></a>.NET turu

.NET, genel amaçlı geliştirme platformudur. Birden çok programlama dilleri, zaman uyumsuz ve eş zamanlı programlama modellerini ve yerel birlikte çalışabilirliği, birden çok platformda sağlayan çok çeşitli senaryolar için destek gibi birkaç temel özellikleri var.

Bu makalede .NET önemli özelliklerinden bazıları aracılığıyla Kılavuzlu bir turu sunar. Bkz: [.NET Mimari Bileşenleri](components.md) konu, .NET ve kullanıldıkları mimari parçalarını hakkında bilgi edinmek için.

## <a name="how-to-run-the-code-samples"></a>Kod örneklerini çalıştırma

Kod örnekleri çalıştırmak için bir geliştirme ortamı hakkında bilgi edinmek için bkz: [Başlarken](get-started.md) konu. Kopyalayın ve bunları yürütmek için ortamınıza kod örnekleri bu sayfadan yapıştırın. 

## <a name="programming-languages"></a>Programlama dilleri

.NET, birden fazla programlama dili destekler. .NET uygulamalarında uygulama [ortak dil altyapısı (CLI)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/), başka şeylerin yanında bir dilden bağımsız çalışma zamanı ve dil birlikte çalışabilirliği belirtir. Başka bir deyişle, .NET uygulamaları ve hizmetleri oluşturmak için dilediğiniz .NET dilini seçin.

Microsoft etkin olarak geliştirir ve üç .NET dilleri desteklemektedir: C#, F # ve Visual Basic (VB). 

* C# basit, güçlü, tür kullanımı uyumlu ve nesne yönelimli anlamlılık ve inceliğini C stili dillerin korurken. C ve benzer dilleri ile tanıdık herkes, birkaç sorun C# ' tan uyarlama içinde bulur. Kullanıma [C# Kılavuzu](../csharp/index.md) C# hakkında daha fazla bilgi edinmek için.

* F # de Geleneksel nesne yönelimli ve buyurgan programlamayı destekleyen bir platformlar arası ve işlevsellik öncelikli programlama dilidir. Kullanıma [F # Kılavuzu](../fsharp/index.md) F # hakkında daha fazla bilgi edinmek için.

* Visual Basic .NET üzerinde çalışan uygulamalar çeşitli oluşturmak için kullandığınız öğrenmek için kolay bir dildir. .NET diller arasında VB, genellikle kişiler için yeni yazılım geliştirme için kolaylaştırarak sıradan İnsan dil en yakın sözdizimidir.

## <a name="automatic-memory-management"></a>Otomatik bellek yönetimi

.NET kullanan [çöp toplama (GC)](garbagecollection/index.md) programları için otomatik bellek yönetimi sağlamak için. Bellek yönetimi, yavaş bir yaklaşım uygulama aktarım hızı, bellek hemen koleksiyonuna belgelemeyi GC çalışır. .NET atık toplama hakkında daha fazla bilgi edinmek için kullanıma [çöp toplama (GC) Temelleri](garbagecollection/fundamentals.md).

Aşağıdaki iki satırı hem bellek ayırma:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Ne zaman çöp toplayıcı, zamanlanan çalıştırma yoluyla belleği geri kazanır ayırmayı kaldırma otomatik olarak gerçekleşir olarak bellek ayırmayı iptal etmek için analojiktir anahtar sözcük yoktur.

Çöp toplayıcı sağlamak hizmetlerden biridir *bellek emniyet*. Yalnızca bellek ayrılan bellek erişirse, güvenli bir programdır. Örneğin, bir uygulama bir dizi sınırlarının ayrılmamış bellek erişim değil çalışma zamanı sağlar.

Aşağıdaki örnekte, çalışma zamanı oluşturur bir `InvalidIndexException` bellek güvenliği zorlamak için özel durum:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Yönetilmeyen kaynakları ile çalışma

Bazı nesneler başvuru *yönetilmeyen kaynakları*. Yönetilmeyen kaynakları .NET çalışma zamanı tarafından otomatik olarak korunmaz kaynaklardır. Örneğin, bir dosya tanıtıcısı yönetilmeyen bir kaynaktır. A <xref:System.IO.FileStream> nesnesi yönetilen bir nesnedir ancak yönetilmeyen bir dosya tanıtıcısı başvuruyor. Bitirdiğinizde kullanarak <xref:System.IO.FileStream>, dosya tanıtıcısını bırakmak gerekir.

Yönetilmeyen kaynaklara başvuran nesneler, .NET uygulama <xref:System.IDisposable> arabirimi. Bitirdiğinizde nesnesini kullanarak, nesnenin çağrı <xref:System.IDisposable.Dispose> yöntemi yönetilmeyen tüm kaynakları serbest bırakmak için sorumludur. .NET dilleri sağlayan bir kullanışlı `using` söz dizimi aşağıdaki örnekte gösterildiği gibi bu tür nesneleri için:

[!code-csharp[UnmanagedResources](../../samples/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

Bir kez `using` blok tamamlandıktan, .NET çalışma zamanı otomatik olarak çağırır `stream` nesnenin <xref:System.IDisposable.Dispose> yöntemi dosya tanıtıcısı serbest bırakır. Çalışma zamanı, denetimi bloğun bırakmak bir özel durum neden olursa da yapar.

Daha fazla ayrıntı için aşağıdaki konulara bakın:

* C# için bkz: [using deyimi (C# Başvurusu)](../csharp/language-reference/keywords/using-statement.md) konu.
* F # için bkz: [kaynak yönetimi: use anahtar sözcüğü](../fsharp/language-reference/resource-management-the-use-keyword.md).
* VB için bkz: [Using deyimi (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) konu.

## <a name="type-safety"></a>Tür güvenliği

Belirli bir türün bir örneği bir nesnedir. Belirli bir nesne için izin verilen işlemler türünü olanlardır. A `Dog` türü olabilir `Jump` ve `WagTail` yöntemleri ama bir `SumTotal` yöntemi. Bir program, yalnızca belirli bir türe ait yöntemleri çağırır. Diğer tüm çağrıları ya da bir derleme zamanı hatası ya da bir çalışma zamanı özel durumuna neden (dinamik özelliklerini kullanarak durumunda veya `object`).

.NET dilleri, nesne yönelimli temel sınıfını hem türetilen sınıflarını hiyerarşilerle. .NET çalışma zamanı, yalnızca bir nesne yayınları ve nesne hiyerarşisi ile hizalanan çağrıları'izin verir. Herhangi bir .NET dilinde tanımlanan her tür temel türetilen unutmayın <xref:System.Object> türü.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Tür güvenliği erişimci anahtar sözcükleri kalitesini güvence altına almak kapsülleme uygulanmasına yardımcı olmak için de kullanılır. Erişimci, başka kod tarafından belirtilen bir türün üyeleri için erişim denetim yapılar sözcüklerdir. Bunlar, genellikle çeşitli davranışını yönetmek için kullanılan bir tür içindeki veri türleri için kullanılır.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, VB ve F # desteği yerel *anlam çıkarma*. Tür çıkarımı, derleyicinin'ın işlecin sağ tarafındaki ifadesinden sol taraftaki ifadenin türü çıkarır anlamına gelir. Bu tür güvenliği bozuk veya önlenmiş gelmez. Sonuç türü gelir güçlü bir tür ile her şey yok. Önceki örnekte `dog` tür çıkarımı tanıtmak için yazılan ve örnek geri kalanında değiştirilmez:

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F # daha da C# ve vb bulunan yöntemi yerel tür çıkarımı daha tür çıkarımı yeteneklere sahip Daha fazla bilgi için bkz. [tür çıkarımı](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Temsilciler ve lambda ifadeleri

Bir temsilci, bir yöntem imzası tarafından temsil edilir. Bu imzaya sahip herhangi bir yöntemi, temsilciye atanabilir ve temsilci çağrıldığında yürütülür.

Tür bakımından güvenli oldukları dışında temsilciler C++ işlev işaretçileri gibidir. Bunlar, bağlantısı kesilmiş yöntemi CLR tür sistemi içinde bir tür hedeflenmiştir. Normal yöntem sınıfa eklenir ve yalnızca statik veya örnek arama doğrudan çağrılabilir kuralları.

. NET'te, temsilcileri genellikle olay işleyicileri, zaman uyumsuz işlemleri tanımlama ve LINQ taşıdır lambda ifadeleri kullanılır. Daha fazla bilgi [Temsilciler ve lambda ifadeleri](delegates-lambdas.md) konu.

## <a name="generics"></a>Genel Türler

Genel türlere izin Programcı tanıtmak bir *tür parametresi* tür parametresi yerine kullanılacak tam türünü belirtmek için istemci kodu (kullanıcı türü) sağlar, sınıflar tasarlanırken.

Genel türler, programcılar genel veri yapıları uygulamak amacıyla eklendi. Kendi varış gibi bir tür için sırayla önce `List` genel olarak yazın, türü olan öğelerle çalışma gerekir `object`. Bu, çeşitli performans ve zarif olası çalışma zamanı hataları birlikte anlam sorunlar vardı. İkincisi en ticaret olan bir veri yapısı, örneğin, hem tamsayı hem de dizeleri içerdiğinde ve bir `InvalidCastException` listesinin üyeleriyle çalışarak üzerinde oluşturulur.

Temel programı çalışan bir örneğini kullanarak aşağıdaki örnekte gösterilmektedir <xref:System.Collections.Generic.List%601> türleri:

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

Daha fazla bilgi için [genel türler (genel türler) genel bakış](generics.md) konu.

## <a name="async-programming"></a>Zaman uyumsuz programlama

Zaman uyumsuz programlama, birinci sınıf bir kavram içinde .NET framework kitaplıkları çalışma zamanı zaman uyumsuz destek ve .NET dil oluşturur. Dahili olarak, bunlar nesnelere bağlı (gibi `Task`), ı/O-ilişkili işleri mümkün olduğunca verimli bir şekilde gerçekleştirmek için işletim sistemi avantajlarından yararlanın.

. NET'te zaman uyumsuz programlama hakkında daha fazla bilgi edinmek için başlayın [zaman uyumsuz genel bakış](async.md) konu.

## <a name="language-integrated-query-linq"></a>Dil ile tümleşik sorgu (LINQ)

LINQ, güçlü bir C# ve VB için veri işletim için basit, bildirim temelli kod yazmanıza olanak tanıyan özellikler kümesidir. Veriler (örneğin, bellek içi nesneler, bir SQL veritabanı veya bir XML belgesi) pek çok biçimde olabilir, ancak genellikle yazma LINQ kodunu veri kaynağı tarafından farklı değildir.

Daha fazla bilgi edinin ve bazı örnekleri görmek için bkz: [LINQ (dil ile tümleşik sorgu)](using-linq.md) konu.

## <a name="native-interoperability"></a>Yerel birlikte çalışabilirliği

Her işletim sistemi sistem hizmetlerini sağlayan bir uygulama programlama arabirimi (API) içerir. .NET bu API'leri çağırmak için birçok yol sağlar.

Yerel birlikte çalışabilirliği yapmak için ana yol "platform çağırma" veya P/Invoke aracılığıyla Linux ve Windows platformlarında desteklenen kısa içindir. Yerel birlikte çalışabilirliği yapılması, yalnızca Windows yolu "çalışmak için kullanılan COM birlikte çalışma," olarak da bilinen [COM bileşenlerini](/cpp/atl/introduction-to-com) yönetilen kod. P/Invoke altyapısı üzerine oluşturulmuştur, ancak farenizin farklı şekillerde çalışır.

Java ve Objective-C Mono'nın (ve bu nedenle Xamarin'in) birlikte çalışabilirlik desteği çoğu benzer şekilde oluşturulmuş, diğer bir deyişle, bunlar aynı ilkeleri kullanın.

Bunun hakkında daha fazla bilgiyi yerel birlikte çalışabilirlik [yerel birlikte çalışabilirliği](native-interop.md) konu.

## <a name="unsafe-code"></a>Güvenli olmayan kod

Dil desteğine bağlı olarak, CLR yerel bellek erişip işaretçi aritmetiği aracılığıyla yapmak sağlar `unsafe` kod. Bu işlemler belirli algoritmaları ve sistem birlikte çalışabilirlik için gereklidir. Gerekli sistem API'leri ile birlikte veya en verimli algoritma uygulayan sürece güçlü ancak güvenli olmayan kod kullanılması önerilmez. Güvenli olmayan kod farklı ortamlarda aynı şekilde yürütülmeyebilir ve ayrıca bir çöp toplayıcı ve tür güvenliği avantajlarından kaybeder. Sınırlamak, güvenli olmayan kod mümkün olduğunca merkezileştirin ve bu kodu sınamanız önerilir.

Aşağıdaki örnek, değiştirilmiş bir sürümünü `ToString()` yönteminden `StringBuilder` sınıfı. Bu gösterir kullanıldığında nasıl `unsafe` kod verimli bir şekilde uygulayabilirsiniz bir algoritma bellek öbekleri doğrudan taşıyarak:

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Sonraki adımlar

C# özellikleri bir tur makalemize göz atın [turu C# ' in](../csharp/tour-of-csharp/index.md).

F # özelliklerinin bir tur ilgileniyorsanız bkz [turu, F #](../fsharp/tour.md).

Kendi ziyaret edin, kod yazmaya başlamak istiyorsanız [Başlarken](get-started.md).

Önemli .NET bileşenleri hakkında bilgi edinmek için kullanıma [.NET Mimari Bileşenleri](components.md).
