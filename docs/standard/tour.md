---
title: .NET Turu
description: .NET 'in bazı önemli özelliklerinden bazıları arasında kılavuzlu bir tur.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: 0cfd9d6da2c53b46c04773f429ab2e52f2b65c7f
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438092"
---
# <a name="tour-of-net"></a>.NET Turu

.NET, genel amaçlı bir geliştirme platformudur. Birden çok platformda çok çeşitli senaryolar sağlayan çoklu programlama dilleri, zaman uyumsuz ve eşzamanlı programlama modelleri ve yerel birlikte çalışabilirlik gibi birçok temel özelliğe sahiptir.

Bu makalede, .NET 'in temel özelliklerinden bazıları üzerinden kılavuzlu bir tur sunulmaktadır. .NET 'in mimari parçaları ve için kullanıldıkları özellikler hakkında bilgi edinmek için bkz. [.net mimari bileşenleri](components.md) konusu.

## <a name="how-to-run-the-code-samples"></a>Kod örneklerini çalıştırma

Kod örneklerini çalıştırmak için bir geliştirme ortamı ayarlamayı öğrenmek için [Başlarken](get-started.md) konusuna bakın. Kod örneklerini bu sayfadan kopyalayıp yürütmek için ortamınıza yapıştırın.

## <a name="programming-languages"></a>Programlama dilleri

.NET birden çok programlama dilini destekler. .NET uygulamaları, diğer şeyler arasında dilden bağımsız çalışma zamanı ve dil birlikte çalışabilirliği belirten [ortak dil altyapısını (CLI)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)uygular. Bu, .NET üzerinde uygulama ve hizmet oluşturmak için herhangi bir .NET dilini seçtiğiniz anlamına gelir.

Microsoft, üç .NET dilini etkin bir şekilde geliştirir ve destekler: C#, F # ve Visual Basic.

* C# basit, güçlü, tür kullanımı uyumlu ve nesne yönelimli bir işlemdir. Bu, C stili dillerin ifade ve inceliğini bir kısmını korur. C ve benzer dilleri bilen herkes C# ' ye uyarlanmaya yönelik birkaç sorun buluyor. C# hakkında daha fazla bilgi edinmek için [C# kılavuzuna](../csharp/index.yml) göz atın.

* F #, geleneksel nesne yönelimli ve kesinlik temelli programlamayı da destekleyen platformlar arası, işlevsel ilk programlama dilidir. F # hakkında daha fazla bilgi edinmek için [f # kılavuzuna](../fsharp/index.yml) göz atın.

* Visual Basic .NET üzerinde çalışan çeşitli uygulamalar oluşturmak için kullanacağınızı öğrenmek için kolay bir dildir. .NET dilleri arasında Visual Basic sözdizimi, normal insan diline en yakın bir deyişle, çoğu zaman yazılım geliştirme konusunda yeni kişiler daha kolay hale gelir. Visual Basic hakkında daha fazla bilgi edinmek için [Visual Basic kılavuzuna](../visual-basic/index.yml) göz atın.

## <a name="automatic-memory-management"></a>Otomatik bellek yönetimi

.NET, programlar için otomatik bellek yönetimi sağlamak üzere [çöp toplama (GC)](garbage-collection/index.md) kullanır. GC, bellek yönetimine yönelik yavaş bir yaklaşımda çalışır ve uygulama aktarım hızını hemen bellek koleksiyonuna tercih etmenizi sağlar. .NET GC hakkında daha fazla bilgi edinmek için [çöp toplamanın (GC) temellerini](garbage-collection/fundamentals.md)inceleyin.

Aşağıdaki iki satır, her ikisi de bellek ayırır:

