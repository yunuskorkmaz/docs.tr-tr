---
title: Bellek<T> ve aralık<T> kullanım yönergeleri
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 728f360d2e8f93ebdf2b17fec39477b95ed11357
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063287"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="e7390-102">Bellek\<T > ve aralık\<T > kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e7390-102">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="e7390-103">.NET core, bir rastgele bitişik bellek bölgesini temsil eden türler içerir.</span><span class="sxs-lookup"><span data-stu-id="e7390-103">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="e7390-104">.NET core 2.0 kullanılmaya <xref:System.Span%601> ve <xref:System.ReadOnlySpan%601>, yönetilen veya yönetilmeyen bellek tarafından yedeklenen hafif bellek arabelleği olduğu.</span><span class="sxs-lookup"><span data-stu-id="e7390-104">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="e7390-105">Yığın üzerinde bu türleri depolanabilir olduğundan, bunlar zaman uyumsuz yöntem çağrıları gibi senaryolar, bir dizi için uygun değil.</span><span class="sxs-lookup"><span data-stu-id="e7390-105">Because these types can be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="e7390-106">.NET core 2.1 ekler gibi ek türleri sayısı <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, ve <xref:System.Buffers.MemoryPool%601>.</span><span class="sxs-lookup"><span data-stu-id="e7390-106">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="e7390-107">Gibi <xref:System.Span%601>, <xref:System.Memory%601> ve ilgili türlerinden tarafından yönetilen ve yönetilmeyen bellek yedeklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e7390-107">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="e7390-108">Farklı <xref:System.Span%601>, <xref:System.Memory%601> yalnızca yönetilen yığında depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="e7390-108">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can only be stored on the managed heap.</span></span>

<span data-ttu-id="e7390-109">Her ikisi de <xref:System.Span%601> ve <xref:System.Memory%601> hatlarında kullanılabilir yapılandırılmış verilerin arabellek.</span><span class="sxs-lookup"><span data-stu-id="e7390-109">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="e7390-110">Böylece onları işleyebilir ve isteğe bağlı olarak önbelleği değiştiren bileşenleri için ardışık düzeninde, bazı veya tüm verileri verimli bir şekilde geçirilebilir diğer bir deyişle, bunlar tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e7390-110">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="e7390-111">Çünkü <xref:System.Memory%601> ve ilgili türlerinden erişilebilir birden çok bileşen veya birden çok iş parçacığı tarafından geliştiricilerin güçlü kod üretmek için bazı standart kullanım yönergeleri takip edin önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e7390-111">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="e7390-112">Sahipleri, tüketicilere ve ömür Yönetimi</span><span class="sxs-lookup"><span data-stu-id="e7390-112">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="e7390-113">Arabellekler etrafında ve API arasında arabelleklere bazen birden çok iş parçacığı tarafından erişilebilir olduğundan geçirilebilir olduğundan, ömür Yönetimi dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e7390-113">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="e7390-114">Üç temel kavram vardır:</span><span class="sxs-lookup"><span data-stu-id="e7390-114">There are three core concepts:</span></span>

