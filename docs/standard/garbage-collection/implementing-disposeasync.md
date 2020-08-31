---
title: DisposeAsync metodu uygulama
description: Zaman uyumsuz kaynak Temizleme işlemini gerçekleştirmek için DisposeAsync ve Dispomevsimsynccore yöntemlerini nasıl uygulayacağınızı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 08/25/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 268cea7584040ad92e2da75e5e03112480cda93c
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053184"
---
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="93e3a-103">DisposeAsync metodu uygulama</span><span class="sxs-lookup"><span data-stu-id="93e3a-103">Implement a DisposeAsync method</span></span>

<span data-ttu-id="93e3a-104"><xref:System.IAsyncDisposable?displayProperty=nameWithType>Arabirim, C# 8,0 'nin bir parçası olarak sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="93e3a-104">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="93e3a-105"><xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> [Bir Dispose yöntemi uygularken](implementing-dispose.md)yaptığınız gibi, kaynak temizlik gerçekleştirmeniz gerektiğinde yöntemini uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93e3a-105">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="93e3a-106">Ancak, bu uygulamanın zaman uyumsuz temizleme işlemlerine izin verdiği önemli farklılıklardan biridir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-106">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="93e3a-107">, <xref:System.IAsyncDisposable.DisposeAsync> <xref:System.Threading.Tasks.ValueTask> Zaman uyumsuz Dispose işlemini temsil eden bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="93e3a-107">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="93e3a-108">Sınıfların de arabirimini uyguladığı arabirim, tipik olarak kullanılır <xref:System.IAsyncDisposable> <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="93e3a-108">It is typical when implementing the <xref:System.IAsyncDisposable> interface that classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="93e3a-109">Arabirimin iyi bir uygulama deseninin, <xref:System.IAsyncDisposable> zaman uyumlu ya da zaman uyumsuz Dispose için hazırlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-109">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous, or asynchronous dispose.</span></span> <span data-ttu-id="93e3a-110">Dispose deseninin uygulanması için tüm rehberlik, zaman uyumsuz uygulama için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-110">All of the guidance for implementing the dispose pattern also applies to the asynchronous implementation.</span></span> <span data-ttu-id="93e3a-111">Bu makalede, [bir Dispose yönteminin nasıl uygulanacağını](implementing-dispose.md)bildiğiniz varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-111">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="93e3a-112">DisposeAsync () ve Dispodeniz synccore ()</span><span class="sxs-lookup"><span data-stu-id="93e3a-112">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="93e3a-113"><xref:System.IAsyncDisposable>Arabirim, parametresiz tek bir yöntem bildirir <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="93e3a-113">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="93e3a-114">Korumalı olmayan herhangi bir sınıfın `DisposeAsyncCore()` , döndüren ek bir yöntemi olmalıdır <xref:System.Threading.Tasks.ValueTask> .</span><span class="sxs-lookup"><span data-stu-id="93e3a-114">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="93e3a-115">Parametresi olmayan bir `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> uygulama.</span><span class="sxs-lookup"><span data-stu-id="93e3a-115">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="93e3a-116">`protected virtual ValueTask DisposeAsyncCore()`İmzası şu şekilde olan bir yöntem:</span><span class="sxs-lookup"><span data-stu-id="93e3a-116">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a><span data-ttu-id="93e3a-117">DisposeAsync () yöntemi</span><span class="sxs-lookup"><span data-stu-id="93e3a-117">The DisposeAsync() method</span></span>

<span data-ttu-id="93e3a-118">`public`Parametresiz `DisposeAsync()` yöntemi bir bildirimde örtük olarak çağrılır `await using` ve amacı yönetilmeyen kaynakları serbest bırakmak, genel temizleme gerçekleştirmek ve bir tane varsa sonlandırıcının çalıştırılmaması gerektiğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, need not run.</span></span> <span data-ttu-id="93e3a-119">Yönetilen bir nesneyle ilişkili belleği serbest bırakma, her zaman [çöp toplayıcının](index.md)etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="93e3a-120">Bu nedenle, standart bir uygulaması vardır:</span><span class="sxs-lookup"><span data-stu-id="93e3a-120">Because of this, it has a standard implementation:</span></span>

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
> <span data-ttu-id="93e3a-121">Zaman uyumsuz Dispose deseninin, Dispose düzenine kıyasla bir birincil farkı, <xref:System.IAsyncDisposable.DisposeAsync> `Dispose(bool)` aşırı yükleme yöntemine yapılan çağrının `false` bir bağımsız değişken olarak verilme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="93e3a-122"><xref:System.IDisposable.Dispose?displayProperty=nameWithType>Yöntemi uygularken, `true` bunun yerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however; `true` is passed instead.</span></span> <span data-ttu-id="93e3a-123">Bu, zaman uyumlu Dispose düzeniyle işlevsel denklik sağlanmasına yardımcı olur ve Sonlandırıcı kod yollarının hala çağrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="93e3a-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="93e3a-124">Diğer bir deyişle, `DisposeAsyncCore()` Yöntem yönetilen kaynakları zaman uyumsuz olarak elden atıyor, bu nedenle bunları zaman uyumlu olarak atmak istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="93e3a-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="93e3a-125">Bu nedenle, `Dispose(false)` yerine çağırın `Dispose(true)` .</span><span class="sxs-lookup"><span data-stu-id="93e3a-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

### <a name="the-disposeasynccore-method"></a><span data-ttu-id="93e3a-126">Dispomevsimsynccore () yöntemi</span><span class="sxs-lookup"><span data-stu-id="93e3a-126">The DisposeAsyncCore() method</span></span>

