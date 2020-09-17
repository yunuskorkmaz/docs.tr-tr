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
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="79f61-103">DisposeAsync metodu uygulama</span><span class="sxs-lookup"><span data-stu-id="79f61-103">Implement a DisposeAsync method</span></span>

<span data-ttu-id="79f61-104"><xref:System.IAsyncDisposable?displayProperty=nameWithType>Arabirim, C# 8,0 'nin bir parçası olarak sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="79f61-104">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="79f61-105"><xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> [Bir Dispose yöntemi uygularken](implementing-dispose.md)yaptığınız gibi, kaynak temizlik gerçekleştirmeniz gerektiğinde yöntemini uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79f61-105">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="79f61-106">Ancak, bu uygulamanın zaman uyumsuz temizleme işlemlerine izin verdiği önemli farklılıklardan biridir.</span><span class="sxs-lookup"><span data-stu-id="79f61-106">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="79f61-107">, <xref:System.IAsyncDisposable.DisposeAsync> <xref:System.Threading.Tasks.ValueTask> Zaman uyumsuz Dispose işlemini temsil eden bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="79f61-107">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="79f61-108">Sınıfların de arabirimini uyguladığı arabirim, tipik olarak kullanılır <xref:System.IAsyncDisposable> <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="79f61-108">It is typical when implementing the <xref:System.IAsyncDisposable> interface that classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="79f61-109">Arabirimin iyi bir uygulama deseninin, <xref:System.IAsyncDisposable> zaman uyumlu ya da zaman uyumsuz Dispose için hazırlanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="79f61-109">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous or asynchronous dispose.</span></span> <span data-ttu-id="79f61-110">Dispose deseninin uygulanması için tüm rehberlik, zaman uyumsuz uygulama için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="79f61-110">All of the guidance for implementing the dispose pattern also applies to the asynchronous implementation.</span></span> <span data-ttu-id="79f61-111">Bu makalede, [bir Dispose yönteminin nasıl uygulanacağını](implementing-dispose.md)bildiğiniz varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79f61-111">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="79f61-112">DisposeAsync () ve Dispodeniz synccore ()</span><span class="sxs-lookup"><span data-stu-id="79f61-112">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="79f61-113"><xref:System.IAsyncDisposable>Arabirim, parametresiz tek bir yöntem bildirir <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="79f61-113">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="79f61-114">Korumalı olmayan herhangi bir sınıfın `DisposeAsyncCore()` , döndüren ek bir yöntemi olmalıdır <xref:System.Threading.Tasks.ValueTask> .</span><span class="sxs-lookup"><span data-stu-id="79f61-114">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="79f61-115">Parametresi olmayan bir `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> uygulama.</span><span class="sxs-lookup"><span data-stu-id="79f61-115">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="79f61-116">`protected virtual ValueTask DisposeAsyncCore()`İmzası şu şekilde olan bir yöntem:</span><span class="sxs-lookup"><span data-stu-id="79f61-116">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a><span data-ttu-id="79f61-117">DisposeAsync () yöntemi</span><span class="sxs-lookup"><span data-stu-id="79f61-117">The DisposeAsync() method</span></span>

<span data-ttu-id="79f61-118">`public`Parametresiz `DisposeAsync()` yöntemi bir bildirimde örtük olarak çağrılır `await using` ve amacı yönetilmeyen kaynakları serbest bırakmak, genel temizleme gerçekleştirmek ve bir tane varsa sonlandırıcının çalıştırılmaması gerektiğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79f61-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, need not run.</span></span> <span data-ttu-id="79f61-119">Yönetilen bir nesneyle ilişkili belleği serbest bırakma, her zaman [çöp toplayıcının](index.md)etki alanıdır.</span><span class="sxs-lookup"><span data-stu-id="79f61-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="79f61-120">Bu nedenle, standart bir uygulaması vardır:</span><span class="sxs-lookup"><span data-stu-id="79f61-120">Because of this, it has a standard implementation:</span></span>

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
> <span data-ttu-id="79f61-121">Zaman uyumsuz Dispose deseninin, Dispose düzenine kıyasla bir birincil farkı, <xref:System.IAsyncDisposable.DisposeAsync> `Dispose(bool)` aşırı yükleme yöntemine yapılan çağrının `false` bir bağımsız değişken olarak verilme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="79f61-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="79f61-122"><xref:System.IDisposable.Dispose?displayProperty=nameWithType>Ancak, yöntemi uygularken `true` bunun yerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="79f61-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however, `true` is passed instead.</span></span> <span data-ttu-id="79f61-123">Bu, zaman uyumlu Dispose düzeniyle işlevsel denklik sağlanmasına yardımcı olur ve Sonlandırıcı kod yollarının hala çağrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="79f61-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="79f61-124">Diğer bir deyişle, `DisposeAsyncCore()` Yöntem yönetilen kaynakları zaman uyumsuz olarak elden atıyor, bu nedenle bunları zaman uyumlu olarak atmak istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="79f61-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="79f61-125">Bu nedenle, `Dispose(false)` yerine çağırın `Dispose(true)` .</span><span class="sxs-lookup"><span data-stu-id="79f61-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

