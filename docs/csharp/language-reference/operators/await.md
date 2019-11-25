---
title: Await işleci- C# başvuru
ms.custom: seodec18
ms.date: 11/08/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 36cb4a5def6b75281edbe878d89af0c18ab226ec
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140650"
---
# <a name="await-operator-c-reference"></a>Await işleci (C# başvuru)

`await` işleci, işleneni tarafından temsil edilen zaman uyumsuz işlem tamamlanana kadar kapsayan [zaman uyumsuz](../keywords/async.md) metodun değerlendirmesini askıya alır. Zaman uyumsuz işlem tamamlandığında `await` işleci, varsa işlemin sonucunu döndürür. `await` işleci, zaten tamamlanmış bir işlemi temsil eden işlenene uygulandığında, kapsayan metodun askıya alınması gerekmeden işlemin sonucunu hemen döndürür. `await` işleci zaman uyumsuz yöntemi değerlendiren iş parçacığını engellemez. `await` işleci kapsayan zaman uyumsuz yöntemi askıya aldığında, denetim yöntemi çağırana döner.

Aşağıdaki örnekte <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> yöntemi, tamamlandığında bir bayt dizisi üreten zaman uyumsuz bir işlemi temsil eden `Task<byte[]>` örneğini döndürür. İşlem tamamlanana kadar `await` işleci `DownloadDocsMainPageAsync` yöntemini askıya alır. `DownloadDocsMainPageAsync` askıya alındığında, denetim, `DownloadDocsMainPageAsync`çağıranı olan `Main` yöntemine döndürülür. `Main` yöntemi, `DownloadDocsMainPageAsync` yöntemi tarafından gerçekleştirilen zaman uyumsuz işlemin sonucuna ihtiyaç duyuncaya kadar yürütülür. <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> tüm baytlar aldığında, `DownloadDocsMainPageAsync` yönteminin geri kalanı değerlendirilir. Bundan sonra `Main` yönteminin geri kalanı değerlendirilir.

[!code-csharp[await example](~/samples/csharp/language-reference/operators/AwaitOperator.cs)]

Yukarıdaki örnekte, 7,1 ile C# başlayan [zaman uyumsuz `Main` yöntemi](../../programming-guide/main-and-command-args/index.md)kullanılmaktadır. Daha fazla bilgi için, [ana yöntem bölümünde await işlecine](#await-operator-in-the-main-method) bakın.

> [!NOTE]
> Zaman uyumsuz programlamaya giriş için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md). `async` ve `await` ile zaman uyumsuz programlama, [görev tabanlı zaman uyumsuz düzene](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)uyar.

`await` işlecini yalnızca [zaman uyumsuz](../keywords/async.md) anahtar sözcük tarafından değiştirilen bir yöntemde, [lambda ifadesinde](../../programming-guide/statements-expressions-operators/lambda-expressions.md)veya [anonim yöntemde](delegate-operator.md) kullanabilirsiniz. Zaman uyumsuz bir yöntemde, zaman uyumlu bir işlevin gövdesinde, bir [Lock ifadesinin](../keywords/lock-statement.md)bloğu içinde ve [güvenli olmayan](../keywords/unsafe.md) bir bağlamda `await` işlecini kullanamazsınız.

`await` işlecinin işleneni genellikle şu .NET türlerinden biridir: <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>veya <xref:System.Threading.Tasks.ValueTask%601>. Ancak, herhangi bir zaman awasever ifadesi `await` işlecinin işleneni olabilir. Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [awasever ifadeleri](~/_csharplang/spec/expressions.md#awaitable-expressions) bölümüne bakın.

8,0 ' C# den başlayarak, zaman uyumsuz veri akışını kullanmak için `await foreach` ifadesini kullanabilirsiniz. Daha fazla bilgi için [ C# 8,0](../../whats-new/csharp-8.md) sürümündeki yenilikler makalesindeki [zaman uyumsuz akışlar](../../whats-new/csharp-8.md#asynchronous-streams) bölümüne bakın.

İfade türü `t` <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.ValueTask%601>ise `await t` ifade türü `TResult`. `t` türü <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.ValueTask>ise, `await t` türü `void`olur. Her iki durumda da `t` bir özel durum oluşturursa, `await t` özel durumu yeniden oluşturur. Özel durum işleme hakkında daha fazla bilgi için, [try-catch beyanı](../keywords/try-catch.md) makalesindeki [zaman uyumsuz metotlar bölümünde özel durumlar](../keywords/try-catch.md#exceptions-in-async-methods) bölümüne bakın.

`async` ve `await` anahtar sözcükleri C# 5 ve sonraki sürümlerde kullanılabilir.

## <a name="await-operator-in-the-main-method"></a>Main yönteminde Await işleci

7,1 ' C# den başlayarak, uygulama giriş noktası olan [`Main` yöntemi](../../programming-guide/main-and-command-args/index.md)`Task`veya`Task<int>`döndürebilir, onun gövdesinde`await`işlecini kullanabilmeniz için zaman uyumsuz olmasını sağlayabilir. Önceki C# sürümlerde `Main` yönteminin zaman uyumsuz bir işlemin tamamlanmasını beklediği için, karşılık gelen async yöntemi tarafından döndürülen <xref:System.Threading.Tasks.Task%601> örneğinin <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> özelliğinin değerini alabilirsiniz. Değer üretmeyen zaman uyumsuz işlemler için <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz. Dil sürümünü seçme hakkında daha fazla bilgi için bkz [ C# . dil sürümü oluşturma](../configure-language-version.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [await ifadeleri](~/_csharplang/spec/expressions.md#await-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [async](../keywords/async.md)
- [Görev zaman uyumsuz programlama modeli](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Zaman uyumsuz programlama](../../async.md)
- [Zaman uyumsuz, derinlemesine](../../../standard/async-in-depth.md)
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Öğretici: 8,0 ve .NET Core 3,0 kullanarak C# zaman uyumsuz akışlar oluşturma ve kullanma](../../tutorials/generate-consume-asynchronous-stream.md)
