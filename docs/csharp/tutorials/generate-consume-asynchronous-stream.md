---
title: Zaman uyumsuz akışlar oluşturma ve kullanma
description: Bu gelişmiş öğreticide, zaman uyumsuz akışlarının oluşturulması ve kullanılması, zaman uyumsuz olarak oluşturulabilecek veri dizileri ile çalışmak için daha doğal bir yol sağlar.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: 412e5de5d9d73846fe2af36e3def383364389c75
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039219"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Öğretici: 8,0 ve .NET Core 3,0 kullanarak C# zaman uyumsuz akışlar oluşturma ve kullanma

C#8,0, veri akışındaki öğeler alınabilir veya zaman uyumsuz olarak oluşturulduğunda verilerin akış kaynağını modelleyebilir ve **zaman uyumsuz akışları**tanıtır. Zaman uyumsuz akışlar .NET Standard 2,1 ' de tanıtılan ve .NET Core 3,0 ' de uygulanan yeni arabirimleri kullanır ve zaman uyumsuz akış veri kaynakları için doğal bir programlama modeli sağlar.

Bu öğreticide, aşağıdakileri nasıl yapacağınızı öğreneceksiniz:

> [!div class="checklist"]
>
> - Zaman uyumsuz bir veri öğeleri dizisi üreten bir veri kaynağı oluşturun.
> - Bu veri kaynağını zaman uyumsuz olarak tükettin.
> - Yeni arabirim ve veri kaynağı daha önceki zaman uyumlu veri dizileri için tercih edildiği zaman tanıyın.

## <a name="prerequisites"></a>Prerequisites

Makinenizi, C# 8,0 derleyicisi dahil .NET Core çalıştıracak şekilde ayarlamanız gerekir. 8 C# derleyicisi, [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.

GitHub GraphQL uç noktasına erişebilmek için bir [GitHub erişim belirteci](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) oluşturmanız gerekir. GitHub erişim belirteciniz için aşağıdaki izinleri seçin:

- Depo: durum
- public_repo

Erişim belirtecini, GitHub API uç noktasına erişim kazanmak için kullanabilmeniz için güvenli bir yere kaydedin.

> [!WARNING]
> Kişisel erişim belirtecinizi güvende tutun. Kişisel erişim belirtecinize sahip tüm yazılımlar, erişim haklarınızı kullanarak GitHub API çağrıları yapabilir.

Bu öğreticide, Visual Studio veya C# .NET Core CLI dahil olmak üzere, .net hakkında bilgi sahibi olduğunuz varsayılır.

## <a name="run-the-starter-application"></a>Başlangıç uygulamasını çalıştırma

