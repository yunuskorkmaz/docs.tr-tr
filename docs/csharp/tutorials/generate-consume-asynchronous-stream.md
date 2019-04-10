---
title: Oluştur ve zaman uyumsuz akışları kullanma
description: Bu gelişmiş Öğreticisi burada oluşturma ve zaman uyumsuz akışlar kullanan zaman uyumsuz olarak oluşturulan veri dizileri ile çalışmak için daha doğal bir yol sağlar senaryo da gösterilir.
ms.date: 02/10/2019
ms.custom: mvc
ms.openlocfilehash: 0fa7c778ca9ce0f0124fcc520dd4de65f2f92ea8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308555"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Öğretici: Oluşturma ve kullanarak zaman uyumsuz akışlarını kullanmasını C# 8.0 ve .NET Core 3.0

C#8.0 tanıtır **zaman uyumsuz akışlar**, veri akışında öğeleri alınan veya zaman uyumsuz olarak oluşturulan bir akış veri kaynağı modeli. Zaman uyumsuz akışlar .NET standart 2.1 içinde tanıtılan ve zaman uyumsuz akış veri kaynakları için doğal bir programlama modeli sağlamak için .NET Core 3.0 uygulanan yeni arabirimleri kullanır.

Bu öğreticide şunları öğrenirsiniz nasıl yapılır:

> [!div class="checklist"]
> * Zaman uyumsuz olarak veri öğelerinin bir dizisi oluşturan bir veri kaynağı oluşturun.
> * Bu veri kaynağı zaman uyumsuz olarak kullanır.
> * Yeni arabirim ve veri kaynağı önceki zaman uyumlu veri dizileri için tercih edilen olduğunda algılar.

## <a name="prerequisites"></a>Önkoşullar

.NET Core çalıştırmak için makinenizi ayarlamak ihtiyacınız olacak dahil olmak üzere C# 8.0 beta derleyici. C# 8 beta derleyici sürümünden itibaren kullanılabilir [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), veya en son [.NET Core 3.0 Önizleme SDK'sı](https://dotnet.microsoft.com/download/dotnet-core/3.0). Zaman uyumsuz akışlar ilk .NET Core 3.0 Önizleme 1'de kullanılabilir.

Oluşturmak ihtiyacınız olacak bir [GitHub erişim belirteci](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) GitHub GraphQL uç noktaya erişebilmesi için. GitHub erişim belirtecinizi için şu izinler seçin:

- Depo: durumu
- public_repo

GitHub API uç noktasına erişmek için kullandığı için erişim belirteci güvenli bir yere kaydedin.

> [!WARNING]
> Kişisel erişim belirtecinizi güvenli tutun. Kişisel erişim belirteci ile herhangi bir yazılım erişim haklarınız kullanarak GitHub API çağrıları yapabilir.

Bu öğreticide, aşina olduğunuz varsayılır C# ve .NET, Visual Studio veya .NET Core CLI gibi.

## <a name="run-the-starter-application"></a>Başlangıç uygulaması çalıştırma

