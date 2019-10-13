---
title: .NET turu
description: .NET 'in bazı önemli özelliklerinden bazıları arasında kılavuzlu bir tur.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: a83253e37d3afde9ed8266ec1195c9726f6462cc
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291598"
---
# <a name="tour-of-net"></a>.NET turu

.NET, genel amaçlı bir geliştirme platformudur. Birden çok platformda çok çeşitli senaryolar sağlayan çoklu programlama dilleri, zaman uyumsuz ve eşzamanlı programlama modelleri ve yerel birlikte çalışabilirlik gibi birçok temel özelliğe sahiptir.

Bu makalede, .NET 'in temel özelliklerinden bazıları üzerinden kılavuzlu bir tur sunulmaktadır. .NET 'in mimari parçaları ve için kullanıldıkları özellikler hakkında bilgi edinmek için bkz. [.net mimari bileşenleri](components.md) konusu.

## <a name="how-to-run-the-code-samples"></a>Kod örneklerini çalıştırma

Kod örneklerini çalıştırmak için bir geliştirme ortamı ayarlamayı öğrenmek için [Başlarken](get-started.md) konusuna bakın. Kod örneklerini bu sayfadan kopyalayıp yürütmek için ortamınıza yapıştırın. 

## <a name="programming-languages"></a>Programlama dilleri

.NET birden çok programlama dilini destekler. .NET uygulamaları, diğer şeyler arasında dilden bağımsız çalışma zamanı ve dil birlikte çalışabilirliği belirten [ortak dil altyapısını (CLI)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)uygular. Bu, .NET üzerinde uygulama ve hizmet oluşturmak için herhangi bir .NET dilini seçtiğiniz anlamına gelir.

Microsoft, üç .NET dilini etkin bir şekilde geliştirir C#ve F#destekler:, ve Visual Basic (vb). 

* C#basit, güçlü, tür kullanımı uyumlu ve nesne yönelimlidir. Bu, C stili dillerin ifade ve inceliğini bir kısmını korur. C ve benzer dilleri bilen herkes, ile uyumlu olan bazı sorunlar buluyor C#. Hakkında C#daha fazla bilgi edinmek için [ C# kılavuza](../csharp/index.md) göz atın.

* F#, geleneksel nesne yönelimli ve kesinlik temelli programlamayı da destekleyen platformlar arası, işlevsel ilk programlama dilidir. Hakkında F#daha fazla bilgi edinmek için [ F# kılavuza](../fsharp/index.md) göz atın.

* Visual Basic .NET üzerinde çalışan çeşitli uygulamalar oluşturmak için kullanacağınızı öğrenmek için kolay bir dildir. .NET dilleri arasında, VB 'nin sözdizimi, normal insan diline en yakın bir deyişle, genellikle yazılım geliştirme konusunda yeni kişiler daha kolay hale gelir.

## <a name="automatic-memory-management"></a>Otomatik bellek yönetimi

.NET, programlar için otomatik bellek yönetimi sağlamak üzere [çöp toplama (GC)](garbagecollection/index.md) kullanır. GC, bellek yönetimine yönelik yavaş bir yaklaşımda çalışır ve uygulama aktarım hızını hemen bellek koleksiyonuna tercih etmenizi sağlar. .NET GC hakkında daha fazla bilgi edinmek için [çöp toplamanın (GC) temellerini](garbagecollection/fundamentals.md)inceleyin.

Aşağıdaki iki satır, her ikisi de bellek ayırır:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Bellek ayırmayı serbest bırakmak için benzer bir anahtar sözcük yoktur, çünkü atık toplayıcı tarafından zamanlanan çalışma üzerinden bellek geri kazanır.

Çöp toplayıcı, *bellek güvenliğini*sağlamaya yardımcı olan hizmetlerden biridir. Bir program, yalnızca ayrılmış belleğe eriştiğinde bellek güvende olur. Örneğin, çalışma zamanı, bir uygulamanın ayrılmamış belleğe bir dizi sınırlarının ötesinde erişmesini sağlar.

Aşağıdaki örnekte, çalışma zamanı bellek güvenliğini zorlamak için `InvalidIndexException` özel durumu oluşturur:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Yönetilmeyen kaynaklarla çalışma

Bazı nesneler *yönetilmeyen kaynaklara*başvurur. Yönetilmeyen kaynaklar, .NET çalışma zamanı tarafından otomatik olarak tutulmayan kaynaklardır. Örneğin, bir dosya tanıtıcısı yönetilmeyen bir kaynaktır. @No__t-0 nesnesi yönetilen bir nesnedir, ancak yönetilmeyen bir dosya tanıtıcısına başvurur. @No__t-0 kullanarak işiniz bittiğinde dosya tanıtıcısını serbest bırakmanız gerekir.