Bu öğreticide kullanılan başlangıç uygulamasının kodunu [CSharp/öğreticiler/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) klasöründeki [DotNet/Samples](https://github.com/dotnet/samples) depomızdan alabilirsiniz.

Başlangıç uygulaması, [DotNet/docs](https://github.com/dotnet/docs) deposunda yazılan son sorunları almak Için [GitHub graphql](https://developer.github.com/v4/) arabirimini kullanan bir konsol uygulamasıdır. Başlangıç uygulaması `Main` yöntemi için aşağıdaki koda bakarak başlayın:

[!code-csharp[StarterAppMain](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Kişisel erişim belirtecinize bir `GitHubKey` ortam değişkeni ayarlayabilir veya çağrdaki son bağımsız değişkeni kişisel erişim belirtecinizle birlikte `GenEnvVariable` olarak değiştirebilirsiniz. Kaynağı başkalarıyla kaydediyorsanız veya paylaşılan bir kaynak deposuna koymak istiyorsanız, erişim kodunuzu kaynak koda yerleştirmeyin.

GitHub istemcisini oluşturduktan sonra `Main` kod, bir ilerleme raporlama nesnesi ve bir iptal belirteci oluşturur. Bu nesneler oluşturulduktan sonra `Main` en son 250 oluşturulan sorunları almak için `runPagedQueryAsync` çağırır. Bu görev bittikten sonra sonuçlar görüntülenir.

Başlangıç uygulamasını çalıştırdığınızda, bu uygulamanın nasıl çalıştığı hakkında bazı önemli gözlemlerinizi yapabilirsiniz.  GitHub 'dan döndürülen her sayfa için ilerleme durumunu görürsünüz. GitHub her yeni sorun sayfasını geri döndürdüğünden, dikkat çekici bir duraklama gözlemleyebilirsiniz. Son olarak, sorunlar yalnızca GitHub 'dan 10 sayfa alındıktan sonra görüntülenir.

## <a name="examine-the-implementation"></a>Uygulamayı İnceleme

Uygulama, önceki bölümde ele alınan davranışı neden gözlemlediğinizi ortaya çıkarır. `runPagedQueryAsync`için kodu inceleyin:

[!code-csharp[RunPagedQueryStarter](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Yukarıdaki kodun disk belleği algoritmasına ve zaman uyumsuz yapısına odaklanalım. (GitHub GraphQL API 'SI ile ilgili ayrıntılar için [GitHub graphql belgelerine](https://developer.github.com/v4/guides/) başvurabilirsiniz.) `runPagedQueryAsync` yöntemi en sonuncudan en eskiye doğru olan sorunları numaralandırır. Sayfa başına 25 sorun ister ve önceki sayfaya devam etmek için yanıtın `pageInfo` yapısını inceler. Bu, çok sayfalı yanıtlar için GraphQL 'in standart disk belleği desteğini izler. Yanıt, bir `hasPreviousPages` değeri ve önceki sayfayı istemek için kullanılan bir `startCursor` değeri içeren bir `pageInfo` nesnesi içerir. Sorunlar `nodes` dizidir. `runPagedQueryAsync` yöntemi, tüm sayfalardaki sonuçları içeren bir diziye bu düğümleri ekler.

Bir sonuç sayfasını aldıktan ve geri yükledikten sonra, `runPagedQueryAsync` ilerlemeyi raporlar ve iptal olup olmadığını denetler. İptal isteniyorsa, `runPagedQueryAsync` bir <xref:System.OperationCanceledException> oluşturur.

Bu kodda iyileştirilen birkaç öğe vardır. En önemlisi `runPagedQueryAsync`, döndürülen tüm sorunlar için depolama alanı ayırmalıdır. Tüm açık sorunların alınması, alınan tüm sorunları depolamak için çok daha fazla bellek gerektirdiğinden, bu örnek 250 sorunlarını durduruyor. Ayrıca, ilerlemeyi destekleme ve iptali destekleme protokolleri, algoritmayı ilk okuma konusunda daha zor hale getirir. İlerleme durumunun nerede bildirileceğini bulmak için ilerleme sınıfına bakmanız gerekir. Ayrıca, İptalin istendiği ve nerede verildiğini anlamak için <xref:System.Threading.CancellationTokenSource> ve ilişkili <xref:System.Threading.CancellationToken> arasındaki iletişimleri izlemeniz gerekir.

## <a name="async-streams-provide-a-better-way"></a>Zaman uyumsuz akışlar daha iyi bir yol sağlar

Zaman uyumsuz akışlar ve ilişkili dil desteği Bu kaygıların tümünü ele. Diziyi oluşturan kod artık, `async` değiştiricisiyle bildirildi bir yöntemde öğe döndürmek için `yield return` kullanabilir. Bir `await foreach` döngüsünü kullanarak, bir `foreach` döngüsü kullanarak herhangi bir diziyi tükettiğinizde zaman uyumsuz bir akış kullanabilirsiniz.

Bu yeni dil özellikleri, 2,1 .NET Standard eklenen ve .NET Core 3,0 ' de uygulanan üç yeni arabirime bağımlıdır:

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

Bu üç arabirim çoğu C# geliştiricilere tanıdık gelmelidir. Zaman uyumlu ortaklarınıza benzer bir şekilde davranır:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Alışkın olabilecek bir tür <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>. `ValueTask` yapısı, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfına benzer bir API sağlar. `ValueTask`, performans nedenleriyle bu arabirimlerde kullanılır.

## <a name="convert-to-async-streams"></a>Zaman uyumsuz akışlara Dönüştür

Sonra, `runPagedQueryAsync` yöntemini bir zaman uyumsuz akış oluşturacak şekilde dönüştürün. İlk olarak, `runPagedQueryAsync` imzasını bir `IAsyncEnumerable<JToken>` döndürecek şekilde değiştirin ve aşağıdaki kodda gösterildiği gibi parametre listesinden iptal belirtecini ve ilerleme nesnelerini kaldırın:

[!code-csharp[FinishedSignature](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

Başlangıç kodu, aşağıdaki kodda gösterildiği gibi her sayfayı sayfa alındığından işler:

[!code-csharp[StarterPaging](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Bu üç satırı aşağıdaki kodla değiştirin:

[!code-csharp[FinishedPaging](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Ayrıca, bu yöntemin önceki `finalResults` bildirimini ve değiştirdiğiniz döngüyü izleyen `return` bildirimini de kaldırabilirsiniz.

Zaman uyumsuz akış oluşturma değişikliklerini tamamladınız. Tamamlanan yöntem aşağıdaki koda benzemelidir:

[!code-csharp[FinishedGenerate](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

Daha sonra, zaman uyumsuz akışı kullanmak için koleksiyonu tüketen kodu değiştirirsiniz. Sorun koleksiyonunu işleyen `Main` aşağıdaki kodu bulun:

[!code-csharp[EnumerateOldStyle](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Bu kodu aşağıdaki `await foreach` döngüsüyle değiştirin:

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Tamamlanan öğreticinin kodunu [CSharp/öğreticiler/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) klasöründeki [DotNet/Samples](https://github.com/dotnet/samples) deposundan alabilirsiniz.

## <a name="run-the-finished-application"></a>Tamamlanmış uygulamayı çalıştırma

Uygulamayı yeniden çalıştırın. Davranışını, başlangıç uygulamasının davranışıyla kontrast. Sonuçların ilk sayfası, kullanılabilir duruma geldiğinde numaralandırılır. Her yeni sayfa istendiği ve alındığı için bir observable durakladıkça, sonraki sayfanın sonuçları hızla numaralandırılır. `try` / `catch` bloğu iptali işlemek için gerekli değildir: çağıran, koleksiyonu listemeyi durdurabilir. Zaman uyumsuz akış, her sayfa indirildiğinden sonuçlar oluşturduğundan, ilerleme durumu açıkça raporlanır. Döndürülen her bir sorunun durumu `await foreach` döngüsüne sorunsuz bir şekilde dahildir. İlerlemeyi izlemek için bir geri çağırma nesnesine gerek yoktur.

Kodu inceleyerek, bellek kullanımıyla iyileştirmeleri görebilirsiniz. Artık tüm sonuçları numaralandırılmadan önce depolamak için bir koleksiyon ayırmanız gerekmez. Çağıran, sonuçların nasıl kullanıldığını ve bir depolama koleksiyonu gerekip gerekmediğini belirleyebilir.

Hem Başlatıcı hem de tamamlanmış uygulamaları çalıştırın ve uygulamalar arasındaki farklılıkları gözlemleyebilirsiniz. İşiniz bittiğinde, bu öğreticiyi başlattığınızda oluşturduğunuz GitHub erişim belirtecini silebilirsiniz. Bir saldırgan bu belirtece erişim kazanırsa, kimlik bilgilerinizi kullanarak GitHub API 'Lerine erişebilirler.