Bu öğreticide kullanılan başlangıç uygulaması için kodu alma bizim [dotnet/samples](https://github.com/dotnet/samples) depoda [csharp/öğreticiler/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) klasör.

Başlangıç uygulaması kullanan bir konsol uygulamasıdır [GitHub GraphQL](https://developer.github.com/v4/) yazılan son sorunlar almak için arabirimi [dotnet/docs](https://github.com/dotnet/docs) depo. Başlangıç başlangıç uygulaması için şu kodu bakarak `Main` yöntemi:

[!code-csharp[StarterAppMain](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Kümelerden yapabilirsiniz bir `GitHubKey` kişisel erişim belirtecinizi veya ortam değişkeni çağrısında son bağımsız değişken yerine `GenEnvVariable` kişisel erişim belirteci ile. Kaynak başkalarıyla kaydetme veya paylaşılan kaynak deposunda koyarak erişim kodunuzu kaynak kodunda yerleştirmeyin.

GitHub istemci kodu oluşturduktan sonra `Main` bir ilerleme raporlama nesnesi ve bir iptal belirteci oluşturur. Bu nesneler oluşturulduktan sonra `Main` çağrıları `runPagedQueryAsync` sorunları oluşturulan en son 250 alınacak. Bu görev tamamlandıktan sonra sonuçlar görüntülenir.

Başlangıç uygulamasını çalıştırdığınızda, bu uygulamanın nasıl çalıştığı hakkında bazı önemli gözlemler yapabilirsiniz.  Her bir sayfa için bildirilen ilerleme durumunu görürsünüz Github'dan döndürdü. Github'da her yeni sayfa sorunların döndürmeden önce belirgin bir duraklama gözlemleyebilirsiniz. Son olarak, yalnızca tüm 10 sayfaları Github'dan alındıktan sonra sorunlar görüntülenir.

## <a name="examine-the-implementation"></a>Uygulama inceleyin

Uygulama önceki bölümde açıklanan davranışı gözlemlenen neden ortaya çıkarır. Kodu incelemek `runPagedQueryAsync`:

[!code-csharp[RunPagedQueryStarter](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Şimdi sayfalama algoritması ve zaman uyumsuz yapısını önceki kod üzerinde yoğunlaşabilirsiniz. (, Başvurabilirsiniz [GitHub GraphQL belgeleri](https://developer.github.com/v4/guides/) GitHub GraphQL API hakkında ayrıntılı bilgi için.) `runPagedQueryAsync` Yöntemi sorunları en son Yeniye numaralandırır. Sayfa başına 25 sorunları istekleri ve inceler `pageInfo` önceki sayfaya ile devam etmek için yanıtın yapısı. Bu, çok sayfalı yanıtları için standart disk belleği desteği GraphQL'ın izler. Yanıt içeren bir `pageInfo` içeren bir nesne bir `hasPreviousPages` değer ve bir `startCursor` önceki sayfaya istemek için kullanılan değer. Sorunları bulunan `nodes` dizisi. `runPagedQueryAsync` Yöntem tüm sayfalarındaki tüm sonuçları içeren bir dizi için bu düğümler ekler.

Alma ve sonuçları, bir sayfa geri sonra `runPagedQueryAsync` ilerleme raporları ve iptalleri denetler. İptal istenirse `runPagedQueryAsync` oluşturur bir <xref:System.OperationCanceledException>.

Bu kodda geliştirilebilir birkaç öğe vardır. En önemlisi de `runPagedQueryAsync` döndürülen tüm sorunlar için depolama ayırmanız gerekir. Tüm açık sorunları alınıyor alınan tüm sorunları depolamak için çok daha fazla bellek gerekeceğinden, bu örnek 250 sorunu durdurur. Ayrıca, algoritma ilerleme desteklemek ve iptalini destekleyen protokoller, ilk okuma anlaşılması zor sağlar. İlerleme durumunu burada bildirilir bulmak ilerleme sınıfı için aramanız gerekir. Üzerinden iletişime izlemek de <xref:System.Threading.CancellationTokenSource> ve onun ilişkili <xref:System.Threading.CancellationToken> burada İptal işlemi istendikten ve burada verilen anlamak için.

## <a name="async-streams-provide-a-better-way"></a>Zaman uyumsuz akışlar daha iyi bir yol sağlar.

Zaman uyumsuz akışlar ve ilişkili dil desteği tüm o endişelere. Bir sıra üretir kodu artık kullanabilirsiniz `yield return` ile bildirilen bir yöntemi öğeleri döndürmek için `async` değiştiricisi. Kullanarak bir zaman uyumsuz akış tüketebileceği bir `await foreach` dizisi kullanılarak kullanma gibi döngü bir `foreach` döngü.

Bu yeni dil özellikleri standart .NET 2.1 için eklenen ve .NET Core 3. 0'uygulanan üç yeni arabirimi bağlıdır:

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

Bu üç arabirimi en bilmelisiniz C# geliştiriciler. Zaman uyumlu karşılıkları benzer şekilde davranır:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Tanınmayan bir tür <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>. `ValueTask` Yapısı için benzer bir API sağlar <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfı. `ValueTask` Bu arabirimleri, performansı artırmak için kullanılır.

## <a name="convert-to-async-streams"></a>Zaman uyumsuz akışlara dönüştürür

Ardından, dönüştürme `runPagedQueryAsync` bir zaman uyumsuz akış oluşturmak için yöntemi. İlk olarak, imzasını Değiştir `runPagedQueryAsync` döndürülecek bir `IAsyncEnumerable<JToken>`ve aşağıdaki kodda gösterildiği gibi parametre listesinden iptal belirtecini ve ilerleme nesneleri kaldırın:

[!code-csharp[FinishedSignature](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

Sayfa getirildiği Başlatıcı kodunu her sayfada aşağıdaki kodda gösterildiği gibi işler:

[!code-csharp[StarterPaging](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Bu üç satırı aşağıdaki kodla değiştirin:

[!code-csharp[FinishedPaging](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Bildirimi de kaldırabilirsiniz `finalResults` bu yöntemin önceki ve `return` takip eden döngü ifadesi, değiştiren.

Zaman uyumsuz bir akış oluşturmak için değişiklikleri tamamladınız. Tamamlanmış yöntemi, aşağıdaki koda benzemelidir:

[!code-csharp[FinishedGenerate](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

Ardından, zaman uyumsuz akışın kullanmak için koleksiyon kullanan kodu değiştirin. Aşağıdaki kodu bulun `Main` sorunları koleksiyonunu işlemler:

[!code-csharp[EnumerateOldStyle](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Bu kodu aşağıdakiyle değiştirin `await foreach` döngü:

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Öğreticinin tamamlanan kodu alabilirsiniz [dotnet/samples](https://github.com/dotnet/samples) depoda [csharp/öğreticiler/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) klasör.

## <a name="run-the-finished-application"></a>Tamamlanmış uygulamayı çalıştırın

Uygulamayı yeniden çalıştırın. Başlangıç uygulaması davranış davranışını karşılaştırın. Kullanılabilir duruma geldiği ilk sayfasını numaralandırılmış alan şeklinde. Her yeni sayfa istenen ve alınan gözlemlenebilir bir duraklatma olan ve sonraki sayfanın sonuçlarını hızla numaralandırılır. `try`  /  `catch` Blok iptal işlemek için gerekli olmayan: çağıran koleksiyon numaralandırma durdurabilirsiniz. Zaman uyumsuz akış her sayfada indirildiğini sonuçları oluşturduğundan ilerleme NET bir şekilde bildirilir.

Kodu inceleyerek, bellek kullanımı geliştirmeleri görebilirsiniz. Artık, bunlar numaralandırılan önce tüm sonuçları depolamak için bir koleksiyon ayırması gerekmez. Çağıran, sonuçları kullanma ve bir depolama koleksiyon gerekip gerekmediğini belirleyebilirsiniz.

Başlangıç ve tamamlanan uygulamaların çalıştırın ve kendiniz için uygulamaları arasındaki farklar gözlemleyebilirsiniz. Sonra Bu öğreticide başlatıldığında oluşturduğunuz GitHub erişim belirteci silebilirsiniz tamamlandı. Bir saldırganın bu belirteci erişim elde edilen, GitHub kimlik bilgilerinizi kullanarak API'leri erişim.