.NET ' te, yönetilmeyen kaynaklara başvuran nesneler <xref:System.IDisposable> arabirimini uygular. Nesnesini kullanarak işiniz bittiğinde, yönetilmeyen kaynakları serbest bırakmaktan sorumlu olan nesnenin <xref:System.IDisposable.Dispose> yöntemini çağırılırsınız. .NET dilleri, aşağıdaki örnekte gösterildiği gibi, bu nesneler için uygun bir [`using` ekstresi](../csharp/language-reference/keywords/using.md) sağlar:

[!code-csharp[UnmanagedResources](../../samples/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

@No__t-0 bloğu tamamlandığında, .NET çalışma zamanı `stream` nesnesinin <xref:System.IDisposable.Dispose> yöntemini otomatik olarak çağırır, bu da dosya tanıtıcısını yayınlar. Ayrıca, bir özel durum denetimin bloğundan ayrılmasına neden olursa, çalışma zamanı bunu yapar.

Daha fazla bilgi için aşağıdaki konulara bakın:

* İçin C#, [using deyimleri (C# başvuru)](../csharp/language-reference/keywords/using-statement.md) konusuna bakın.
* İçin F#bkz. [kaynak yönetimi: Use anahtar sözcüğü](../fsharp/language-reference/resource-management-the-use-keyword.md).
* VB için [using deyimlerinin (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) konusuna bakın.

## <a name="type-safety"></a>Tür güvenliği

Bir nesne, belirli bir türün örneğidir. Belirli bir nesne için izin verilen tek işlemler, türü olanlardır. @No__t-0 türünde `Jump` ve `WagTail` yöntemleri olabilir, ancak `SumTotal` yöntemi olamaz. Program yalnızca belirli bir türe ait yöntemleri çağırır. Diğer tüm çağrılar, derleme zamanı hatası veya çalışma zamanı özel durumuyla sonuçlanır (dinamik özellikleri veya `object` ' i kullanmak durumunda).

.NET dilleri, temel ve türetilmiş sınıfların Hiyerarşileriyle nesne yönelimlidir. .NET çalışma zamanı, yalnızca nesne hiyerarşisine göre hizalı nesne yayınlarına ve çağrılarına izin verir. Herhangi bir .NET dilinde tanımlanan her türün temel <xref:System.Object> türünden türetildiğinden emin unutmayın.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Tür güvenliği, erişimci anahtar sözcüklerinin aslına uygunluğunu garanti ederek kapsüllemeye yardımcı olmak için de kullanılır. Erişimci anahtar sözcükleri, belirli bir türdeki üyelere diğer kod tarafından erişimi denetleyen yapıtlardır. Bunlar genellikle davranışını yönetmek için kullanılan bir tür içindeki çeşitli veri türleri için kullanılır.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, VB ve F# desteği yerel *tür çıkarımı*. Tür çıkarımı, derleyicinin sağ taraftaki ifadeden sol taraftaki ifadenin türünü akmasıdır. Bu, tür güvenliği kopmuş veya kaçınılmış değildir. Elde edilen türün, her şeyi ifade eden güçlü bir türü vardır. Önceki örnekte, `dog` tür çıkarımı tanıtmak için yeniden yazılır ve örneğin geri kalanı değiştirilmez:

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F#, ve VB 'de C# bulunan yöntem yerel tür çıkarımı dışında daha fazla tür çıkarımı özelliğine sahiptir. Daha fazla bilgi için bkz. [tür çıkarımı](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Temsilciler ve Lambdalar

Bir temsilci bir yöntem imzasıyla temsil edilir. Bu imzaya sahip herhangi bir yöntem temsilciye atanabilir ve temsilci çağrıldığında yürütülür.

Temsilciler tür kullanımı C++ güvenli olduklarından hariç işlev işaretçilerine benzer. CLR tür sistemi içindeki bir bağlantısı kesilmiş yöntem türüdür. Normal yöntemler bir sınıfa iliştirilir ve yalnızca statik veya örnek çağırma kuralları aracılığıyla doğrudan çağrılabilir.

.NET ' te temsilciler genellikle olay işleyicilerde, zaman uyumsuz işlemleri tanımlama ve LINQ 'in bir temel pulu olan Lambda ifadelerinde kullanılır. [Temsilciler ve Lambdalar](delegates-lambdas.md) konusunda daha fazla bilgi edinin.

## <a name="generics"></a>Tür

Genel türler, programcı 'nin, istemci kodunun (tür kullanıcıları) tür parametresi yerine kullanılacak tam türü belirtmesini sağlayan sınıflarını tasarlarken bir *tür parametresi* almasına izin verir.

Yardım geliştirenler genel veri yapıları uygulayan genel türler eklenmiştir. @No__t-0 türü gibi bir türün genel olması için varış öncesinde, `object` türünde olan öğelerle çalışması gerekir. Bu, olası hafif çalışma zamanı hatalarıyla birlikte çeşitli performans ve anlam sorunları içeriyordu. İkincinin en fazla bir veri yapısı, örneğin, hem tamsayılar hem de dizeler ve listenin üyeleriyle çalışma sırasında bir `InvalidCastException` ' ı içerdiğinde oluşur.

Aşağıdaki örnek, <xref:System.Collections.Generic.List%601> türlerinin bir örneğini kullanarak çalışan temel bir programı göstermektedir:

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

Daha fazla bilgi için [Genel türler (genel türler) genel bakış](generics.md) konusuna bakın.

## <a name="async-programming"></a>Zaman uyumsuz programlama

Zaman uyumsuz programlama, .NET içinde çalışma zamanı, çerçeve kitaplıkları ve .NET dil yapılarında zaman uyumsuz destek içeren birinci sınıf kavramdır. Dahili olarak, g/ç bağlantılı işleri mümkün olduğunca verimli bir şekilde gerçekleştirmek için işletim sisteminden faydalanan nesneleri (`Task`) temel alırlar.

.NET 'te zaman uyumsuz programlama hakkında daha fazla bilgi edinmek için [zaman uyumsuz genel bakış](async.md) konusuyla başlayın.

## <a name="language-integrated-query-linq"></a>Dil ile tümleşik sorgu (LINQ)

LINQ, C# ve vb 'nin veri üzerinde çalışma için basit ve bildirim temelli kod yazmanıza olanak tanıyan güçlü bir özellikler kümesidir. Veriler birçok biçimde (örneğin, bellek içi nesneler, bir SQL veritabanı veya bir XML belgesi) olabilir, ancak yazdığınız LINQ kodu genellikle veri kaynağı tarafından farklılık gösterir.

Daha fazla bilgi edinmek ve bazı örneklere bakmak için bkz. [LINQ (dil Ile tümleşik sorgu)](using-linq.md) konusu.

## <a name="native-interoperability"></a>Yerel birlikte çalışabilirlik

Her işletim sistemi, sistem hizmetleri sağlayan bir uygulama programlama arabirimi (API) içerir. .NET, bu API 'Leri çağırmak için çeşitli yollar sağlar.

Yerel birlikte çalışabilirliğin ana yolu, Linux ve Windows platformları genelinde desteklenen Short için "Platform Invoke" veya P/Invoke aracılığıyla yapılır. Yerel birlikte çalışabilirliğin yalnızca Windows 'un bir yolu, Yönetilen koddaki [COM bileşenleriyle](/cpp/atl/introduction-to-com) çalışmak için kullanılan "com birlikte çalışma" olarak bilinir. P/Invoke altyapısının üzerine kurulmuştur, ancak daha sorunsuz şekilde farklı yollarla çalışmaktadır.

Birçok Mono (ve bu nedenle Xamarin 'in) Java ve amaç için birlikte çalışabilirlik desteğinin çoğu benzer şekilde oluşturulmuştur, yani aynı ilkeleri kullanır.

Yerel birlikte çalışabilirlik hakkında daha fazla bilgi için bkz. [yerel birlikte çalışabilirlik](native-interop/index.md) makalesi.

## <a name="unsafe-code"></a>Güvenli olmayan kod

Dil desteğine bağlı olarak, CLR yerel belleğe erişmenizi ve `unsafe` kodu aracılığıyla işaretçi aritmetiği yapmanızı sağlar. Bu işlemler, bazı algoritmalar ve sistem birlikte çalışabilirliği için gereklidir. Güçlü, güvenli olmayan kod kullanımı, sistem API 'Leriyle birlikte çalışabilmek ya da en verimli algoritmayı uygulamak için gerekli olmadığı için önerilmez. Güvenli olmayan kod farklı ortamlarda aynı şekilde yürütülemeyebilir ve ayrıca çöp toplayıcı ve tür güvenliği avantajlarından de yararlanmaya başlayabilir. Güvenli olmayan kodu sınırlamak ve merkezileştirmek ve kodu tamamen test etmeniz önerilir.

Aşağıdaki örnek, `StringBuilder` sınıfından `ToString()` yönteminin değiştirilmiş bir sürümüdür. @No__t-0 kodu kullanmanın, belleğin öbeklerini doğrudan taşıyarak bir algoritmayı verimli bir şekilde nasıl uygulayabileceği gösterilmektedir:

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Sonraki adımlar

Bir C# Özellik turu ile Ilgileniyorsanız, [turuna C# ](../csharp/tour-of-csharp/index.md)göz atın.

Bir F# Özellik turu ile Ilgileniyorsanız, [turuna F# ](../fsharp/tour.md)bakın.

Kendi kodunuzu yazmaya başlamak istiyorsanız [Başlarken](get-started.md)' i ziyaret edin.

.NET ' in önemli bileşenleri hakkında bilgi edinmek için [.net mimari bileşenleri](components.md)' ne göz atın.
