---
title: Memory<T> ve Span<T> kullanım yönergeleri
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 0a614f628faa98be778c627573e4dddc462c9107
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121968"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="57c79-102">Memory\<T > ve Span\<T > kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="57c79-102">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="57c79-103">.NET Core, rasgele bitişik bellek bölgesini temsil eden bir dizi tür içerir.</span><span class="sxs-lookup"><span data-stu-id="57c79-103">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="57c79-104">.NET Core 2.0 <xref:System.Span%601> <xref:System.ReadOnlySpan%601>tanıtıldı ve yönetilen veya yönetilmeyen bellek tarafından desteklenen hafif bellek arabellekleri vardır.</span><span class="sxs-lookup"><span data-stu-id="57c79-104">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="57c79-105">Bu türler yalnızca yığında depolanabildiği için, eşzamanlı yöntem çağrıları da dahil olmak üzere bir dizi senaryo için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="57c79-105">Because these types can only be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="57c79-106">.NET Core 2.1 , <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601> <xref:System.Buffers.IMemoryOwner%601>, ve <xref:System.Buffers.MemoryPool%601>.</span><span class="sxs-lookup"><span data-stu-id="57c79-106">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="57c79-107">Gibi <xref:System.Span%601> <xref:System.Memory%601> , ve ilgili türleri hem yönetilen ve yönetilmeyen bellek tarafından desteklenebilir.</span><span class="sxs-lookup"><span data-stu-id="57c79-107">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="57c79-108"><xref:System.Span%601>Aksine, <xref:System.Memory%601> yönetilen yığın üzerinde saklanabilir.</span><span class="sxs-lookup"><span data-stu-id="57c79-108">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can be stored on the managed heap.</span></span>

<span data-ttu-id="57c79-109">Her <xref:System.Span%601> <xref:System.Memory%601> ikisi de ve ardışık hatlar kullanılabilir yapılandırılmış veri arabellekleri vardır.</span><span class="sxs-lookup"><span data-stu-id="57c79-109">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="57c79-110">Diğer bir deyişle, verilerin bir kısmının veya tamamının ardışık olarak aktarılabilen, bunları işleyen ve isteğe bağlı olarak arabelleği değiştirebilen parçalara aktarılabilen şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="57c79-110">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="57c79-111"><xref:System.Memory%601> Ve ilgili türleri birden çok bileşen veya birden çok iş parçacığı tarafından erişilebildiği için, geliştiricilerin sağlam kod lar üretmek için bazı standart kullanım yönergelerini izlemesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="57c79-111">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="57c79-112">Sahipleri, tüketiciler ve ömür boyu yönetim</span><span class="sxs-lookup"><span data-stu-id="57c79-112">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="57c79-113">Arabellekler API'ler arasında geçirilebildiği ve arabelleklere bazen birden çok iş parçacığından erişilebildiği için, yaşam boyu yönetimi göz önünde bulundurmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="57c79-113">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="57c79-114">Üç temel kavram vardır:</span><span class="sxs-lookup"><span data-stu-id="57c79-114">There are three core concepts:</span></span>