### <a name="the-disposeasynccore-method"></a><span data-ttu-id="79f61-126">Dispomevsimsynccore () yöntemi</span><span class="sxs-lookup"><span data-stu-id="79f61-126">The DisposeAsyncCore() method</span></span>

<span data-ttu-id="79f61-127">`DisposeAsyncCore()`Yöntemi, yönetilen kaynakların zaman uyumsuz temizliğini veya ' nin basamaklı çağrılarını gerçekleştirmek için tasarlanmıştır `DisposeAsync()` .</span><span class="sxs-lookup"><span data-stu-id="79f61-127">The `DisposeAsyncCore()` method is intended to perform the asynchronous cleanup of managed resources or for cascading calls to `DisposeAsync()`.</span></span> <span data-ttu-id="79f61-128">Bir alt sınıf, uygulamasının bir temel sınıfını devraldığında ortak zaman uyumsuz temizleme işlemlerini Kapsüller <xref:System.IAsyncDisposable> .</span><span class="sxs-lookup"><span data-stu-id="79f61-128">It encapsulates the common asynchronous cleanup operations when a subclass inherits a base class that is an implementation of <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="79f61-129">`DisposeAsyncCore()`Yöntemi, `virtual` türetilmiş sınıfların geçersiz Kılmalarda ek temizleme tanımlayabilmeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79f61-129">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

> [!TIP]
> <span data-ttu-id="79f61-130">Bir uygulamasına <xref:System.IAsyncDisposable> ise `sealed` , `DisposeAsyncCore()` yöntemi gerekli değildir ve zaman uyumsuz temizleme doğrudan <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> yönteminde gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="79f61-130">If an implementation of <xref:System.IAsyncDisposable> is `sealed`, the `DisposeAsyncCore()` method is not needed, and the asynchronous cleanup can be performed directly in the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="79f61-131">Zaman uyumsuz Dispose modelini uygulama</span><span class="sxs-lookup"><span data-stu-id="79f61-131">Implement the async dispose pattern</span></span>

