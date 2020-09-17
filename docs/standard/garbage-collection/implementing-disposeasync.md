---
title: DisposeAsync metodu uygulama
description: Zaman uyumsuz kaynak Temizleme işlemini gerçekleştirmek için DisposeAsync ve Dispomevsimsynccore yöntemlerini nasıl uygulayacağınızı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 6ddfd860571d883e20fdb18985fe2bc2d9477dec
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720289"
---
# <a name="implement-a-disposeasync-method"></a>DisposeAsync metodu uygulama

<xref:System.IAsyncDisposable?displayProperty=nameWithType>Arabirim, C# 8,0 'nin bir parçası olarak sunulmuştur. <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> [Bir Dispose yöntemi uygularken](implementing-dispose.md)yaptığınız gibi, kaynak temizlik gerçekleştirmeniz gerektiğinde yöntemini uygulayabilirsiniz. Ancak, bu uygulamanın zaman uyumsuz temizleme işlemlerine izin verdiği önemli farklılıklardan biridir. , <xref:System.IAsyncDisposable.DisposeAsync> <xref:System.Threading.Tasks.ValueTask> Zaman uyumsuz Dispose işlemini temsil eden bir döndürür.

Sınıfların de arabirimini uyguladığı arabirim, tipik olarak kullanılır <xref:System.IAsyncDisposable> <xref:System.IDisposable> . Arabirimin iyi bir uygulama deseninin, <xref:System.IAsyncDisposable> zaman uyumlu ya da zaman uyumsuz Dispose için hazırlanmasıdır. Dispose deseninin uygulanması için tüm rehberlik, zaman uyumsuz uygulama için de geçerlidir. Bu makalede, [bir Dispose yönteminin nasıl uygulanacağını](implementing-dispose.md)bildiğiniz varsayılmaktadır.

## <a name="disposeasync-and-disposeasynccore"></a>DisposeAsync () ve Dispodeniz synccore ()

<xref:System.IAsyncDisposable>Arabirim, parametresiz tek bir yöntem bildirir <xref:System.IAsyncDisposable.DisposeAsync> . Korumalı olmayan herhangi bir sınıfın `DisposeAsyncCore()` , döndüren ek bir yöntemi olmalıdır <xref:System.Threading.Tasks.ValueTask> .