- <span data-ttu-id="57c79-115">**Sahiplik**.</span><span class="sxs-lookup"><span data-stu-id="57c79-115">**Ownership**.</span></span> <span data-ttu-id="57c79-116">Arabellek örneğinin sahibi, artık kullanılmadığında arabelleği yok etmek de dahil olmak üzere yaşam boyu yönetimden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="57c79-116">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="57c79-117">Tüm arabelleklerin tek bir sahibi var.</span><span class="sxs-lookup"><span data-stu-id="57c79-117">All buffers have a single owner.</span></span> <span data-ttu-id="57c79-118">Genellikle sahibi arabellek oluşturulan veya bir fabrikadan arabellek aldı bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="57c79-118">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="57c79-119">Mülkiyet de devredilebilir; **Bileşen-A** arabellek denetimini **Bileşen-B'ye**verebilir, bu noktada **Bileşen-A** arabelleği artık kullanamayabilir ve **Bileşen-B** artık kullanılmadığında arabelleği yok etmekten sorumlu olur.</span><span class="sxs-lookup"><span data-stu-id="57c79-119">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="57c79-120">**Tüketim**.</span><span class="sxs-lookup"><span data-stu-id="57c79-120">**Consumption**.</span></span> <span data-ttu-id="57c79-121">Arabellek örneğinin tüketicisi, arabellek örneğini ondan okuyarak ve muhtemelen ona yazarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="57c79-121">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="57c79-122">Bazı dış eşitleme mekanizması sağlanmadıkça arabellekler aynı anda bir tüketiciye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="57c79-122">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="57c79-123">Arabellek etkin tüketici mutlaka arabellek sahibi olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="57c79-123">Note that the active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="57c79-124">**Kira .**</span><span class="sxs-lookup"><span data-stu-id="57c79-124">**Lease**.</span></span> <span data-ttu-id="57c79-125">Kiralama, belirli bir bileşenin arabelleğe tüketici sayılsa izin verdiği süredir.</span><span class="sxs-lookup"><span data-stu-id="57c79-125">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="57c79-126">Aşağıdaki sözde kod örneği bu üç kavramı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="57c79-126">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="57c79-127">Bu tür `Main` <xref:System.Memory%601> <xref:System.Char>bir arabellek instantiates bir yöntem `WriteInt32ToBuffer` içerir, arabellek için bir tamsa dize gösterimi `DisplayBufferToConsole` yazmak için yöntemi çağırır ve sonra arabellek değerini görüntülemek için yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="57c79-127">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

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

<span data-ttu-id="57c79-128">Yöntem `Main` arabellek oluşturur (bu durumda <xref:System.Span%601> bir örnek) ve böylece sahibi.</span><span class="sxs-lookup"><span data-stu-id="57c79-128">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="57c79-129">Bu `Main` nedenle, artık kullanılmadığında arabelleği yok etmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="57c79-129">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="57c79-130">Bunu arabellek <xref:System.Span%601.Clear?displayProperty=nameWithType> yöntemini arayarak yapar.</span><span class="sxs-lookup"><span data-stu-id="57c79-130">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="57c79-131">(Buradaki <xref:System.Span%601.Clear> yöntem aslında arabelleğin belleği <xref:System.Span%601> temizler; yapıaslında arabelleği yok eden bir yöntem yok.)</span><span class="sxs-lookup"><span data-stu-id="57c79-131">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="57c79-132">Arabellekte iki tüketici `WriteInt32ToBuffer` `DisplayBufferToConsole`vardır ve.</span><span class="sxs-lookup"><span data-stu-id="57c79-132">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="57c79-133">Aynı anda yalnızca bir tüketici `WriteInt32ToBuffer`vardır `DisplayBufferToConsole`(önce, sonra), ve tüketicilerin hiçbiri tampona sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="57c79-133">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="57c79-134">Bu bağlamda "tüketici"nin arabelleğe salt okunur görünümü anlamına olmadığını da unutmayın; tüketiciler, arabelleğe bir okuma/yazma görünümü verilirse, `WriteInt32ToBuffer` bu arabellek içeriğini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57c79-134">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="57c79-135">Yöntem, `WriteInt32ToBuffer` yöntem çağrısının başlangıcı ile yöntemin döndüğü zaman arasında arabellek üzerinde bir kiraya sahiptir (tüketebilir).</span><span class="sxs-lookup"><span data-stu-id="57c79-135">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="57c79-136">Benzer şekilde, `DisplayBufferToConsole` yürütülürken arabellekte bir kira vardır ve yöntem gerdiğinde kira serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="57c79-136">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="57c79-137">(Kira yönetimi için API yoktur; "kira" kavramsal bir konudur.)</span><span class="sxs-lookup"><span data-stu-id="57c79-137">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="57c79-138">Bellek\<T> ve sahibi/ tüketici modeli</span><span class="sxs-lookup"><span data-stu-id="57c79-138">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="57c79-139">[Sahipleri, tüketiciler ve ömür boyu yönetim](#owners-consumers-and-lifetime-management) bölümü notları gibi, bir arabellek her zaman bir sahibi vardır.</span><span class="sxs-lookup"><span data-stu-id="57c79-139">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="57c79-140">.NET Core iki sahiplik modelini destekler:</span><span class="sxs-lookup"><span data-stu-id="57c79-140">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="57c79-141">Tek sahipliği destekleyen bir model.</span><span class="sxs-lookup"><span data-stu-id="57c79-141">A model that supports single ownership.</span></span> <span data-ttu-id="57c79-142">Bir arabellek tüm ömrü boyunca tek bir sahibi vardır.</span><span class="sxs-lookup"><span data-stu-id="57c79-142">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="57c79-143">Sahiplik aktarımına destek veren bir model.</span><span class="sxs-lookup"><span data-stu-id="57c79-143">A model that supports ownership transfer.</span></span> <span data-ttu-id="57c79-144">Arabelleğe sahipolmak, asıl sahibinden (yaratıcısı) başka bir bileşene aktarılabilir ve bu da arabellbellin yaşam boyu yönetiminden sorumlu hale gelir.</span><span class="sxs-lookup"><span data-stu-id="57c79-144">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="57c79-145">Bu sahip, sahipliği başka bir bileşene aktarabilir ve böyle devam eder.</span><span class="sxs-lookup"><span data-stu-id="57c79-145">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="57c79-146">Arabelleği <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> açıkça yönetmek için arabirimi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="57c79-146">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="57c79-147"><xref:System.Buffers.IMemoryOwner%601>her iki sahiplik modelini de destekler.</span><span class="sxs-lookup"><span data-stu-id="57c79-147"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="57c79-148"><xref:System.Buffers.IMemoryOwner%601> Başvuru sahibi bileşen arabelleğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="57c79-148">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="57c79-149">Aşağıdaki örnek, <xref:System.Buffers.IMemoryOwner%601?> arabelleğin sahipliğini <xref:System.Memory%601> yansıtmak için bir örnek kullanır.</span><span class="sxs-lookup"><span data-stu-id="57c79-149">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of an <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="57c79-150">Biz de bu örneği [`using`](../../csharp/language-reference/keywords/using-statement.md)yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="57c79-150">We can also write this example with the [`using`](../../csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="57c79-151">Bu kodda:</span><span class="sxs-lookup"><span data-stu-id="57c79-151">In this code:</span></span>

