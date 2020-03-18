---
title: bekleyen operatör - C# referans
ms.date: 11/08/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 9f541ae9c26eb12acdcf9a8c59bab98c4772c3b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173451"
---
# <a name="await-operator-c-reference"></a>bekleyen operatör (C# referans)

İşletici, `await` operand'ı temsil eden asynchronous işlemi tamamlanana kadar çevreleyen [async](../keywords/async.md) yönteminin değerlendirilmesini askıya alar. Eşkron işlem tamamlandığında, `await` operatör varsa operasyonun sonucunu döndürür. `await` Operatör zaten tamamlanmış işlemi temsil eden operand uygulandığında, çevreleyen yöntem in süspansiyon olmadan hemen işlem sonucunu döndürür. İşleç, `await` async yöntemini değerlendiren iş parçacığı engellemez. `await` İşleç çevreleyen async yöntemini askıya aldığında, denetim yöntemin arayana döner.

Aşağıdaki örnekte, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> yöntem tamamlandığında `Task<byte[]>` bir bayt dizisi üreten bir eşzamanlı işlemi temsil eden örneği döndürür. İşlem tamamlanana `await` kadar, operatör `DownloadDocsMainPageAsync` yöntemi askıya adakalır. Askıya `DownloadDocsMainPageAsync` alındığında, denetim ' `Main` yi arayan yönteme `DownloadDocsMainPageAsync`döndürülür. Yöntem, `Main` yöntem tarafından gerçekleştirilen eşzamanlı işlemin sonucuna ihtiyaç dolana `DownloadDocsMainPageAsync` kadar yürütülür. Tüm <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> baytlar aldığında, yöntemin `DownloadDocsMainPageAsync` geri kalanı değerlendirilir. Bundan sonra, yöntemin `Main` geri kalanı değerlendirilir.

[!code-csharp[await example](snippets/AwaitOperator.cs)]

Yukarıdaki örnek, C# 7.1 ile başlayan [ `Main` async yöntemini](../../programming-guide/main-and-command-args/index.md)kullanır. Daha fazla bilgi [için, Ana yöntem](#await-operator-in-the-main-method) bölümünde bekleyen işleci bakın.

> [!NOTE]
> Asynchronous programlamaya giriş için, [async ile Asynchronous programlama](../../programming-guide/concepts/async/index.md)bakın ve bekliyor. Asynchronous programlama `async` ile `await` ve [görev tabanlı asynchronous desen](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)izler.

İşlemciyi `await` yalnızca [async](../keywords/async.md) anahtar sözcüğü tarafından değiştirilen bir yöntem, [lambda ifadesi](../../programming-guide/statements-expressions-operators/lambda-expressions.md)veya [anonim yöntemle](delegate-operator.md) kullanabilirsiniz. Bir eşitleme yöntemi içinde, `await` işleci senkron bir işlevin gövdesinde, kilit [deyiminin](../keywords/lock-statement.md)bloğunda ve güvenli [olmayan](../keywords/unsafe.md) bir bağlamda kullanamazsınız.

`await` İşleticinin operand genellikle aşağıdaki .NET türlerinden <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>biridir: , , <xref:System.Threading.Tasks.ValueTask>, veya <xref:System.Threading.Tasks.ValueTask%601>. Ancak, herhangi bir bekleyen ifade `await` işleç operand olabilir. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Beklenilen İfadeler](~/_csharplang/spec/expressions.md#awaitable-expressions) bölümüne bakın.

C# 8.0 ile başlayarak, `await foreach` deyimi eşzamanlı veri akışını kullanmak için kullanabilirsiniz. Daha fazla bilgi [ `foreach` ](../keywords/foreach-in.md) için, [C# 8.0](../../whats-new/csharp-8.md) makalesindeki yeniliklerin ifade makalesine ve [Asynchronous akışları](../../whats-new/csharp-8.md#asynchronous-streams) bölümüne bakın.

`await t` İfade `TResult` türü, ifade `t` türü <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.ValueTask%601>. Türü `t` ise <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.ValueTask>, türü `await t` . `void` Her iki durumda `t` da, bir `await t` özel durum atarsa, özel durumu yeniden atar. Özel durum işleme hakkında daha fazla bilgi için, [try-catch deyimi](../keywords/try-catch.md) makalesinin [özel durumlar bölümüne](../keywords/try-catch.md#exceptions-in-async-methods) bakın.

Anahtar `async` `await` kelimeler C# 5 ve sonraki durumlarda mevcuttur.

## <a name="await-operator-in-the-main-method"></a>Ana yöntemde operatörü bekliyor

C# 7.1 ile başlayarak, uygulama giriş noktası olan `Task` `Task<int>` [ `Main` yöntem,](../../programming-guide/main-and-command-args/index.md)geri dönebilir veya , async `await` olmasını sağlayarak operatörü gövdesinde kullanabilirsiniz. Önceki C# sürümlerinde, yöntemin `Main` bir eşzamanlı işlemin tamamlanmasını beklediğinden emin olmak için, <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> ilgili async yöntemi tarafından döndürülen <xref:System.Threading.Tasks.Task%601> örneğin özelliğinin değerini alabilirsiniz. Değer üretmeyen eşzamanlı işlemler için <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> yöntemi arayabilirsiniz. Dil sürümünü nasıl seçiler hakkında bilgi için [C# dil sürümüne](../configure-language-version.md)bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Bekle ifadeleri](~/_csharplang/spec/expressions.md#await-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)
- [async](../keywords/async.md)
- [Zaman uyumsuz görev programlama modeli](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Zaman uyumsuz programlama](../../async.md)
- [Derinlemesine Async](../../../standard/async-in-depth.md)
- [Walkthrough: async kullanarak Web'e erişim ve bekleme](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Öğretici: C# 8.0 ve .NET Core 3.0 kullanarak async akışları oluşturun ve tüketin](../../tutorials/generate-consume-asynchronous-stream.md)