- <span data-ttu-id="e7390-115">**Sahipliği**.</span><span class="sxs-lookup"><span data-stu-id="e7390-115">**Ownership**.</span></span> <span data-ttu-id="e7390-116">Sahibi bir arabellek örneğinin kullanım ömrü Yönetimi artık kullanımda olmadığında arabellek yok etme içeren sorumludur.</span><span class="sxs-lookup"><span data-stu-id="e7390-116">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="e7390-117">Tüm arabellekler tek bir sahip.</span><span class="sxs-lookup"><span data-stu-id="e7390-117">All buffers have a single owner.</span></span> <span data-ttu-id="e7390-118">Genellikle sahibi, arabellek oluşturulan veya, bir fabrikadan arabelleğe alınan bileşendir.</span><span class="sxs-lookup"><span data-stu-id="e7390-118">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="e7390-119">Sahiplik da aktarılabilir; **Bileşen A** arabelleğe denetimin teknisyene **bileşeni B**, hangi noktada **bileşen A** arabellek artık kullanabilir ve **bileşen B**  artık kullanımda olmadığında arabellek yok etme için sorumlu olur.</span><span class="sxs-lookup"><span data-stu-id="e7390-119">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="e7390-120">**Tüketim**.</span><span class="sxs-lookup"><span data-stu-id="e7390-120">**Consumption**.</span></span> <span data-ttu-id="e7390-121">Tüketici bir arabellek örneğinin arabellek örneği buradan okuma ve büyük olasılıkla yazma kullanmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="e7390-121">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="e7390-122">Bazı dış eşitleme mekanizması sağlanmadığı sürece arabellekler aynı anda tek bir tüketici olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7390-122">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="e7390-123">Etkin kullanıcısı olan bir arabellek arabellek sahibi olmak zorunda olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e7390-123">Note that the active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="e7390-124">**Kira**.</span><span class="sxs-lookup"><span data-stu-id="e7390-124">**Lease**.</span></span> <span data-ttu-id="e7390-125">Belirli bir bileşene arabellek tüketici izin verilen süre kira var.</span><span class="sxs-lookup"><span data-stu-id="e7390-125">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="e7390-126">Aşağıdaki sözde kod örneği, bu üç kavramı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7390-126">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="e7390-127">İçerdiği bir `Main` başlatan yöntem bir <xref:System.Memory%601> arabellek türü <xref:System.Char>, çağrıları `WriteInt32ToBuffer` tamsayı dize gösterimini arabellek ve ardından çağrıları yazma yöntemi `DisplayBufferToConsole` değerini görüntülemek için yöntemi arabellek.</span><span class="sxs-lookup"><span data-stu-id="e7390-127">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

```csharp
using System;

class Program
{
    // Write 'value' as a human-readable string to the output buffer.
    void WriteInt32ToBuffer(int value, Buffer buffer);

    // Display the contents of the buffer to the console.
    void DisplayBufferToConsole(Buffer buffer);

    // Application code
    static void Main()
    {
        var buffer = CreateBuffer();
        try
        {
            int value = Int32.Parse(Console.ReadLine());
            WriteInt32ToBuffer(value, buffer);
            DisplayBufferToConsole(buffer);
        }
        finally
        {
            buffer.Destroy();
        }
    }
}
```