[!code-csharp[MemoryManagement](../../samples/snippets/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Bellek ayırmayı serbest bırakmak için benzer bir anahtar sözcük yoktur, çünkü atık toplayıcı tarafından zamanlanan çalışma üzerinden bellek geri kazanır.

Çöp toplayıcı, *bellek güvenliğini*sağlamaya yardımcı olan hizmetlerden biridir. Bir program, yalnızca ayrılmış belleğe eriştiğinde bellek güvende olur. Örneğin, çalışma zamanı, bir uygulamanın ayrılmamış belleğe bir dizi sınırlarının ötesinde erişmesini sağlar.

Aşağıdaki örnekte, çalışma zamanı <xref:System.IndexOutOfRangeException> bellek güvenliğini zorlamak için bir özel durum oluşturur:

[!code-csharp[MemoryManagement](../../samples/snippets/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Yönetilmeyen kaynaklarla çalışma

Bazı nesneler *yönetilmeyen kaynaklara*başvurur. Yönetilmeyen kaynaklar, .NET çalışma zamanı tarafından otomatik olarak tutulmayan kaynaklardır. Örneğin, bir dosya tanıtıcısı yönetilmeyen bir kaynaktır. Bir <xref:System.IO.FileStream> nesne yönetilen bir nesnedir, ancak yönetilmeyen bir dosya tanıtıcısına başvurur. Kullanarak işiniz bittiğinde <xref:System.IO.FileStream> dosya tanıtıcısını serbest bırakmanız gerekir.

.NET ' te, yönetilmeyen kaynaklara başvuran nesneler arabirimini uygular <xref:System.IDisposable> . Nesnesini kullanarak işiniz bittiğinde, <xref:System.IDisposable.Dispose> yönetilmeyen kaynakları serbest bırakmaktan sorumlu olan nesnenin yöntemini çağıracağız. .NET dilleri, aşağıdaki örnekte gösterildiği gibi, bu nesneler için uygun bir [ `using` bildirim](../csharp/language-reference/keywords/using.md) sağlar:

[!code-csharp[UnmanagedResources](../../samples/snippets/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

`using`Blok tamamlandığında, .NET çalışma zamanı otomatik olarak `stream` nesnenin <xref:System.IDisposable.Dispose> yöntemini çağırır ve dosya tanıtıcısını yayınlar. Ayrıca, bir özel durum denetimin bloğundan ayrılmasına neden olursa, çalışma zamanı bunu yapar.

Daha fazla bilgi için aşağıdaki konulara bakın:

* C# için bkz. [using deyimleri (C# Başvurusu)](../csharp/language-reference/keywords/using-statement.md) konusu.
* F # için bkz. [kaynak yönetimi: Use anahtar sözcüğü](../fsharp/language-reference/resource-management-the-use-keyword.md).
* Visual Basic için bkz. [using deyimin (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) konusu.

## <a name="type-safety"></a>Tür güvenliği

Bir nesne, belirli bir türün örneğidir. Belirli bir nesne için izin verilen tek işlemler, türü olanlardır. Bir `Dog` tür `Jump` ve yöntemleri olabilir, `WagTail` ancak bir `SumTotal` Yöntem olamaz. Program yalnızca belirli bir türe ait yöntemleri çağırır. Diğer tüm çağrılar, derleme zamanı hatası veya çalışma zamanı özel durumuyla sonuçlanır (dinamik özellikleri veya kullanımı durumunda `object` ).

.NET dilleri, temel ve türetilmiş sınıfların Hiyerarşileriyle nesne yönelimlidir. .NET çalışma zamanı, yalnızca nesne hiyerarşisine göre hizalı nesne yayınlarına ve çağrılarına izin verir. Herhangi bir .NET dilinde tanımlanan her türün temel türden türetildiğinden emin olmak <xref:System.Object> .

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Tür güvenliği, erişimci anahtar sözcüklerinin aslına uygunluğunu garanti ederek kapsüllemeye yardımcı olmak için de kullanılır. Erişimci anahtar sözcükleri, belirli bir türdeki üyelere diğer kod tarafından erişimi denetleyen yapıtlardır. Bunlar genellikle davranışını yönetmek için kullanılan bir tür içindeki çeşitli veri türleri için kullanılır.

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, Visual Basic ve F # yerel *tür çıkarımını*destekler. Tür çıkarımı, derleyicinin sağ taraftaki ifadeden sol taraftaki ifadenin türünü akmasıdır. Bu, tür güvenliği kopmuş veya kaçınılmış değildir. Elde edilen türün, her şeyi ifade eden güçlü bir türü vardır. Önceki örnekte, `dog` tür çıkarımı tanıtmak için yeniden yazılır ve örneğin geri kalanı değiştirilmez:

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F #, C# ve Visual Basic ' de bulunan yöntem yerel tür çıkarımı dışında daha da fazla tür çıkarımı özelliğine sahiptir. Daha fazla bilgi için bkz. [tür çıkarımı](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Temsilciler ve lambda ifadeleri

Bir temsilci bir yöntem imzasıyla temsil edilir. Bu imzaya sahip herhangi bir yöntem temsilciye atanabilir ve temsilci çağrıldığında yürütülür.

Temsilciler tür kullanımı güvenli olduklarından, C++ işlev işaretçilerine benzer. CLR tür sistemi içindeki bir bağlantısı kesilmiş yöntem türüdür. Normal yöntemler bir sınıfa iliştirilir ve yalnızca statik veya örnek çağırma kuralları aracılığıyla doğrudan çağrılabilir.

.NET ' te temsilciler genellikle olay işleyicilerde, zaman uyumsuz işlemleri tanımlama ve LINQ 'in bir temel pulu olan Lambda ifadelerinde kullanılır. [Temsilciler ve Lambdalar](delegates-lambdas.md) konusunda daha fazla bilgi edinin.

## <a name="generics"></a>Genel Türler

Genel türler, programcı 'nin, istemci kodunun (tür kullanıcıları) tür parametresi yerine kullanılacak tam türü belirtmesini sağlayan sınıflarını tasarlarken bir *tür parametresi* almasına izin verir.

Yardım geliştirenler genel veri yapıları uygulayan genel türler eklenmiştir. Gelişinden önce, tür gibi bir türün genel olması için, `List` türünde olan öğelerle çalışması gerekir `object` . Bu, olası hafif çalışma zamanı hatalarıyla birlikte çeşitli performans ve anlam sorunları içeriyordu. Ortak bir çalışma zamanı hatası, bir veri yapısının içerdiğinde, örneğin hem tamsayılar hem de dizeler ve <xref:System.InvalidCastException> listenin üyelerini işlerken oluşturulur.

Aşağıdaki örnek, bir tür örneği kullanılarak çalışan temel bir programı göstermektedir <xref:System.Collections.Generic.List%601> :

[!code-csharp[GenericsShort](../../samples/snippets/csharp/snippets/tour/GenericsShort.csx)]

Daha fazla bilgi için [Genel türler (genel türler) genel bakış](generics.md) konusuna bakın.

## <a name="async-programming"></a>Zaman uyumsuz programlama

Zaman uyumsuz programlama, .NET içinde çalışma zamanı, çerçeve kitaplıkları ve .NET dil yapılarında zaman uyumsuz destek içeren birinci sınıf kavramdır. Dahili olarak, `Task` g/ç bağlantılı işleri mümkün olduğunca verimli bir şekilde gerçekleştirmek için işletim sisteminden faydalanan nesneleri (gibi) temel alırlar.

.NET 'te zaman uyumsuz programlama hakkında daha fazla bilgi edinmek için [zaman uyumsuz genel bakış](async.md) konusuyla başlayın.

## <a name="language-integrated-query-linq"></a>Dil ile Tümleşik Sorgu (LINQ)

LINQ, C# ve Visual Basic veri üzerinde çalışma için basit ve bildirim temelli kod yazmanıza olanak tanıyan güçlü bir özellikler kümesidir. Veriler birçok biçimde (örneğin, bellek içi nesneler, bir SQL veritabanı veya bir XML belgesi) olabilir, ancak yazdığınız LINQ kodu genellikle veri kaynağı tarafından farklılık gösterir.

Daha fazla bilgi edinmek ve bazı örneklere bakmak için bkz. [LINQ (dil Ile tümleşik sorgu) genel bakış](./linq/index.md) makalesi.

## <a name="native-interoperability"></a>Native ile birlikte çalışma

Her işletim sistemi, sistem hizmetleri sağlayan bir uygulama programlama arabirimi (API) içerir. .NET, bu API 'Leri çağırmak için çeşitli yollar sağlar.

Yerel birlikte çalışabilirliğin ana yolu, Linux ve Windows platformları genelinde desteklenen Short için "Platform Invoke" veya P/Invoke aracılığıyla yapılır. Yerel birlikte çalışabilirliğin yalnızca Windows 'un bir yolu, Yönetilen koddaki [COM bileşenleriyle](/cpp/atl/introduction-to-com) çalışmak için kullanılan "com birlikte çalışma" olarak bilinir. P/Invoke altyapısının üzerine kurulmuştur, ancak daha sorunsuz şekilde farklı yollarla çalışmaktadır.

Birçok Mono (ve bu nedenle Xamarin 'in) Java ve amaç için birlikte çalışabilirlik desteğinin çoğu benzer şekilde oluşturulmuştur, yani aynı ilkeleri kullanır.

Yerel birlikte çalışabilirlik hakkında daha fazla bilgi için bkz. [yerel birlikte çalışabilirlik](native-interop/index.md) makalesi.

## <a name="unsafe-code"></a>Güvenli olmayan kod

Dil desteğine bağlı olarak, CLR yerel belleğe erişmenizi ve kod aracılığıyla işaretçi aritmetiği yapmanızı sağlar `unsafe` . Bu işlemler, bazı algoritmalar ve sistem birlikte çalışabilirliği için gereklidir. Güçlü, güvenli olmayan kod kullanımı, sistem API 'Leriyle birlikte çalışabilmek ya da en verimli algoritmayı uygulamak için gerekli olmadığı için önerilmez. Güvenli olmayan kod farklı ortamlarda aynı şekilde yürütülemeyebilir ve ayrıca çöp toplayıcı ve tür güvenliği avantajlarından de yararlanmaya başlayabilir. Güvenli olmayan kodu sınırlamak ve merkezileştirmek ve kodu tamamen test etmeniz önerilir.

Aşağıdaki örnek, sınıfından yönteminin değiştirilmiş bir sürümüdür `ToString()` `StringBuilder` . Kod kullanmanın, `unsafe` bellek öbeklerini doğrudan kullanarak bir algoritmayı nasıl verimli bir şekilde uygulayabileceği gösterilmektedir:

[!code-csharp[Unsafe](../../samples/snippets/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Sonraki adımlar

C# özelliklerinin turuna ilgileniyorsanız, [C# turuna](../csharp/tour-of-csharp/index.md)göz atın.

F # özelliklerinin turuna ilgileniyorsanız, bkz. [Tur-f #](../fsharp/tour.md).

Kendi kodunuzu yazmaya başlamak istiyorsanız [Başlarken](get-started.md)' i ziyaret edin.

.NET ' in önemli bileşenleri hakkında bilgi edinmek için [.net mimari bileşenleri](components.md)' ne göz atın.
