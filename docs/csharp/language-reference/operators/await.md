---
title: Await işleci- C# başvuru
ms.custom: seodec18
ms.date: 08/30/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: c2172f651dd106825680de3195e26f032225a9ab
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169392"
---
# <a name="await-operator-c-reference"></a>Await işleci (C# başvuru)

İşleci, işleneni tarafından temsil edilen zaman uyumsuz işlem tamamlanana kadar kapsayan [zaman uyumsuz](../keywords/async.md) metodun değerlendirmesini askıya alır. `await` Zaman uyumsuz işlem tamamlandığında `await` işleci, varsa işlemin sonucunu döndürür. `await` İşleci, zaten tamamlanmış bir işlemi temsil eden işlenene uygulandığında, kapsayan metodun askıya alınması gerekmeden işlemin sonucunu hemen döndürür. `await` İşleci zaman uyumsuz yöntemi değerlendiren iş parçacığını engellemez. `await` İşleç kapsayan yöntemi askıya aldığında, denetim yöntemi çağırana döner.

Aşağıdaki örnekte, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> yöntemi, tamamlandığında bir bayt dizisi `Task<byte[]>` üreten zaman uyumsuz bir işlemi temsil eden örneğini döndürür. İşlem tamamlanana `await` kadar operatör `DownloadDocsMainPageAsync` yöntemi askıya alır. Askıya alındığında, denetim, çağıran `DownloadDocsMainPageAsync`olan `Main` yöntemine döndürülür. `DownloadDocsMainPageAsync` Yöntemi, `DownloadDocsMainPageAsync` yöntemi tarafından gerçekleştirilen zaman uyumsuz işlemin sonucuna ihtiyaç duyuncaya kadar yürütülür. `Main` Tüm baytlar aldığında `DownloadDocsMainPageAsync` yöntemin geri kalanı değerlendirilir. <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> Bundan sonra `Main` yöntemin geri kalanı değerlendirilir.

[!code-csharp[await example](~/samples/csharp/language-reference/operators/AwaitOperator.cs)]

Önceki örnekte, 7,1 ile C# başlayarak olası [zaman uyumsuz `Main` yöntemi](../../programming-guide/main-and-command-args/index.md)kullanılmaktadır. Daha fazla bilgi için, [ana yöntem bölümünde await işlecine](#await-operator-in-the-main-method) bakın.

> [!NOTE]
> Zaman uyumsuz programlamaya giriş için bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md). `async` Ve`await` ile zaman uyumsuz programlama, [görev tabanlı zaman uyumsuz düzene](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)uyar.

`await` İşlecini yalnızca bir yöntem, [lambda ifadesi](../../programming-guide/statements-expressions-operators/lambda-expressions.md)veya [zaman uyumsuz](../keywords/async.md) anahtar sözcük tarafından değiştirilen [anonim bir yöntemde](delegate-operator.md) kullanabilirsiniz. Zaman uyumsuz bir yöntemde `await` işleci, bir [kilit ifadesinin](../keywords/lock-statement.md)bloğu içinde ve [güvenli olmayan](../keywords/unsafe.md) bir bağlamda, zaman uyumlu bir işlevin gövdesinde kullanamazsınız.
  
`await` İşlecin işleneni genellikle şu .net türlerinden biridir: <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>, veya <xref:System.Threading.Tasks.ValueTask%601>. Ancak, herhangi bir awasever ifadesi `await` işlecin işleneni olabilir. Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [awasever ifadeleri](~/_csharplang/spec/expressions.md#awaitable-expressions) bölümüne bakın.

`TResult` <xref:System.Threading.Tasks.Task%601> İfadenin türü, ifade`t` türünün veya `await t` olması<xref:System.Threading.Tasks.ValueTask%601>durumunda olur. `t` <xref:System.Threading.Tasks.Task> Türü veya<xref:System.Threading.Tasks.ValueTask>ise, türü olur.`await t` `void` Her iki durumda da `t` bir `await t` özel durum oluşturursa, özel durumu yeniden oluşturur. Özel durum işleme hakkında daha fazla bilgi için, [try-catch beyanı](../keywords/try-catch.md) makalesindeki [zaman uyumsuz metotlar bölümünde özel durumlar](../keywords/try-catch.md#exceptions-in-async-methods) bölümüne bakın.

Ve anahtar `await` sözcükleri 5 ' den C# başlayarak kullanılabilir. `async`

## <a name="await-operator-in-the-main-method"></a>Main yönteminde Await işleci

7,1 ' C# `Task` `Task<int>` `await` den başlayarak, uygulama giriş noktası olan [ yöntemi,'ıngövdesindebirişleçkullanabilmeniziçin,zamanuyumsuzolmasınısağlayabilirveyadöndürebilir.`Main` ](../../programming-guide/main-and-command-args/index.md) Önceki C# sürümlerde, `Main` yöntemin zaman uyumsuz bir işlemin tamamlanmasını beklediğini garantilemek için, karşılık gelen zaman uyumsuz tarafından döndürülen <xref:System.Threading.Tasks.Task%601> örnek <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> özelliğinin değerini alabilirsiniz yöntemidir. Değer üretmeyen zaman uyumsuz işlemler için <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz. Dil sürümünü seçme hakkında daha fazla bilgi için bkz. [ C# dil sürümünü seçme](../configure-language-version.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [await ifadeleri](~/_csharplang/spec/expressions.md#await-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [async](../keywords/async.md)
- [Async ve await ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md)
- [Görev zaman uyumsuz programlama modeli](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Zaman uyumsuz programlama](../../async.md)
- [Görev tabanlı zaman uyumsuz model](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Zaman uyumsuz, derinlemesine](../../../standard/async-in-depth.md)
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