<span data-ttu-id="79f61-132">Tüm korumalı olmayan sınıflar, devralınabileceğinden olası bir temel sınıf olarak düşünülmelidir.</span><span class="sxs-lookup"><span data-stu-id="79f61-132">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="79f61-133">Herhangi bir olası temel sınıf için zaman uyumsuz Dispose modelini uygularsanız, yöntemini sağlamanız gerekir `protected virtual ValueTask DisposeAsyncCore()` .</span><span class="sxs-lookup"><span data-stu-id="79f61-133">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="79f61-134">Tarafından kullanılan zaman uyumsuz Dispose deseninin örnek bir uygulamasıdır <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="79f61-134">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="79f61-135">Önceki örnekte, kullanılır <xref:System.Text.Json.Utf8JsonWriter> .</span><span class="sxs-lookup"><span data-stu-id="79f61-135">The preceding example uses the <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="79f61-136">Hakkında daha fazla bilgi için `System.Text.Json` bkz. [Newtonsoft.Jsüzerinde System.Text.Jsüzerine geçiş](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="79f61-136">For more information about `System.Text.Json`, see [How to migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="implement-both-dispose-and-async-dispose-patterns"></a><span data-ttu-id="79f61-137">Dispose ve Async Dispose desenleri uygulama</span><span class="sxs-lookup"><span data-stu-id="79f61-137">Implement both dispose and async dispose patterns</span></span>

<span data-ttu-id="79f61-138"><xref:System.IDisposable> <xref:System.IAsyncDisposable> Özellikle sınıf kapsamınız bu uygulamaların örneklerini içerdiğinde hem hem de arabirimlerini uygulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="79f61-138">You may need to implement both the <xref:System.IDisposable> and <xref:System.IAsyncDisposable> interfaces, especially when your class scope contains instances of these implementations.</span></span> <span data-ttu-id="79f61-139">Bunun yapılması, temizleme çağrılarını doğru bir şekilde basamaklı olarak belirleyebilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="79f61-139">Doing so ensures that you can properly cascade clean up calls.</span></span> <span data-ttu-id="79f61-140">Her iki arabirimi de uygulayan ve temizleme için uygun Kılavuzu gösteren örnek bir sınıf aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="79f61-140">Here is an example class that implements both interfaces and demonstrates the proper guidance for cleanup.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/dispose-and-disposeasync.cs":::

<span data-ttu-id="79f61-141"><xref:System.IDisposable.Dispose?displayProperty=nameWithType>Ve <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> uygulamaları hem basit ortak koddur.</span><span class="sxs-lookup"><span data-stu-id="79f61-141">The <xref:System.IDisposable.Dispose?displayProperty=nameWithType> and <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementations are both simple boilerplate code.</span></span>

<span data-ttu-id="79f61-142">`Dispose(bool)`Aşırı yükleme yönteminde, <xref:System.IDisposable> örnek koşullu olarak atıldı `null` .</span><span class="sxs-lookup"><span data-stu-id="79f61-142">In the `Dispose(bool)` overload method, the <xref:System.IDisposable> instance is conditionally disposed of if it is not `null`.</span></span> <span data-ttu-id="79f61-143"><xref:System.IAsyncDisposable>Örnek olarak atama yapılır <xref:System.IDisposable> ve aynı zamanda atılkdır `null` .</span><span class="sxs-lookup"><span data-stu-id="79f61-143">The <xref:System.IAsyncDisposable> instance is cast as <xref:System.IDisposable>, and if it is also not `null`, it is disposed of as well.</span></span> <span data-ttu-id="79f61-144">Her iki örnek de öğesine atanır `null` .</span><span class="sxs-lookup"><span data-stu-id="79f61-144">Both instances are then assigned to `null`.</span></span>

<span data-ttu-id="79f61-145">`DisposeAsyncCore()`Yöntemiyle aynı mantıksal yaklaşım izlenir.</span><span class="sxs-lookup"><span data-stu-id="79f61-145">With the `DisposeAsyncCore()` method, the same logical approach is followed.</span></span> <span data-ttu-id="79f61-146"><xref:System.IAsyncDisposable>Örnek değilse `null` , öğesine çağrısı `DisposeAsync().ConfigureAwait(false)` beklenir.</span><span class="sxs-lookup"><span data-stu-id="79f61-146">If the <xref:System.IAsyncDisposable> instance is not `null`, its call to `DisposeAsync().ConfigureAwait(false)` is awaited.</span></span> <span data-ttu-id="79f61-147"><xref:System.IDisposable>Örnek aynı zamanda bir uygulama ise <xref:System.IAsyncDisposable> , zaman uyumsuz olarak da atılmış olur.</span><span class="sxs-lookup"><span data-stu-id="79f61-147">If the <xref:System.IDisposable> instance is also an implementation of <xref:System.IAsyncDisposable>, it's also disposed of asynchronously.</span></span> <span data-ttu-id="79f61-148">Her iki örnek de öğesine atanır `null` .</span><span class="sxs-lookup"><span data-stu-id="79f61-148">Both instances are then assigned to `null`.</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="79f61-149">Async atılabilir kullanma</span><span class="sxs-lookup"><span data-stu-id="79f61-149">Using async disposable</span></span>

<span data-ttu-id="79f61-150">Arabirimi uygulayan bir nesneyi düzgün bir şekilde kullanmak için <xref:System.IAsyncDisposable> [await](../../csharp/language-reference/operators/await.md) kullanır ve anahtar sözcükleri birlikte [using](../../csharp/language-reference/keywords/using-statement.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79f61-150">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md) and [using](../../csharp/language-reference/keywords/using-statement.md) keywords together.</span></span> <span data-ttu-id="79f61-151">Aşağıdaki örneği, `ExampleAsyncDisposable` sınıfın örneklendiği ve sonra bir deyime sarmalanmış olduğunu göz önünde bulundurun `await using` .</span><span class="sxs-lookup"><span data-stu-id="79f61-151">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated and then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="79f61-152"><xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> <xref:System.IAsyncDisposable> Görevin devamlılığın orijinal bağlam veya Scheduler üzerinde nasıl sıraya alınacağını yapılandırmak için arabirimin genişletme yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="79f61-152">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="79f61-153">Hakkında daha fazla bilgi için `ConfigureAwait` bkz. [ConfigureAwait SSS](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span><span class="sxs-lookup"><span data-stu-id="79f61-153">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="79f61-154">Kullanımının `ConfigureAwait` gerekli olmadığı durumlarda, `await using` aşağıdaki gibi bir ifade basitleştirilir:</span><span class="sxs-lookup"><span data-stu-id="79f61-154">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="79f61-155">Ayrıca, bir [using bildiriminin](../../csharp/whats-new/csharp-8.md#using-declarations)örtük kapsamını kullanmak için yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="79f61-155">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="79f61-156">Yığılmış kullanımlar</span><span class="sxs-lookup"><span data-stu-id="79f61-156">Stacked usings</span></span>

<span data-ttu-id="79f61-157">Uygulayan birden çok nesne oluşturup kullandığınız durumlarda <xref:System.IAsyncDisposable> , `using` errant koşullarında yığınlama deyimlerinin çağrıları engelleyebileceği olasıdır <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="79f61-157">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `using` statements in errant conditions could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="79f61-158">Olası bir sorunu önlemeye yardımcı olmak için yığınlama zorunluluğunu ortadan kaldırmak ve bunun yerine bu örnek düzeni izlemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="79f61-158">In order to help prevent potential concern, you should avoid stacking, and instead follow this example pattern:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a><span data-ttu-id="79f61-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79f61-159">See also</span></span>

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