<span data-ttu-id="e7390-128">`Main` Yöntemi arabellek oluşturur (Bu durumda bir <xref:System.Span%601> örnek) sahibi olur.</span><span class="sxs-lookup"><span data-stu-id="e7390-128">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="e7390-129">Bu nedenle, `Main` artık kullanımda olmadığında arabellek yok etme için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="e7390-129">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="e7390-130">Bunu arabellek çağırarak yapar <xref:System.Span%601.Clear?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e7390-130">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e7390-131">( <xref:System.Span%601.Clear> Yöntemi burada gerçekten temizler arabellek belleği; <xref:System.Span%601> yapısı gerçekten arabellek yok eder bir yöntem yok.)</span><span class="sxs-lookup"><span data-stu-id="e7390-131">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="e7390-132">Arabellek iki Tüketiciler, sahip `WriteInt32ToBuffer` ve `DisplayBufferToConsole`.</span><span class="sxs-lookup"><span data-stu-id="e7390-132">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="e7390-133">Aynı anda yalnızca tek bir tüketici yoktur (ilk `WriteInt32ToBuffer`, ardından `DisplayBufferToConsole`), ve tüketiciler hiçbiri arabellek sahip.</span><span class="sxs-lookup"><span data-stu-id="e7390-133">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="e7390-134">Ayrıca, bu bağlamda "Müşteri" bir salt okunur görünüm arabellek yaptığından emin değil unutmayın; Tüketiciler arabellek içeriği olarak değiştirebilirsiniz `WriteInt32ToBuffer` bir arabellek okuma/yazma görünümünü verildiyse yapar.</span><span class="sxs-lookup"><span data-stu-id="e7390-134">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="e7390-135">`WriteInt32ToBuffer` Yöntemi sahip bir kira (kullanabilir) yöntem çağrısının başlangıcı ve yöntemi döndürür. saat arasındaki arabellek.</span><span class="sxs-lookup"><span data-stu-id="e7390-135">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="e7390-136">Benzer şekilde, `DisplayBufferToConsole` Yürütülüyor iken arabelleği bir kira var ve yöntem geriye doğru izler kira serbest kalır.</span><span class="sxs-lookup"><span data-stu-id="e7390-136">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="e7390-137">(Kiralama yönetimi için hiçbir API yoktur; "kira" kavramsal bir konudur.)</span><span class="sxs-lookup"><span data-stu-id="e7390-137">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="e7390-138">Bellek\<T > ve sahibi/tüketici modeli</span><span class="sxs-lookup"><span data-stu-id="e7390-138">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="e7390-139">Olarak [sahipleri, tüketicilere ve ömür Yönetimi](#owners-consumers-and-lifetime-management) bölümünde Not, bir arabellek her zaman bir sahip vardır.</span><span class="sxs-lookup"><span data-stu-id="e7390-139">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="e7390-140">.NET core iki sahipliği modeli destekler:</span><span class="sxs-lookup"><span data-stu-id="e7390-140">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="e7390-141">Tek sahipliği destekleyen bir model.</span><span class="sxs-lookup"><span data-stu-id="e7390-141">A model that supports single ownership.</span></span> <span data-ttu-id="e7390-142">Arabellek tüm yaşam süresi için tek bir kullanıcıya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e7390-142">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="e7390-143">Bir modeli sahipliğinin aktarılmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="e7390-143">A model that supports ownership transfer.</span></span> <span data-ttu-id="e7390-144">Arabellek sahipliğini özgün sahibi (oluşturana), ardından arabellek ömür yönetimi için sorumlu olur başka bir bileşene aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7390-144">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="e7390-145">Bu sahibi sırayla sahipliğini başka bir bileşene ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="e7390-145">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="e7390-146">Kullandığınız <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> açıkça bir arabellek sahipliğini yönetmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="e7390-146">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="e7390-147"><xref:System.Buffers.IMemoryOwner%601> Her iki sahipliği modelleri destekler.</span><span class="sxs-lookup"><span data-stu-id="e7390-147"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="e7390-148">Sahip bileşen bir <xref:System.Buffers.IMemoryOwner%601> başvuru arabellek sahip.</span><span class="sxs-lookup"><span data-stu-id="e7390-148">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="e7390-149">Aşağıdaki örnekte bir <xref:System.Buffers.IMemoryOwner%601?> sahipliğini yansıtmak için örnek bir <xref:System.Memory%601> arabellek.</span><span class="sxs-lookup"><span data-stu-id="e7390-149">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of an <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="e7390-150">Bu örnekle aynı zamanda yazabiliriz [ `using` ](~/docs/csharp/language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="e7390-150">We can also write this example with the [`using`](~/docs/csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="e7390-151">Bu kod:</span><span class="sxs-lookup"><span data-stu-id="e7390-151">In this code:</span></span>

- <span data-ttu-id="e7390-152">`Main` Yöntemi başvuru tutan <xref:System.Buffers.IMemoryOwner%601> örneği, bu nedenle `Main` yöntemi arabellek sahibidir.</span><span class="sxs-lookup"><span data-stu-id="e7390-152">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="e7390-153">`WriteInt32ToBuffer` Ve `DisplayBufferToConsole` yöntemleri kabul <xref:System.Memory%601> Genel API olarak.</span><span class="sxs-lookup"><span data-stu-id="e7390-153">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="e7390-154">Bu nedenle, arabellek tüketicilerinin altındadır.</span><span class="sxs-lookup"><span data-stu-id="e7390-154">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="e7390-155">Ve bunların yalnızca birini tüketicilerimizin birer güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="e7390-155">And they only consume it one at a time.</span></span>

<span data-ttu-id="e7390-156">Ancak `WriteInt32ToBuffer` yöntemi bir değer arabelleğe yazmak için tasarlanmıştır `DisplayBufferToConsole` yöntemi değildir.</span><span class="sxs-lookup"><span data-stu-id="e7390-156">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="e7390-157">Bunu yansıtmak için onu türünde bir bağımsız değişken kabul ettiğini <xref:System.ReadOnlyMemory%601>.</span><span class="sxs-lookup"><span data-stu-id="e7390-157">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="e7390-158">Hakkında daha fazla bilgi için <xref:System.ReadOnlyMemory%601>, bkz: [Kural 2: ReadOnlySpan kullanın\<T > ya da ReadOnlyMemory\<T > salt okunur arabellek olması gerekiyorsa](#rule-2).</span><span class="sxs-lookup"><span data-stu-id="e7390-158">For additional information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="e7390-159">"Ownerless" bellek\<T > örnekleri</span><span class="sxs-lookup"><span data-stu-id="e7390-159">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="e7390-160">Oluşturabileceğiniz bir <xref:System.Memory%601> kullanmadan örneği <xref:System.Buffers.IMemoryOwner%601>.</span><span class="sxs-lookup"><span data-stu-id="e7390-160">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="e7390-161">Bu durumda, arabellek sahiplik açık ve yalnızca yerine örtük tek sahip model desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e7390-161">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="e7390-162">Bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e7390-162">You can do this by:</span></span>

- <span data-ttu-id="e7390-163">Birini çağırma <xref:System.Memory%601> oluşturucular doğrudan öğesinde geçen bir `T[]`, aşağıdaki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="e7390-163">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="e7390-164">Çağırma [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) üretmek için genişletme yöntemi bir `ReadOnlyMemory<char>` örneği.</span><span class="sxs-lookup"><span data-stu-id="e7390-164">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="e7390-165">Başlangıçta oluşturan yöntemine <xref:System.Memory%601> arabellek örtük sahibi örneğidir.</span><span class="sxs-lookup"><span data-stu-id="e7390-165">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="e7390-166">Sahipliği olduğundan başka bir bileşen için aktarılamaz hiçbir <xref:System.Buffers.IMemoryOwner%601> aktarımı kolaylaştırmak için örneği.</span><span class="sxs-lookup"><span data-stu-id="e7390-166">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="e7390-167">(Alternatif olarak, ayrıca çalışma zamanının atık toplayıcısı arabellek sahibi ve tüm yöntemleri yalnızca arabellek tüketen hayal edebilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="e7390-167">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="e7390-168">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e7390-168">Usage guidelines</span></span>

<span data-ttu-id="e7390-169">Bir bellek bloğuna sahip olduğu ancak bazıları çalışan belirli bellek bloğu üzerinde aynı anda birden çok bileşeni için geçirilecek yöneliktir çünkü her ikisi de kullanma yönergeleri kurmak daha önemlidir <xref:System.Memory%601> ve <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="e7390-169">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="e7390-170">Yönergeleri gereklidir çünkü:</span><span class="sxs-lookup"><span data-stu-id="e7390-170">Guidelines are necessary because:</span></span>

- <span data-ttu-id="e7390-171">Bir bileşen sahibi kullanıma sundu sonra bellek bloğu için bir başvuru korumak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e7390-171">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="e7390-172">Bir bileşen başka bir bileşen üzerinde arabellekteki verileri bozmasına işlemde çalıştığından aynı anda bir arabellek üzerinde çalışılacak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e7390-172">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="e7390-173">Yığın ayırma yapısını while <xref:System.Span%601> performansı en iyi duruma getirir ve yapar <xref:System.Span%601> Ayrıca, bir bellek bloğu üzerinde çalışmak tercih edilen türünü konuları <xref:System.Span%601> bazı önemli kısıtlamaları.</span><span class="sxs-lookup"><span data-stu-id="e7390-173">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="e7390-174">Ne zaman kullanılacağını bilmek önemlidir bir <xref:System.Span%601> ve ne zaman kullanılacağı <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="e7390-174">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="e7390-175">Aşağıdakiler önerilerimizle başarıyla kullanmak için <xref:System.Memory%601> ve ilgili türleri.</span><span class="sxs-lookup"><span data-stu-id="e7390-175">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="e7390-176">Geçerli Kılavuzu unutmayın <xref:System.Memory%601> ve <xref:System.Span%601> için de geçerlidir <xref:System.ReadOnlyMemory%601> ve <xref:System.ReadOnlySpan%601> sürece biz açıkça aksi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e7390-176">Note that guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="e7390-177">**Kural #1: Aralık için zaman uyumlu bir API kullanmak\<T > bellek yerine\<T > mümkünse bir parametre olarak.**</span><span class="sxs-lookup"><span data-stu-id="e7390-177">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="e7390-178"><xref:System.Span%601> Daha fazla yönlüdür <xref:System.Memory%601> ve çok çeşitli bitişik bellek arabelleği temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="e7390-178"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="e7390-179"><xref:System.Span%601> Ayrıca performans teklifler daha iyi <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="e7390-179"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="e7390-180">Son olarak, kullanabileceğiniz <xref:System.Memory%601.Span?displayProperty=nameWithType> dönüştürmek için özellik bir <xref:System.Memory%601> için örnek bir <xref:System.Span%601>, aralık ancak\<T > - to - bellek\<T > dönüştürme mümkün değil.</span><span class="sxs-lookup"><span data-stu-id="e7390-180">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="e7390-181">Bunu, Arayanların varsa bir <xref:System.Memory%601> örneği, bunlar yapabileceksiniz yöntemlerinizi ile çağrılacak <xref:System.Span%601> parametreleri yine de.</span><span class="sxs-lookup"><span data-stu-id="e7390-181">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="e7390-182">Türünde bir parametre kullanarak <xref:System.Span%601> tür yerine <xref:System.Memory%601> de doğru kullanan bir yöntem uygulaması yazma yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e7390-182">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="e7390-183">Derleme zamanı denetimleri, arabellek, yöntemin kira (daha sonra bu) ötesinde erişmeye çalıştığınız değil emin olmak için otomatik olarak alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e7390-183">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="e7390-184">Bazı durumlarda kullanmak zorunda kalırsınız bir <xref:System.Memory%601> yerine parametre bir <xref:System.Span%601> parametresi, tam olarak zaman uyumlu olsa bile.</span><span class="sxs-lookup"><span data-stu-id="e7390-184">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="e7390-185">Belki de yalnızca kullandığınız bir API kabul <xref:System.Memory%601> bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="e7390-185">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="e7390-186">Bu bir sakınca yoktur ancak alışverişler kullanırken dikkat <xref:System.Memory%601> zaman uyumlu olarak.</span><span class="sxs-lookup"><span data-stu-id="e7390-186">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="e7390-187">**#2. kural: ReadOnlySpan kullanın\<T > ya da ReadOnlyMemory\<T > salt okunur arabellek olması gerekiyorsa.**</span><span class="sxs-lookup"><span data-stu-id="e7390-187">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="e7390-188">Önceki örneklerde, `DisplayBufferToConsole` yöntemi yalnızca arabellekteki okur; arabellek içeriğini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="e7390-188">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="e7390-189">Yöntem imzası, aşağıdaki değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e7390-189">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="e7390-190">Aslında, bu kural ve kural 1 birleştirdik, biz daha da iyi yapın ve yöntem imzası şu şekilde yeniden yazın:</span><span class="sxs-lookup"><span data-stu-id="e7390-190">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="e7390-191">`DisplayBufferToConsole` Yöntemi hemen her arabellek türü hayal nasıl çalıştığını: `T[]`, depolama ile ayrılmış [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md)ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="e7390-191">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), and so on.</span></span> <span data-ttu-id="e7390-192">Hatta geçirebilirsiniz bir <xref:System.String> doğrudan alın!</span><span class="sxs-lookup"><span data-stu-id="e7390-192">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="e7390-193">**#3. kural: Bellek yönteminizin kabul ediyorsa\<T > ve döndürür `void`, bellek kullanmamalıdır\<T >, yöntemin dönüşünün ardından örnek.**</span><span class="sxs-lookup"><span data-stu-id="e7390-193">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="e7390-194">Bu, daha önce bahsedilen "kira" kavramı ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="e7390-194">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="e7390-195">Void döndüren yöntemin kira <xref:System.Memory%601> örneği yöntemi girilir ve yöntemi çıktığında bunu bittiğinde başlar.</span><span class="sxs-lookup"><span data-stu-id="e7390-195">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="e7390-196">Çağıran aşağıdaki örneği inceleyin `Log` konsolundan giriş göre döngü içinde.</span><span class="sxs-lookup"><span data-stu-id="e7390-196">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="e7390-197">Varsa `Log` tamamen zaman uyumlu bir yöntem bu kodu herhangi bir zamanda yalnızca bir etkin tüketici bellek örneğinin olduğundan beklendiği gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="e7390-197">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="e7390-198">Ancak bunun yerine, Imagine `Log` bu uygulamaya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e7390-198">But imagine instead that `Log` has this implementation.</span></span>

```csharp
// !!! INCORRECT IMPLEMENTATION !!!
static void Log(ReadOnlyMemory<char> message)
{
    // Run in background so that we don't block the main thread while performing IO.
    Task.Run(() =>
    {
        StreamWriter sw = File.AppendText(@".\input-numbers.dat");
        sw.WriteLine(message);
    });
}
```

<span data-ttu-id="e7390-199">Bu uygulamada `Log` onu kullanmaya çalışır çünkü kirasını ihlal <xref:System.Memory%601> asıl yöntemi döndürdü sonra arka planda örneği.</span><span class="sxs-lookup"><span data-stu-id="e7390-199">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="e7390-200">`Main` Yöntemi sırasında arabellek bulunmamalıdır `Log` kendisinden okumak veri bozulmasına neden çalışır.</span><span class="sxs-lookup"><span data-stu-id="e7390-200">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="e7390-201">Bu sorunu çözmek için birçok yol vardır:</span><span class="sxs-lookup"><span data-stu-id="e7390-201">There are several ways to resolve this:</span></span>

- <span data-ttu-id="e7390-202">`Log` Yöntemi döndürebilir bir <xref:System.Threading.Tasks.Task> yerine `void`, aşağıdaki uygulaması olarak `Log` yöntemi yapar.</span><span class="sxs-lookup"><span data-stu-id="e7390-202">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="e7390-203">`Log` Bunun yerine şu şekilde uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="e7390-203">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="e7390-204">**Kural #4: Bir bellek yönteminizin kabul ediyorsa\<T > ve bir görev döndürür bellek kullanmamalıdır\<T > Görev geçişlerini terminal durumuna sonra örneği.**</span><span class="sxs-lookup"><span data-stu-id="e7390-204">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="e7390-205">Kural 3 yalnızca zaman uyumsuz çeşidini budur.</span><span class="sxs-lookup"><span data-stu-id="e7390-205">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="e7390-206">`Log` Yöntemi önceki örnekle yazılabilir gibi bu kurala uygun:</span><span class="sxs-lookup"><span data-stu-id="e7390-206">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="e7390-207">Burada, görev geçişleri tamamlandı, hatalı veya iptal edildi durumu "terminal durumuna" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e7390-207">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="e7390-208">Diğer bir deyişle, "terminal durumuna" anlamına gelir "neden olan herhangi bir şey await throw veya yürütmeye devam et."</span><span class="sxs-lookup"><span data-stu-id="e7390-208">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="e7390-209">Bu kılavuz döndüren yöntemler için geçerlidir <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, veya benzer bir tür.</span><span class="sxs-lookup"><span data-stu-id="e7390-209">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="e7390-210">**Kural #5: Güvenlik denetimini atladığından bellek kabul ediyorsa\<T > parametre olarak, oluşturulan nesne üzerinde örnek yöntemleri bellek tüketicilerinin olarak kabul edilir\<T > örneği.**</span><span class="sxs-lookup"><span data-stu-id="e7390-210">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="e7390-211">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e7390-211">Consider the following example:</span></span>

```csharp
class OddValueExtractor
{
    public OddValueExtractor(ReadOnlyMemory<int> input);
    public bool TryReadNextOddValue(out int value);
}

void PrintAllOddValues(ReadOnlyMemory<int> input)
{
    var extractor = new OddValueExtractor(input);
    while (extractor.TryReadNextOddValue(out int value))
    {
      Console.WriteLine(value);
    }
}
```

<span data-ttu-id="e7390-212">Burada, `OddValueExtractor` Oluşturucusu kabul eden bir `ReadOnlyMemory<int>` Oluşturucu parametresi olarak, bu nedenle Oluşturucusu olan bir tüketicisi `ReadOnlyMemory<int>` örneği ve döndürülen değer tüm örnek yöntemler olan ayrıca orijinal tüketicilerinin `ReadOnlyMemory<int>` örneği.</span><span class="sxs-lookup"><span data-stu-id="e7390-212">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="e7390-213">Diğer bir deyişle `TryReadNextOddValue` tüketir `ReadOnlyMemory<int>` örneği doğrudan geçirilen değil olsa da, örnek `TryReadNextOddValue` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e7390-213">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="e7390-214">**Kural #6: Ayarlanabilir bir bellek varsa\<T >-örnek yöntemler bu nesne, türü belirlenmiş bir özellik (veya eşdeğer bir örnek yöntemi) varsayılır bellek tüketicilerinin\<T > örneği.**</span><span class="sxs-lookup"><span data-stu-id="e7390-214">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="e7390-215">Bu aslında bir kural 5 çeşididir.</span><span class="sxs-lookup"><span data-stu-id="e7390-215">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="e7390-216">Özellik ayarlayıcılarına veya eşdeğer yöntemleri yakalamak ve yakalanan durum kullanabilen aynı nesne üzerinde örnek yöntemleri için kendi girişleri kalıcı hale getirmek için kabul edilir çünkü bu kuralı yok.</span><span class="sxs-lookup"><span data-stu-id="e7390-216">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="e7390-217">Aşağıdaki örnek, bu kural tetiklenir:</span><span class="sxs-lookup"><span data-stu-id="e7390-217">The following example triggers this rule:</span></span>

```csharp
class Person
{
    // Settable property.
    public Memory<char> FirstName { get; set; }

    // alternatively, equivalent "setter" method
    public SetFirstName(Memory<char> value);

    // alternatively, a public settable field
    public Memory<char> FirstName;
}
```

<span data-ttu-id="e7390-218">**#7. kural: Bir IMemoryOwner varsa\<T > başvuru, bir noktada bunu dispose noktası veya gerekir sahipliğini (ancak her ikisini birden değil) aktarım.**</span><span class="sxs-lookup"><span data-stu-id="e7390-218">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="e7390-219">Bu yana bir <xref:System.Memory%601> örneği tarafından yönetilen veya yönetilmeyen bellek yedeklenen, sahibi çağırmalıdır <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> iş zaman gerçekleştirilen <xref:System.Memory%601> örneği tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="e7390-219">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="e7390-220">Alternatif olarak, sahibi sahipliğini aktarabilir <xref:System.Buffers.IMemoryOwner%601> hangi noktada alınırken bir bileşen için arama sorumlu olur, farklı bir bileşen örneğine <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> (Bu, daha sonra daha fazla) uygun zamanda.</span><span class="sxs-lookup"><span data-stu-id="e7390-220">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="e7390-221">Aranacak hata <xref:System.Buffers.MemoryPool%601.Dispose%2A> yöntemi yönetilmeyen bellek sızıntısı veya diğer performans düşüşüne neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7390-221">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="e7390-222">Bu kural gibi Fabrika yöntemleri çağıran kod için de geçerlidir. <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e7390-222">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e7390-223">Arayan döndürülen sahibi olur <xref:System.Buffers.IMemoryOwner%601> ve bittiğinde örneğini disposing için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="e7390-223">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="e7390-224">**Kural #8: Bir IMemoryOwner varsa\<T > parametresi, API yüzeyi, bu örneğe sahipliğini kabul edersiniz.**</span><span class="sxs-lookup"><span data-stu-id="e7390-224">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="e7390-225">Bu türün örneğini kabul bileşenin bu örneği sahipliğini amaçlayan bildirir.</span><span class="sxs-lookup"><span data-stu-id="e7390-225">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="e7390-226">Bileşeniniz düzgün bir şekilde elden kural #7 göre sorumlu olur.</span><span class="sxs-lookup"><span data-stu-id="e7390-226">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="e7390-227">Sahipliğini aktaran herhangi bir bileşeni <xref:System.Buffers.IMemoryOwner%601> yöntem çağrısı tamamlandığında örneği farklı bir bileşen için bu örneği artık kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7390-227">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e7390-228">Güvenlik denetimini atladığından kabul ediyorsa <xref:System.Buffers.IMemoryOwner%601> türünü bir parametre olarak, uygulamalıdır <xref:System.IDisposable>ve <xref:System.IDisposable.Dispose%2A> yöntemini çağırma <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e7390-228">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e7390-229">**Kural #9: Bir zaman uyumlu p/Invoke yöntemi sarmalama, API'nizi yayılma kabul etmelidir\<T > parametre olarak.**</span><span class="sxs-lookup"><span data-stu-id="e7390-229">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="e7390-230">Kural 1 göre <xref:System.Span%601> genellikle zaman uyumlu API'leri için kullanılacak doğru türüdür.</span><span class="sxs-lookup"><span data-stu-id="e7390-230">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="e7390-231">Sabitleyebilmeniz için <xref:System.Span%601> aracılığıyla örnekler [ `fixed` ](~/docs/csharp/language-reference/keywords/fixed-statement.md) aşağıdaki örnekteki gibi anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="e7390-231">You can pin <xref:System.Span%601> instances via the [`fixed`](~/docs/csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

```csharp
using System.Runtime.InteropServices;

[DllImport(...)]
private static extern unsafe int ExportedMethod(byte* pbData, int cbData);

public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        int retVal = ExportedMethod(pbData, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

<span data-ttu-id="e7390-232">Önceki örnekte, `pbData` Örneğin, giriş aralık boş ise null olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7390-232">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="e7390-233">Dışarı aktarılan yöntemi kesinlikle gerektiriyorsa `pbData` null olmayan, olması bile `cbData` 0 ise, yöntem şu şekilde uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="e7390-233">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

```csharp
public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        byte dummy = 0;
        int retVal = ExportedMethod((pbData != null) ? pbData : &dummy, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

<span data-ttu-id="e7390-234">**#10 kuralı: Bir zaman uyumsuz p/Invoke yöntemi sarmalama, API'nizi bellek kabul etmelidir\<T > parametre olarak.**</span><span class="sxs-lookup"><span data-stu-id="e7390-234">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="e7390-235">Bu yana kullanamazsınız [ `fixed` ](~/docs/csharp/language-reference/keywords/fixed-statement.md) anahtar sözcüğü arasında zaman uyumsuz işlemler, kullandığınız <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> sabitlemek yöntemi <xref:System.Memory%601> örnekleri, örnekteki bitişik bellek türü ne olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="e7390-235">Since you cannot use the [`fixed`](~/docs/csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="e7390-236">Aşağıdaki örnek, bir zaman uyumsuz p/Invoke araması gerçekleştirmek için bu API kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7390-236">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

```csharp
using System.Runtime.InteropServices;

[UnmanagedFunctionPointer(...)]
private delegate void OnCompletedCallback(IntPtr state, int result);

[DllImport(...)]
private static extern unsafe int ExportedAsyncMethod(byte* pbData, int cbData, IntPtr pState, IntPtr lpfnOnCompletedCallback);

private static readonly IntPtr _callbackPtr = GetCompletionCallbackPointer();

public unsafe Task<int> ManagedWrapperAsync(Memory<byte> data)
{
    // setup
    var tcs = new TaskCompletionSource<int>();
    var state = new MyCompletedCallbackState
    {
        Tcs = tcs
    };
    var pState = (IntPtr)GCHandle.Alloc(state);

    var memoryHandle = data.Pin();
    state.MemoryHandle = memoryHandle;

    // make the call
    int result;
    try
    {
        result = ExportedAsyncMethod((byte*)memoryHandle.Pointer, data.Length, pState, _callbackPtr);
    }
    catch
    {
        ((GCHandle)pState).Free(); // cleanup since callback won't be invoked
        memoryHandle.Dispose();
        throw;
    }

    if (result != PENDING)
    {
        // Operation completed synchronously; invoke callback manually
        // for result processing and cleanup.
        MyCompletedCallbackImplementation(pState, result);
    }

    return tcs.Task;
}

private static void MyCompletedCallbackImplementation(IntPtr state, int result)
{
    GCHandle handle = (GCHandle)state;
    var actualState = (MyCompletedCallbackState)state;
    handle.Free();
    actualState.MemoryHandle.Dispose();

    /* error checking result goes here */

    if (error)
    {
        actualState.Tcs.SetException(...);
    }
    else
    {
        actualState.Tcs.SetResult(result);
    }
}

private static IntPtr GetCompletionCallbackPointer()
{
    OnCompletedCallback callback = MyCompletedCallbackImplementation;
    GCHandle.Alloc(callback); // keep alive for lifetime of application
    return Marshal.GetFunctionPointerForDelegate(callback);
}

private class MyCompletedCallbackState
{
    public TaskCompletionSource<int> Tcs;
    public MemoryHandle MemoryHandle;
}
```

## <a name="see-also"></a><span data-ttu-id="e7390-237">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7390-237">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
