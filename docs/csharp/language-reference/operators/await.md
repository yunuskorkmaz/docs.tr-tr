---
title: Await işleci-C# başvurusu
ms.date: 07/13/2020
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 20fc492e45b2d248602de59682e752026d421e06
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916916"
---
# <a name="await-operator-c-reference"></a>Await işleci (C# Başvurusu)

`await`İşleci, işleneni tarafından temsil edilen zaman uyumsuz işlem tamamlanana kadar kapsayan [zaman uyumsuz](../keywords/async.md) metodun değerlendirmesini askıya alır. Zaman uyumsuz işlem tamamlandığında `await` işleci, varsa işlemin sonucunu döndürür. İşleci, `await` zaten tamamlanmış bir işlemi temsil eden işlenene uygulandığında, kapsayan metodun askıya alınması gerekmeden işlemin sonucunu hemen döndürür. `await`İşleci zaman uyumsuz yöntemi değerlendiren iş parçacığını engellemez. `await`İşleç kapsayan zaman uyumsuz yöntemi askıya aldığında, denetim yöntemi çağırana döner.

Aşağıdaki örnekte, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> yöntemi, `Task<byte[]>` tamamlandığında bir bayt dizisi üreten zaman uyumsuz bir işlemi temsil eden örneğini döndürür. İşlem tamamlanana kadar `await` operatör yöntemi askıya alır `DownloadDocsMainPageAsync` . `DownloadDocsMainPageAsync`Askıya alındığında, denetim, çağıran olan yöntemine döndürülür `Main` `DownloadDocsMainPageAsync` . Yöntemi, `Main` yöntemi tarafından gerçekleştirilen zaman uyumsuz işlemin sonucuna ihtiyaç duyuncaya kadar yürütülür `DownloadDocsMainPageAsync` . <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>Tüm baytlar aldığında yöntemin geri kalanı `DownloadDocsMainPageAsync` değerlendirilir. Bundan sonra yöntemin geri kalanı `Main` değerlendirilir.

[!code-csharp[await example](snippets/shared/AwaitOperator.cs)]

Önceki örnekte, C# 7,1 ile başlayarak [zaman uyumsuz `Main` yöntemi](../../programming-guide/main-and-command-args/index.md)kullanılmaktadır. Daha fazla bilgi için, [ana yöntem bölümünde await işlecine](#await-operator-in-the-main-method) bakın.

> [!NOTE]
> Zaman uyumsuz programlamaya giriş için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md). Ve ile zaman uyumsuz programlama `async` `await` , [görev tabanlı zaman uyumsuz düzene](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)uyar.

`await`İşlecini yalnızca bir yöntem, [lambda ifadesi](../../programming-guide/statements-expressions-operators/lambda-expressions.md)veya [zaman uyumsuz](../keywords/async.md) anahtar sözcük tarafından değiştirilen [anonim bir yöntemde](delegate-operator.md) kullanabilirsiniz. Zaman uyumsuz bir yöntemde `await` işlecini, bir [kilit ifadesinin](../keywords/lock-statement.md)bloğu içinde ve [güvenli olmayan](../keywords/unsafe.md) bir bağlamda, zaman uyumlu bir işlevin gövdesinde kullanamazsınız.

`await`İşlecin işleneni genellikle şu .net türlerinden biridir: <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> , <xref:System.Threading.Tasks.ValueTask> , veya <xref:System.Threading.Tasks.ValueTask%601> . Ancak, herhangi bir awasever ifadesi işlecin işleneni olabilir `await` . Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [awasever ifadeleri](~/_csharplang/spec/expressions.md#awaitable-expressions) bölümüne bakın.

İfadenin türü, `await t` `TResult` ifade türünün `t` veya olması durumunda olur <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.ValueTask%601> . Türü `t` <xref:System.Threading.Tasks.Task> veya ise <xref:System.Threading.Tasks.ValueTask> , türü olur `await t` `void` . Her iki durumda da `t` bir özel durum oluşturursa, `await t` özel durumu yeniden oluşturur. Özel durum işleme hakkında daha fazla bilgi için, [try-catch beyanı](../keywords/try-catch.md) makalesindeki [zaman uyumsuz metotlar bölümünde özel durumlar](../keywords/try-catch.md#exceptions-in-async-methods) bölümüne bakın.

`async`Ve `await` anahtar sözcükleri C# 5 ve sonraki sürümlerde kullanılabilir.

## <a name="asynchronous-streams-and-disposables"></a>Zaman uyumsuz akışlar ve disposaya

C# 8,0 ' den başlayarak, zaman uyumsuz akışlar ve elden atıçlarla çalışabilirsiniz.

`await foreach`Zaman uyumsuz bir veri akışını kullanmak için ifadesini kullanın. Daha fazla bilgi için [C# 8,0 'deki](../../whats-new/csharp-8.md) yenilikler makalesindeki [ `foreach` bildirim](../keywords/foreach-in.md) makalesine ve [zaman uyumsuz akışlar](../../whats-new/csharp-8.md#asynchronous-streams) bölümüne bakın.

`await using`Bir arabirimi uygulayan bir türün nesnesi olan bir zaman uyumsuz atılabilir nesnesiyle çalışmak için ifadesini kullanın <xref:System.IAsyncDisposable> . Daha fazla bilgi için, [DisposeAsync yöntemi uygulama](../../../standard/garbage-collection/implementing-disposeasync.md) makalesinin [zaman uyumsuz atılabilir kullanma](../../../standard/garbage-collection/implementing-disposeasync.md#using-async-disposable) bölümüne bakın.

## <a name="await-operator-in-the-main-method"></a>Main yönteminde Await işleci

C# 7,1 ' den başlayarak, uygulama giriş noktası olan [ `Main` yöntemi](../../programming-guide/main-and-command-args/index.md)bir veya döndürebilir, `Task` `Task<int>` böylece işlecini gövdesinde kullanabilmeniz için zaman uyumsuz olmasını sağlayabilir `await` . Önceki C# sürümlerinde, `Main` yöntemin zaman uyumsuz bir işlemin tamamlanmasını beklediğini sağlamak için, <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601> karşılık gelen async yöntemi tarafından döndürülen örnek özelliğinin değerini alabilirsiniz. Değer üretmeyen zaman uyumsuz işlemler için <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz. Dil sürümünü seçme hakkında daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../configure-language-version.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [await ifadeleri](~/_csharplang/spec/expressions.md#await-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [async](../keywords/async.md)
- [Zaman uyumsuz görev programlama modeli](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Zaman uyumsuz programlama](../../async.md)
- [Zaman uyumsuz, derinlemesine](../../../standard/async-in-depth.md)
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Öğretici: C# 8,0 ve .NET Core 3,0 kullanarak zaman uyumsuz akışlar oluşturma ve kullanma](../../tutorials/generate-consume-asynchronous-stream.md)