- Parametresi olmayan bir `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> uygulama.
- `protected virtual ValueTask DisposeAsyncCore()`İmzası şu şekilde olan bir yöntem:

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a>DisposeAsync () yöntemi

`public`Parametresiz `DisposeAsync()` yöntemi bir bildirimde örtük olarak çağrılır `await using` ve amacı yönetilmeyen kaynakları serbest bırakmak, genel temizleme gerçekleştirmek ve bir tane varsa sonlandırıcının çalıştırılmaması gerektiğini belirtmek için kullanılır. Yönetilen bir nesneyle ilişkili belleği serbest bırakma, her zaman [çöp toplayıcının](index.md)etki alanıdır. Bu nedenle, standart bir uygulaması vardır:

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of unmanaged resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> Zaman uyumsuz Dispose deseninin, Dispose düzenine kıyasla bir birincil farkı, <xref:System.IAsyncDisposable.DisposeAsync> `Dispose(bool)` aşırı yükleme yöntemine yapılan çağrının `false` bir bağımsız değişken olarak verilme yöntemidir. <xref:System.IDisposable.Dispose?displayProperty=nameWithType>Ancak, yöntemi uygularken `true` bunun yerine geçirilir. Bu, zaman uyumlu Dispose düzeniyle işlevsel denklik sağlanmasına yardımcı olur ve Sonlandırıcı kod yollarının hala çağrılmasını sağlar. Diğer bir deyişle, `DisposeAsyncCore()` Yöntem yönetilen kaynakları zaman uyumsuz olarak elden atıyor, bu nedenle bunları zaman uyumlu olarak atmak istemezsiniz. Bu nedenle, `Dispose(false)` yerine çağırın `Dispose(true)` .

### <a name="the-disposeasynccore-method"></a>Dispomevsimsynccore () yöntemi

`DisposeAsyncCore()`Yöntemi, yönetilen kaynakların zaman uyumsuz temizliğini veya ' nin basamaklı çağrılarını gerçekleştirmek için tasarlanmıştır `DisposeAsync()` . Bir alt sınıf, uygulamasının bir temel sınıfını devraldığında ortak zaman uyumsuz temizleme işlemlerini Kapsüller <xref:System.IAsyncDisposable> . `DisposeAsyncCore()`Yöntemi, `virtual` türetilmiş sınıfların geçersiz Kılmalarda ek temizleme tanımlayabilmeleri için kullanılır.

> [!TIP]
> Bir uygulamasına <xref:System.IAsyncDisposable> ise `sealed` , `DisposeAsyncCore()` yöntemi gerekli değildir ve zaman uyumsuz temizleme doğrudan <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> yönteminde gerçekleştirilebilir.

## <a name="implement-the-async-dispose-pattern"></a>Zaman uyumsuz Dispose modelini uygulama

Tüm korumalı olmayan sınıflar, devralınabileceğinden olası bir temel sınıf olarak düşünülmelidir. Herhangi bir olası temel sınıf için zaman uyumsuz Dispose modelini uygularsanız, yöntemini sağlamanız gerekir `protected virtual ValueTask DisposeAsyncCore()` . Tarafından kullanılan zaman uyumsuz Dispose deseninin örnek bir uygulamasıdır <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

Önceki örnekte, kullanılır <xref:System.Text.Json.Utf8JsonWriter> . Hakkında daha fazla bilgi için `System.Text.Json` bkz. [Newtonsoft.Jsüzerinde System.Text.Jsüzerine geçiş](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).

## <a name="implement-both-dispose-and-async-dispose-patterns"></a>Dispose ve Async Dispose desenleri uygulama

<xref:System.IDisposable> <xref:System.IAsyncDisposable> Özellikle sınıf kapsamınız bu uygulamaların örneklerini içerdiğinde hem hem de arabirimlerini uygulamanız gerekebilir. Bunun yapılması, temizleme çağrılarını doğru bir şekilde basamaklı olarak belirleyebilmenizi sağlar. Her iki arabirimi de uygulayan ve temizleme için uygun Kılavuzu gösteren örnek bir sınıf aşağıda verilmiştir.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/dispose-and-disposeasync.cs":::

<xref:System.IDisposable.Dispose?displayProperty=nameWithType>Ve <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> uygulamaları hem basit ortak koddur.

`Dispose(bool)`Aşırı yükleme yönteminde, <xref:System.IDisposable> örnek koşullu olarak atıldı `null` . <xref:System.IAsyncDisposable>Örnek olarak atama yapılır <xref:System.IDisposable> ve aynı zamanda atılkdır `null` . Her iki örnek de öğesine atanır `null` .

`DisposeAsyncCore()`Yöntemiyle aynı mantıksal yaklaşım izlenir. <xref:System.IAsyncDisposable>Örnek değilse `null` , öğesine çağrısı `DisposeAsync().ConfigureAwait(false)` beklenir. <xref:System.IDisposable>Örnek aynı zamanda bir uygulama ise <xref:System.IAsyncDisposable> , zaman uyumsuz olarak da atılmış olur. Her iki örnek de öğesine atanır `null` .

## <a name="using-async-disposable"></a>Async atılabilir kullanma

Arabirimi uygulayan bir nesneyi düzgün bir şekilde kullanmak için <xref:System.IAsyncDisposable> [await](../../csharp/language-reference/operators/await.md) kullanır ve anahtar sözcükleri birlikte [using](../../csharp/language-reference/keywords/using-statement.md) kullanabilirsiniz. Aşağıdaki örneği, `ExampleAsyncDisposable` sınıfın örneklendiği ve sonra bir deyime sarmalanmış olduğunu göz önünde bulundurun `await using` .

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> <xref:System.IAsyncDisposable> Görevin devamlılığın orijinal bağlam veya Scheduler üzerinde nasıl sıraya alınacağını yapılandırmak için arabirimin genişletme yöntemini kullanın. Hakkında daha fazla bilgi için `ConfigureAwait` bkz. [ConfigureAwait SSS](https://devblogs.microsoft.com/dotnet/configureawait-faq/).

Kullanımının `ConfigureAwait` gerekli olmadığı durumlarda, `await using` aşağıdaki gibi bir ifade basitleştirilir:

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

Ayrıca, bir [using bildiriminin](../../csharp/whats-new/csharp-8.md#using-declarations)örtük kapsamını kullanmak için yazılabilir.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a>Yığılmış kullanımlar

Uygulayan birden çok nesne oluşturup kullandığınız durumlarda <xref:System.IAsyncDisposable> , `using` errant koşullarında yığınlama deyimlerinin çağrıları engelleyebileceği olasıdır <xref:System.IAsyncDisposable.DisposeAsync> . Olası bir sorunu önlemeye yardımcı olmak için yığınlama zorunluluğunu ortadan kaldırmak ve bunun yerine bu örnek düzeni izlemeniz gerekir:

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
