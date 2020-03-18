---
title: Async akışları oluşturma ve tüket
description: Bu gelişmiş öğretici, async akışları oluşturma ve tüketen eşitbir şekilde oluşturulabilir veri dizileri ile çalışmak için daha doğal bir yol sağlar senaryoları göstermektedir.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: de090eb9cc1e8b511956313ab5169ee4d07a492f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156746"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Öğretici: C# 8.0 ve .NET Core 3.0 kullanarak async akışları oluşturun ve tüketin

C# 8.0, veri akışındaki öğeler alınadığında veya eşzamanlı olarak oluşturulabilirken bir veri akışı kaynağını modelleyen **async akışlarını**sunar. Async akışları, asynchronous akış veri kaynakları için doğal bir programlama modeli sağlamak için .NET Standard 2.1'de tanıtılan ve .NET Core 3.0'da uygulanan yeni arabirimlere dayanır.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Eşit bir şekilde bir veri öğesi dizisi oluşturan bir veri kaynağı oluşturun.
> - Bu veri kaynağını eşzamanlı olarak tüketin.
> - Yeni arabirimin ve veri kaynağının önceki senkron veri dizilerine ne zaman tercih edilecek olduğunu tanıyın.

## <a name="prerequisites"></a>Önkoşullar

C# 8.0 derleyicisi de dahil olmak üzere .NET Core'u çalıştıracak şekilde makinenizi ayarlamanız gerekir. C# 8 derleyicisi [Visual Studio 2019 sürüm 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.

GitHub GraphQL bitiş noktasına erişebilmeniz için bir [GitHub erişim belirteci](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) oluşturmanız gerekir. GitHub Erişim Jetonu'nuz için aşağıdaki izinleri seçin:

- repo:durum
- public_repo

Erişim belirtecikaydet, böylece GitHub API bitiş noktasına erişmek için kullanabilirsiniz.

> [!WARNING]
> Kişisel erişim belirtecinizi güvende tutun. Kişisel erişim belirtecinize sahip herhangi bir yazılım, erişim haklarınızı kullanarak GitHub API aramaları yapabilir.

Bu öğretici, Visual Studio veya .NET Core CLI dahil olmak üzere C# ve .NET'e aşina olduğunuzu varsayar.

## <a name="run-the-starter-application"></a>Başlatıcı uygulamasını çalıştırın

