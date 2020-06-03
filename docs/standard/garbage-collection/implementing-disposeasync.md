---
title: DisposeAsync yöntemi uygulama
description: ''
ms.date: 06/02/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: c4f541d5a4f5b5fd31b344a299789d86cd78424c
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84311016"
---
# <a name="implement-a-disposeasync-method"></a>DisposeAsync yöntemi uygulama

<xref:System.IAsyncDisposable?displayProperty=nameWithType>Arabirim, C# 8,0 'nin bir parçası olarak sunulmuştur. <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> [Bir Dispose yöntemi uygularken](implementing-dispose.md)yaptığınız gibi, kaynak temizlik gerçekleştirmeniz gerektiğinde yöntemini uygulayabilirsiniz. Ancak, bu uygulamanın zaman uyumsuz temizleme işlemlerine izin verdiği önemli farklılıklardan biridir. , <xref:System.IAsyncDisposable.DisposeAsync> <xref:System.Threading.Tasks.ValueTask> Zaman uyumsuz Dispose işlemini temsil eden bir döndürür.

Arabirim uygulama sırasında <xref:System.IAsyncDisposable> , sınıfların de arabirimini uyguladığı tipik bir işlem olur <xref:System.IDisposable> . Arabirimin iyi bir uygulama deseninin, <xref:System.IAsyncDisposable> zaman uyumlu ya da zaman uyumsuz Dispose için hazırlanması gerekir. Dispose deseninin uygulanması için tüm rehberlik, zaman uyumsuz uygulama için geçerlidir. Bu makalede, [bir Dispose yönteminin nasıl uygulanacağını](implementing-dispose.md)bildiğiniz varsayılmaktadır.

## <a name="disposeasync-and-disposeasynccore"></a>DisposeAsync () ve Dispodeniz synccore ()

<xref:System.IAsyncDisposable>Arabirim, parametresiz tek bir yöntem bildirir <xref:System.IAsyncDisposable.DisposeAsync> . Korumalı olmayan herhangi bir sınıfın `DisposeAsyncCore()` , döndüren ek bir yöntemi olmalıdır <xref:System.Threading.Tasks.ValueTask> .

- Parametresi olmayan bir `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> uygulama.
- `protected virtual ValueTask DisposeAsyncCore()`İmzası şu şekilde olan bir yöntem:

```csharp
protected virtual ValueTask DisposeAsyncCore()
{
}
```

`DisposeAsyncCore()`Yöntemi, `virtual` türetilmiş sınıfların geçersiz Kılmalarda ek temizleme tanımlayabilmeleri için kullanılır.

### <a name="the-disposeasync-method"></a>DisposeAsync () yöntemi

`public`Parametresiz `DisposeAsync()` yöntemi bir bildirimde örtük olarak çağrılır `await using` ve amacı yönetilmeyen kaynakları serbest bırakmak, genel temizleme gerçekleştirmek ve bir varsa sonlandırıcının mevcut olduğunu belirtmek için gerekli değildir. Yönetilen bir nesneyle ilişkili belleği serbest bırakma, her zaman [çöp toplayıcının](index.md)etki alanıdır. Bu nedenle, standart bir uygulaması vardır:

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of managed resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> Zaman uyumsuz Dispose deseninin, Dispose düzenine kıyasla bir birincil farkı, <xref:System.IAsyncDisposable.DisposeAsync> `Dispose(bool)` aşırı yükleme yöntemine yapılan çağrının `false` bir bağımsız değişken olarak verilme yöntemidir. <xref:System.IDisposable.Dispose?displayProperty=nameWithType>Yöntemi uygularken, `true` bunun yerine geçirilir. Bu, zaman uyumlu Dispose düzeniyle işlevsel denklik sağlanmasına yardımcı olur ve Sonlandırıcı kod yollarının hala çağrılmasını sağlar. Diğer bir deyişle, `DisposeAsyncCore()` Yöntem yönetilen kaynakları zaman uyumsuz olarak elden atıyor, bu nedenle bunları zaman uyumlu olarak atmak istemezsiniz. Bu nedenle, `Dispose(false)` yerine çağırın `Dispose(true)` .

## <a name="implement-the-async-dispose-pattern"></a>Zaman uyumsuz Dispose modelini uygulama

Tüm korumalı olmayan sınıflar, devralınabileceğinden olası bir temel sınıf olarak düşünülmelidir. Herhangi bir olası temel sınıf için zaman uyumsuz Dispose modelini uygularsanız, yöntemini sağlamanız gerekir `protected virtual ValueTask DisposeAsyncCore()` . Tarafından kullanılan zaman uyumsuz Dispose deseninin örnek bir uygulamasıdır <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

Önceki örnekte kullanılan, <xref:System.Text.Json.Utf8JsonWriter> hakkında daha fazla bilgi için, `System.Text.Json` bkz. [Newtonsoft. JSON 'Dan System. Text. JSON 'a geçiş](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).

## <a name="using-async-disposable"></a>Async atılabilir kullanma

Arabirimi uygulayan bir nesneyi düzgün bir şekilde kullanmak için <xref:System.IAsyncDisposable> [await](../../csharp/language-reference/operators/await.md)kullanın ve anahtar sözcükleri birlikte kullanabilirsiniz [using](../../csharp/language-reference/keywords/using.md) . `ExampleAsyncDisposable`Sınıfının örneği oluşturulan ve sonra bir deyime kaydırılan aşağıdaki örneği göz önünde bulundurun `await using` .

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