- <span data-ttu-id="57c79-152">Yöntem `Main` <xref:System.Buffers.IMemoryOwner%601> örneğine başvuru tutar, bu `Main` nedenle yöntem arabellek sahibidir.</span><span class="sxs-lookup"><span data-stu-id="57c79-152">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="57c79-153">Ve `WriteInt32ToBuffer` `DisplayBufferToConsole` yöntemler <xref:System.Memory%601> genel API olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="57c79-153">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="57c79-154">Bu nedenle, arabellek tüketicilerdir.</span><span class="sxs-lookup"><span data-stu-id="57c79-154">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="57c79-155">Ve her seferinde sadece birer tüketirler.</span><span class="sxs-lookup"><span data-stu-id="57c79-155">And they only consume it one at a time.</span></span>

<span data-ttu-id="57c79-156">Yöntem `WriteInt32ToBuffer` arabellek için bir değer yazmak için `DisplayBufferToConsole` tasarlanmış olsa da, yöntem değildir.</span><span class="sxs-lookup"><span data-stu-id="57c79-156">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="57c79-157">Bunu yansıtmak için, tür <xref:System.ReadOnlyMemory%601>bir argüman kabul olabilir.</span><span class="sxs-lookup"><span data-stu-id="57c79-157">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="57c79-158">Daha fazla <xref:System.ReadOnlyMemory%601>bilgi için , [Bkz.\<Kural #2: Arabellek salt okunacaksa ReadOnlySpan T> veya ReadOnlyMemory\<T>'ı kullanın.](#rule-2)</span><span class="sxs-lookup"><span data-stu-id="57c79-158">For additional information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="57c79-159">"Sahipsiz"\<Bellek T örnekleri></span><span class="sxs-lookup"><span data-stu-id="57c79-159">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="57c79-160">Bir <xref:System.Memory%601> örneği kullanmadan <xref:System.Buffers.IMemoryOwner%601>oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57c79-160">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="57c79-161">Bu durumda, arabellek sahipliği açık yerine örtülü ve yalnızca tek sahibi modeli desteklenir.</span><span class="sxs-lookup"><span data-stu-id="57c79-161">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="57c79-162">Bunu şu şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="57c79-162">You can do this by:</span></span>

- <span data-ttu-id="57c79-163"><xref:System.Memory%601> Aşağıdaki örnekte olduğu `T[]`gibi, doğrudan yapıcılardan birini çağırmak.</span><span class="sxs-lookup"><span data-stu-id="57c79-163">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="57c79-164">Bir `ReadOnlyMemory<char>` örnek oluşturmak için [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) uzantı yöntemini çağırma.</span><span class="sxs-lookup"><span data-stu-id="57c79-164">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="57c79-165">Başlangıçta <xref:System.Memory%601> örneği oluşturan yöntem arabellek örtülü sahibidir.</span><span class="sxs-lookup"><span data-stu-id="57c79-165">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="57c79-166">Devriyi kolaylaştıracak bir örnek olmadığından, <xref:System.Buffers.IMemoryOwner%601> sahiplik başka bir bileşene aktarılamaz.</span><span class="sxs-lookup"><span data-stu-id="57c79-166">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="57c79-167">(Alternatif olarak, çalışma zamanının çöp toplayıcısının arabelleğe sahip olduğunu ve tüm yöntemlerin arabelleği tükettiğini de tahmin edebilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="57c79-167">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="57c79-168">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="57c79-168">Usage guidelines</span></span>

<span data-ttu-id="57c79-169">Bir bellek bloğu sahibi olduğundan ancak bazıları belirli bir bellek bloğu üzerinde aynı anda çalışabilir birden çok bileşene <xref:System.Memory%601> geçirilmesi <xref:System.Span%601>amaçlanmıştır, hem ve .</span><span class="sxs-lookup"><span data-stu-id="57c79-169">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="57c79-170">Yönergeler gereklidir, çünkü:</span><span class="sxs-lookup"><span data-stu-id="57c79-170">Guidelines are necessary because:</span></span>

- <span data-ttu-id="57c79-171">Bir bileşenin, sahibi yayımladıktan sonra bellek bloğuna başvuruda bulunmasını sağlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="57c79-171">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="57c79-172">Bir bileşenin, arabellekteki verileri bozma işleminde, başka bir bileşenin üzerinde çalıştığı anda bir arabellek üzerinde çalışması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="57c79-172">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="57c79-173">Yığına ayrılan yapı performansı <xref:System.Span%601> en iyi <xref:System.Span%601> duruma getirir ve bellek bloğunda çalışmak için <xref:System.Span%601> tercih edilen türü yapar, ancak bazı önemli kısıtlamalara da tabi dir.</span><span class="sxs-lookup"><span data-stu-id="57c79-173">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="57c79-174">Ne zaman <xref:System.Span%601> ve ne zaman kullanılacağını <xref:System.Memory%601>bilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="57c79-174">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="57c79-175">Aşağıda başarıyla kullanmak <xref:System.Memory%601> ve ilgili türleri için önerilerimiz verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="57c79-175">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="57c79-176">Aksini <xref:System.Memory%601> açıkça belirtmediğimiz <xref:System.Span%601> sürece, <xref:System.ReadOnlyMemory%601> bu <xref:System.ReadOnlySpan%601> kılavuz için de geçerli olduğunu ve bu kılavuz için de geçerli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="57c79-176">Note that guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="57c79-177">**Kural #1: Senkron API için,\<bellek\<T> yerine Span T>'ı mümkünse parametre olarak kullanın.**</span><span class="sxs-lookup"><span data-stu-id="57c79-177">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="57c79-178"><xref:System.Span%601>daha çok <xref:System.Memory%601> yönlüdür ve bitişik bellek arabelleklerinin daha geniş bir yelpazesini temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="57c79-178"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="57c79-179"><xref:System.Span%601>ayrıca <xref:System.Memory%601>daha iyi performans sunar.</span><span class="sxs-lookup"><span data-stu-id="57c79-179"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="57c79-180">Son olarak, Span <xref:System.Memory%601.Span?displayProperty=nameWithType> <xref:System.Memory%601> \<T>-to-Memory\<T> dönüştürme mümkün olmasa da, bir örneği bir <xref:System.Span%601>, bir ,> dönüştürmek dönüştürmek için özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57c79-180">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="57c79-181">Bu nedenle, arayanların bir <xref:System.Memory%601> örneği varsa, yine de parametrelerle <xref:System.Span%601> yöntemlerinizi arayabilirler.</span><span class="sxs-lookup"><span data-stu-id="57c79-181">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="57c79-182">Tür <xref:System.Span%601> <xref:System.Memory%601> yerine bir tür parametresi kullanmak da doğru bir tüketme yöntemi uygulaması yazmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="57c79-182">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="57c79-183">Yönteminizin kiralanmasının ötesinde arabelleğe erişmeye çalışmadığınızdan emin olmak için otomatik olarak derleme zamanı denetimleri alırsınız (daha sonra bu konuda daha fazla bilgi).</span><span class="sxs-lookup"><span data-stu-id="57c79-183">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="57c79-184">Bazen, tam eşzamanlı olsanız <xref:System.Memory%601> bile <xref:System.Span%601> parametre yerine parametre kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="57c79-184">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="57c79-185">Belki de bağlı olduğunuz bir <xref:System.Memory%601> API yalnızca bağımsız değişkenleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="57c79-185">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="57c79-186">Bu iyi, ancak eşzamanlı kullanırken <xref:System.Memory%601> ilgili tradeoffs farkında olun.</span><span class="sxs-lookup"><span data-stu-id="57c79-186">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="57c79-187">**Kural #2: Arabellek\<salt okunacaksa ReadOnlySpan T> veya ReadOnlyMemory\<T> kullanın.**</span><span class="sxs-lookup"><span data-stu-id="57c79-187">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="57c79-188">Önceki örneklerde, `DisplayBufferToConsole` yöntem yalnızca arabellekten okur; arabelleğe ilişkin içeriğini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="57c79-188">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="57c79-189">Yöntem imzası aşağıdaki şekilde değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="57c79-189">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="57c79-190">Aslında, bu kural ve kural #1 birleştirirseniz, daha da iyisini yapabilir ve yöntem imzasını aşağıdaki gibi yeniden yazabiliriz:</span><span class="sxs-lookup"><span data-stu-id="57c79-190">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="57c79-191">Yöntem `DisplayBufferToConsole` şimdi akla gelebilecek hemen hemen her `T[]`tampon türü ile çalışır: , [depolama stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile tahsis , ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="57c79-191">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), and so on.</span></span> <span data-ttu-id="57c79-192">Hatta doğrudan içine <xref:System.String> bir geçebilir!</span><span class="sxs-lookup"><span data-stu-id="57c79-192">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="57c79-193">**Kural #3: Yönteminiz\<Bellek T `void`>'u kabul edip\<döndürürse, yönteminiz döndükten sonra Bellek T> örneğini kullanmamalısınız.**</span><span class="sxs-lookup"><span data-stu-id="57c79-193">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="57c79-194">Bu daha önce bahsedilen "kira" kavramı ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="57c79-194">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="57c79-195">Bir void-returning yöntemin <xref:System.Memory%601> örnek üzerinde kira yöntemi girildiğinde başlar ve yöntem çıktığında sona erer.</span><span class="sxs-lookup"><span data-stu-id="57c79-195">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="57c79-196">Konsoldan gelen girişe `Log` göre bir döngü içinde çağıran aşağıdaki örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="57c79-196">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="57c79-197">Tam `Log` eşzamanlı bir yöntemse, bu kod beklendiği gibi çalışır, çünkü herhangi bir zamanda bellek örneğinin yalnızca bir etkin tüketicisi vardır.</span><span class="sxs-lookup"><span data-stu-id="57c79-197">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="57c79-198">Ama bunun `Log` yerine bu uygulama olduğunu düşünün.</span><span class="sxs-lookup"><span data-stu-id="57c79-198">But imagine instead that `Log` has this implementation.</span></span>

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

<span data-ttu-id="57c79-199">Bu uygulamada, `Log` özgün yöntem döndükten sonra <xref:System.Memory%601> arka planda örneği kullanmaya çalıştığı için kira sözleşmesini ihlal eder.</span><span class="sxs-lookup"><span data-stu-id="57c79-199">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="57c79-200">Yöntem, `Main` arabelleği okuma `Log` girişimleri sırasında mutasyona uğrayabilir ve bu da veri bozulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="57c79-200">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="57c79-201">Bunu çözmenin birkaç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="57c79-201">There are several ways to resolve this:</span></span>

- <span data-ttu-id="57c79-202">Yöntem, `Log` <xref:System.Threading.Tasks.Task> `Log` yöntemin aşağıdaki `void`uygulama yaptığı gibi yerine bir döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="57c79-202">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="57c79-203">`Log`bunun yerine aşağıdaki gibi uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="57c79-203">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="57c79-204">**Kural #4: Yönteminiz bellek\<T> kabul ediyor ve bir\<Görevi döndürüyorsa, Görev terminal durumuna geçtikten sonra Bellek T> örneğini kullanmamalısınız.**</span><span class="sxs-lookup"><span data-stu-id="57c79-204">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="57c79-205">Bu, Kural #3'nin yalnızca async varyantıdır.</span><span class="sxs-lookup"><span data-stu-id="57c79-205">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="57c79-206">Önceki `Log` örnekteki yöntem, bu kurala uymak için aşağıdaki gibi yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="57c79-206">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="57c79-207">Burada, "terminal durumu" görevin tamamlanmış, hatalı veya iptal edilmiş bir duruma geçiş yaptığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="57c79-207">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="57c79-208">Başka bir deyişle, "terminal durumu" "atmayı veya yürütmeye devam etmeyi bekleyen her şey" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="57c79-208">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="57c79-209">Bu kılavuz, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.ValueTask%601>döndüren yöntemler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="57c79-209">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="57c79-210">**Kural #5: Oluşturucunuz Bellek\<T>'ı bir parametre olarak kabul ederse, yapılandırılan\<nesnedeki örnek yöntemlerin Bellek T> örneğinin tüketicileri olduğu varsayılır.**</span><span class="sxs-lookup"><span data-stu-id="57c79-210">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="57c79-211">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="57c79-211">Consider the following example:</span></span>

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

<span data-ttu-id="57c79-212">Burada, `OddValueExtractor` oluşturucu bir `ReadOnlyMemory<int>` oluşturucu parametre olarak kabul eder, bu nedenle `ReadOnlyMemory<int>` yapıcının kendisi örneğin tüketicisi dir ve döndürülen değerdeki tüm örnek yöntemleri de özgün `ReadOnlyMemory<int>` örneğin tüketicileridir.</span><span class="sxs-lookup"><span data-stu-id="57c79-212">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="57c79-213">Bu, `TryReadNextOddValue` örnek doğrudan `ReadOnlyMemory<int>` `TryReadNextOddValue` yönteme geçirilemese bile örneği tükettiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="57c79-213">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="57c79-214">**Kural #6: Türünüzde>\<türünde ayarlanabilir bir Bellek T özelliği (veya eşdeğer bir örnek yöntemi) varsa, bu\<nesnedeki örnek yöntemleri bellek T> örneğinin tüketicisi olarak kabul edilir.**</span><span class="sxs-lookup"><span data-stu-id="57c79-214">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="57c79-215">Bu gerçekten kural #5 sadece bir çeşididir.</span><span class="sxs-lookup"><span data-stu-id="57c79-215">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="57c79-216">Özellik ayarlayıcıları veya eşdeğer yöntemlerin girişlerini yakalayıp devam ettirmeleri varsayıldığından, aynı nesnedeki örnek yöntemleri yakalanan durumu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="57c79-216">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="57c79-217">Aşağıdaki örnek bu kuralı tetikler:</span><span class="sxs-lookup"><span data-stu-id="57c79-217">The following example triggers this rule:</span></span>

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

<span data-ttu-id="57c79-218">**Kural #7: Bir IMemoryOwner\<T> referans varsa, bir noktada onu elden veya sahipliğini aktarmak gerekir (ama her ikisi de değil).**</span><span class="sxs-lookup"><span data-stu-id="57c79-218">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="57c79-219">Bir <xref:System.Memory%601> örnek yönetilen veya yönetilmeyen bellek tarafından desteklenen olabilir, <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> <xref:System.Memory%601> örnek üzerinde gerçekleştirilen çalışma tamamlandığında sahibi aramak gerekir.</span><span class="sxs-lookup"><span data-stu-id="57c79-219">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="57c79-220">Alternatif olarak, sahibi örneğin sahipliğini <xref:System.Buffers.IMemoryOwner%601> farklı bir bileşene aktarabilir ve bu noktada <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> satın alma bileşeni uygun zamanda çağrıda bulunan (daha sonra bu konuda daha fazla bilgi) sorumlu olur.</span><span class="sxs-lookup"><span data-stu-id="57c79-220">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="57c79-221">Yöntemin <xref:System.Buffers.MemoryPool%601.Dispose%2A> çağrılmaması, yönetilmeyen bellek sızıntılarına veya diğer performans bozulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="57c79-221">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="57c79-222">Bu kural, fabrika yöntemlerini çağıran <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>kod için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="57c79-222">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="57c79-223">Arayan döndürülenin <xref:System.Buffers.IMemoryOwner%601> sahibi olur ve tamamlandığında örneğin atılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="57c79-223">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="57c79-224">**Kural #8: API>\<yüzeyinde bir IMemoryOwner T parametresi varsa, bu örneğin sahipliğini kabul etmiş siniz.**</span><span class="sxs-lookup"><span data-stu-id="57c79-224">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="57c79-225">Bu tür bir örneği kabul etmek, bileşeninizin bu örneğin sahipliğini almayı planladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="57c79-225">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="57c79-226">Bileşeniniz Kural #7'na göre uygun şekilde imha edilmesiiçin sorumlu olur.</span><span class="sxs-lookup"><span data-stu-id="57c79-226">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="57c79-227">Örneğin sahipliğini <xref:System.Buffers.IMemoryOwner%601> farklı bir bileşene aktaran herhangi bir bileşen, yöntem çağrısı tamamlandıktan sonra bu örneği artık kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="57c79-227">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57c79-228">Oluşturucunuz bir <xref:System.Buffers.IMemoryOwner%601> parametre olarak kabul ederse, <xref:System.IDisposable>türü <xref:System.IDisposable.Dispose%2A> uygulanmalıdır <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>ve yönteminiz .</span><span class="sxs-lookup"><span data-stu-id="57c79-228">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="57c79-229">**Kural #9: Eşzamanlı bir p/invoke yöntemini sarıyorsanız, API'niz Span\<T>'yi parametre olarak kabul etmelidir.**</span><span class="sxs-lookup"><span data-stu-id="57c79-229">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="57c79-230">Kural #1 göre, <xref:System.Span%601> genellikle senkron API'ler için kullanılacak doğru türüdür.</span><span class="sxs-lookup"><span data-stu-id="57c79-230">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="57c79-231">Aşağıdaki örnekte olduğu [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) gibi, örnekleri anahtar kelime aracılığıyla sabitleyebilirsiniz. <xref:System.Span%601></span><span class="sxs-lookup"><span data-stu-id="57c79-231">You can pin <xref:System.Span%601> instances via the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

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

<span data-ttu-id="57c79-232">Önceki örnekte, `pbData` örneğin giriş açıklığı boşsa null olabilir.</span><span class="sxs-lookup"><span data-stu-id="57c79-232">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="57c79-233">Dışa aktarılan yöntem `pbData` innull olmayan olmasını `cbData` gerektiriyorsa, 0 olsa bile, yöntem aşağıdaki gibi uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="57c79-233">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

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

<span data-ttu-id="57c79-234">**Kural #10: Bir eşzamanlı p/invoke yöntemini sarıyorsanız, API'niz Bellek\<T>'yi parametre olarak kabul etmelidir.**</span><span class="sxs-lookup"><span data-stu-id="57c79-234">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="57c79-235">Anahtar kelimeyi [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) eşzamanlı işlemlerde kullanamayacağınız için, <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> örneğin temsil <xref:System.Memory%601> ettiği bitişik bellek türünden bağımsız olarak örnekleri sabitleme yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="57c79-235">Since you cannot use the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="57c79-236">Aşağıdaki örnek, eşzamanlı bir p/invoke çağrısı gerçekleştirmek için bu API'nin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="57c79-236">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="57c79-237">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57c79-237">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