Bu öğreticide kullanılan başlangıç uygulamasının kodunu [csharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) klasöründeki [dotnet/samples](https://github.com/dotnet/samples) depomuzdan alabilirsiniz.

Başlatıcı uygulaması, [dotnet/docs](https://github.com/dotnet/docs) deposunda yazılan son sorunları almak için [GitHub GraphQL](https://developer.github.com/v4/) arabirimini kullanan bir konsol uygulamasıdır. Başlangıç uygulaması `Main` yöntemi için aşağıdaki koda bakarak başlayın:

[!code-csharp[StarterAppMain](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Kişisel erişim belirtecinize bir `GitHubKey` ortam değişkeni ayarlayabilir veya aramadaki `GenEnvVariable` son bağımsız değişkeni kişisel erişim belirtecinize değiştirebilirsiniz. Kaynağı başkalarıyla birlikte kaydedecekseniz veya paylaşılan bir kaynak deposuna koyacaksanız, erişim kodunuzu kaynak koduna koymayın.

GitHub istemcisini oluşturduktan sonra, kod `Main` bir ilerleme raporlama nesnesi ve bir iptal belirteci oluşturur. Bu nesneler oluşturulduktan `Main` sonra, en son oluşturulan 250 sorunları almak için çağrılar. `runPagedQueryAsync` Bu görev tamamlandıktan sonra sonuçlar görüntülenir.

Başlangıç uygulamasını çalıştırdığınızda, bu uygulamanın nasıl çalıştığı hakkında bazı önemli gözlemler yapabilirsiniz.  GitHub'dan döndürülen her sayfa için bildirilen ilerlemeyi görürsünüz. GitHub her yeni sorun sayfasını döndürmeden önce fark edilir bir duraklama gözlemleyebilirsiniz. Son olarak, sorunlar yalnızca 10 sayfanın tümü GitHub'dan alındıktan sonra görüntülenir.

## <a name="examine-the-implementation"></a>Uygulamayı inceleyin

Uygulama, önceki bölümde tartışılan davranışı neden gözlemlediğinizi ortaya çıkarır. Aşağıdakilerin kodunu `runPagedQueryAsync`inceleyin:

[!code-csharp[RunPagedQueryStarter](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Sayfalama algoritmasına ve önceki kodun async yapısına odaklanalım. (GitHub GraphQL API ayrıntıları için [GitHub GraphQL belgelerine](https://developer.github.com/v4/guides/) danışabilirsiniz.) Yöntem, `runPagedQueryAsync` sorunları en sondan en eskiye doğru günceller. Sayfa başına 25 sayı ister `pageInfo` ve önceki sayfayla devam etmek için yanıtın yapısını inceler. Bu, GraphQL'nin çok sayfalı yanıtlar için standart sayfalama desteğini izler. Yanıt, bir `pageInfo` `hasPreviousPages` değer ve önceki `startCursor` sayfayı istemek için kullanılan bir değer içeren bir nesne içerir. Sorunlar dizide. `nodes` Yöntem, `runPagedQueryAsync` bu düğümleri tüm sayfaların tüm sonuçlarını içeren bir diziye ekler.

Bir sayfa sonuç alınıp geri aldıktan sonra, `runPagedQueryAsync` ilerleme yi raporlar ve iptal için denetimler. İptal talep edildiyse, `runPagedQueryAsync` bir <xref:System.OperationCanceledException>.

Bu kodda geliştirilebilen birkaç öğe vardır. En önemlisi, `runPagedQueryAsync` döndürülen tüm sorunlar için depolama ayırması gerekir. Tüm açık sorunları almak, alınan tüm sorunları depolamak için çok daha fazla bellek gerektirdiğinden, bu örnek 250 konuda durur. Buna ek olarak, ilerlemeyi ve iptali destekleme protokolleri algoritmayı ilk okumasında daha iyi anlamayı zorlaştırır. İlerlemenin raporlandığı yeri bulmak için ilerleme sınıfını aramalısınız. İptalin nerede istendiğini <xref:System.Threading.CancellationTokenSource> ve nerede verildiğini <xref:System.Threading.CancellationToken> anlamak için iletişimleri ve ilgili iletişimleri izlemeniz gerekir.

## <a name="async-streams-provide-a-better-way"></a>Async akışları daha iyi bir yol sağlar

Async akışları ve ilişkili dil desteği tüm bu endişeleri giderir. Sırayı oluşturan kod artık `yield return` `async` değiştirici ile bildirilen bir yöntemdeki öğeleri döndürmek için kullanabilirsiniz. Bir `foreach` döngü kullanarak herhangi bir `await foreach` dizi tüketmek gibi bir döngü kullanarak bir async akışı tüketebilirsiniz.

Bu yeni dil özellikleri ,NET Standart 2.1'e eklenen ve .NET Core 3.0'da uygulanan üç yeni arabirime bağlıdır:

```csharp
namespace System.Collections.Generic
{
    public interface IAsyncEnumerable<out T>
    {
        IAsyncEnumerator<T> GetAsyncEnumerator(CancellationToken cancellationToken = default);
    }

    public interface IAsyncEnumerator<out T> : IAsyncDisposable
    {
        T Current { get; }

        ValueTask<bool> MoveNextAsync();
    }
}

namespace System
{
    public interface IAsyncDisposable
    {
        ValueTask DisposeAsync();
    }
}
```

Bu üç arabirim çoğu C# geliştiricisine aşina olmalıdır. Senkron benzerlerine benzer bir şekilde davranıyorlar:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Yabancı olabilecek bir tür. <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Yapı, `ValueTask` sınıfa benzer bir API sağlar. `ValueTask`performans nedenleriyle bu arabirimlerde kullanılır.

## <a name="convert-to-async-streams"></a>Async akışlarına dönüştürme

Ardından, bir `runPagedQueryAsync` async akışı oluşturmak için yöntemi dönüştürün. İlk olarak, bir `runPagedQueryAsync` `IAsyncEnumerable<JToken>`, ' döndürmek için imzasını değiştirin ve aşağıdaki kodda gösterildiği gibi parametre listesinden iptal belirteci ve ilerleme nesneleri kaldırın:

[!code-csharp[FinishedSignature](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

Başlangıç kodu, aşağıdaki kodda gösterildiği gibi, sayfa alınırken her sayfayı işler:

[!code-csharp[StarterPaging](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Bu üç satırı aşağıdaki kodla değiştirin:

[!code-csharp[FinishedPaging](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Ayrıca, bu yöntemde `finalResults` önceki bildirimi ve `return` değiştirdiğiniz döngüyü izleyen bildirimi de kaldırabilirsiniz.

Bir async akışı oluşturmak için değişiklikleri tamamladınız. Bitmiş yöntem aşağıdaki koda benzemelidir:

[!code-csharp[FinishedGenerate](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

Ardından, async akışını tüketmek için koleksiyonu tüketen kodu değiştirirsiniz. Sorunların toplanmasını `Main` işleyen aşağıdaki kodu bulun:

[!code-csharp[EnumerateOldStyle](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Bu kodu aşağıdaki `await foreach` döngüyle değiştirin:

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Varsayılan olarak, akış öğeleri yakalanan bağlamında işlenir. Bağlamın ele geçirilmesini devre dışı kılmış <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> olmak istiyorsanız, uzantı yöntemini kullanın. Eşitleme bağlamları ve geçerli bağlamı yakalama hakkında daha fazla bilgi [için, Görev tabanlı eşzamanlı deseni tüketme makalesine](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)bakın.

Bitmiş öğreticinin kodunu [csharp/tutorials/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) klasöründeki [dotnet/samples](https://github.com/dotnet/samples) deposundan alabilirsiniz.

## <a name="run-the-finished-application"></a>Bitmiş uygulamayı çalıştırma

Uygulamayı yeniden çalıştırın. Davranışını başlatıcı uygulamasının davranışıyla karşılaştırın. Sonuçların ilk sayfası kullanılabilir olur olmaz numaralandırılır. Her yeni sayfa istendiğinde ve alındığı için gözlemlenebilir bir duraklama olur, ardından bir sonraki sayfanın sonuçları hızla numaralandırılır. Engellemenin `try`  /  `catch` iptal işlemlerini işlemek için gerekli değildir: arayan koleksiyona sayısal olarak son verebilir. Async akışı her sayfa indirilirken sonuç ürettiğinden ilerleme açıkça bildirilir. Döndürülen her sorunun durumu döngüye `await foreach` sorunsuz bir şekilde dahil edilir. İlerlemeyi izlemek için geri arama nesnesine gerek yoktur.

Kodu inceleyerek bellek kullanımındaki gelişmeleri görebilirsiniz. Artık numaralandırılmadan önce tüm sonuçları depolamak için bir koleksiyon ayırmanız gerekmez. Arayan, sonuçların nasıl tüketilen ve bir depolama koleksiyonu gerekip gerekip gerekip gerekip gerekmeden belirlenebileceğini belirleyebilir.

Hem başlangıç hem de bitmiş uygulamaları çalıştırın ve uygulamalar arasındaki farkları kendiniz görebilirsiniz. Bu öğreticiyi bitirdikten sonra başlattığınızda oluşturduğunuz GitHub erişim jetonunu silebilirsiniz. Bir saldırgan bu belirteç erişimigeldiyse, kimlik bilgilerinizi kullanarak GitHub API'lerine erişebilir.