<span data-ttu-id="93e3a-127">`DisposeAsyncCore()`Yöntemi, yönetilen kaynakların zaman uyumsuz temizliğini veya ' nin basamaklı çağrılarını gerçekleştirmek için tasarlanmıştır `DisposeAsync()` .</span><span class="sxs-lookup"><span data-stu-id="93e3a-127">The `DisposeAsyncCore()` method is intended to perform the asynchronous cleanup of managed resources or for cascading calls to `DisposeAsync()`.</span></span> <span data-ttu-id="93e3a-128">Bir alt sınıf, uygulamasının bir temel sınıfını devraldığında ortak zaman uyumsuz temizleme işlemlerini Kapsüller <xref:System.IAsyncDisposable> .</span><span class="sxs-lookup"><span data-stu-id="93e3a-128">It encapsulates the common asynchronous cleanup operations when a subclass inherits a base class that is an implementation of <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="93e3a-129">`DisposeAsyncCore()`Yöntemi, `virtual` türetilmiş sınıfların geçersiz Kılmalarda ek temizleme tanımlayabilmeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="93e3a-129">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

> [!TIP]
> <span data-ttu-id="93e3a-130">Bir uygulamasına <xref:System.IAsyncDisposable> ise `sealed` , `DisposeAsyncCore()` yöntemi gerekli değildir ve zaman uyumsuz temizleme doğrudan <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> yönteminde gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-130">If an implementation of <xref:System.IAsyncDisposable> is `sealed`, the `DisposeAsyncCore()` method is not needed, and the asynchronous cleanup can be performed directly in the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="93e3a-131">Zaman uyumsuz Dispose modelini uygulama</span><span class="sxs-lookup"><span data-stu-id="93e3a-131">Implement the async dispose pattern</span></span>

<span data-ttu-id="93e3a-132">Tüm korumalı olmayan sınıflar, devralınabileceğinden olası bir temel sınıf olarak düşünülmelidir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-132">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="93e3a-133">Herhangi bir olası temel sınıf için zaman uyumsuz Dispose modelini uygularsanız, yöntemini sağlamanız gerekir `protected virtual ValueTask DisposeAsyncCore()` .</span><span class="sxs-lookup"><span data-stu-id="93e3a-133">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="93e3a-134">Tarafından kullanılan zaman uyumsuz Dispose deseninin örnek bir uygulamasıdır <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="93e3a-134">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="93e3a-135">Önceki örnekte, kullanılır <xref:System.Text.Json.Utf8JsonWriter> .</span><span class="sxs-lookup"><span data-stu-id="93e3a-135">The preceding example uses the <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="93e3a-136">Hakkında daha fazla bilgi için `System.Text.Json` bkz. [Newtonsoft.Jsüzerinde System.Text.Jsüzerine geçiş](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="93e3a-136">For more information about `System.Text.Json`, see [How to migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="93e3a-137">Async atılabilir kullanma</span><span class="sxs-lookup"><span data-stu-id="93e3a-137">Using async disposable</span></span>

<span data-ttu-id="93e3a-138">Arabirimi uygulayan bir nesneyi düzgün bir şekilde kullanmak için <xref:System.IAsyncDisposable> [await](../../csharp/language-reference/operators/await.md)kullanın ve anahtar sözcükleri birlikte kullanabilirsiniz [using](../../csharp/language-reference/keywords/using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="93e3a-138">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md), and [using](../../csharp/language-reference/keywords/using-statement.md) keywords together.</span></span> <span data-ttu-id="93e3a-139">Aşağıdaki örneği, `ExampleAsyncDisposable` sınıfın örneklendiği ve sonra bir deyime sarmalanmış olduğunu göz önünde bulundurun `await using` .</span><span class="sxs-lookup"><span data-stu-id="93e3a-139">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated and then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="93e3a-140"><xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> <xref:System.IAsyncDisposable> Görevin devamlılığın orijinal bağlam veya Scheduler üzerinde nasıl sıraya alınacağını yapılandırmak için arabirimin genişletme yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="93e3a-140">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="93e3a-141">Hakkında daha fazla bilgi için `ConfigureAwait` bkz. [ConfigureAwait SSS](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span><span class="sxs-lookup"><span data-stu-id="93e3a-141">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="93e3a-142">Kullanımının `ConfigureAwait` gerekli olmadığı durumlarda, `await using` aşağıdaki gibi bir ifade basitleştirilir:</span><span class="sxs-lookup"><span data-stu-id="93e3a-142">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="93e3a-143">Ayrıca, bir [using bildiriminin](../../csharp/whats-new/csharp-8.md#using-declarations)örtük kapsamını kullanmak için yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="93e3a-143">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="93e3a-144">Yığılmış kullanımlar</span><span class="sxs-lookup"><span data-stu-id="93e3a-144">Stacked usings</span></span>

<span data-ttu-id="93e3a-145">Uygulayan birden çok nesne oluşturup kullandığınız durumlarda <xref:System.IAsyncDisposable> , `using` errant koşullarında yığınlama deyimlerinin çağrıları engelleyebileceği olasıdır <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="93e3a-145">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `using` statements in errant conditions could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="93e3a-146">Olası bir sorunu önlemeye yardımcı olmak için yığınlama zorunluluğunu ortadan kaldırmak ve bunun yerine bu örnek düzeni izlemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="93e3a-146">In order to help prevent potential concern, you should avoid stacking, and instead follow this example pattern:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a><span data-ttu-id="93e3a-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93e3a-147">See also</span></span>

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
