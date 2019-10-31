---
title: Memory<T> ve Span<T> kullanım yönergeleri
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 0a614f628faa98be778c627573e4dddc462c9107
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121968"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="d8371-102">Bellek\<T > ve yayma\<T > Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d8371-102">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="d8371-103">.NET Core, belleğin rastgele bir bitişik bölgesini temsil eden bir dizi tür içerir.</span><span class="sxs-lookup"><span data-stu-id="d8371-103">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="d8371-104">.NET Core 2,0, yönetilen veya yönetilmeyen bellekle desteklenen basit bellek arabellekleri olan <xref:System.Span%601> ve <xref:System.ReadOnlySpan%601>sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="d8371-104">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="d8371-105">Bu türler yalnızca yığında depolanabileceğinden, zaman uyumsuz yöntem çağrıları dahil olmak üzere çok sayıda senaryo için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="d8371-105">Because these types can only be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="d8371-106">.NET Core 2,1 <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>ve <xref:System.Buffers.MemoryPool%601>dahil olmak üzere çeşitli ek türler ekler.</span><span class="sxs-lookup"><span data-stu-id="d8371-106">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="d8371-107"><xref:System.Span%601>gibi <xref:System.Memory%601> ve ilgili türleri hem yönetilen hem de yönetilmeyen bellekle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d8371-107">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="d8371-108"><xref:System.Span%601>farklı olarak, <xref:System.Memory%601> yönetilen yığında depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="d8371-108">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can be stored on the managed heap.</span></span>

<span data-ttu-id="d8371-109">Hem <xref:System.Span%601> hem de <xref:System.Memory%601>, işlem hatlarında kullanılabilecek yapılandırılmış verilerin arabelleklerdir.</span><span class="sxs-lookup"><span data-stu-id="d8371-109">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="d8371-110">Diğer bir deyişle, verilerin bazılarının veya tümünün işlem hattındaki bileşenlere etkin bir şekilde geçirilmesi için tasarlanmaları ve isteğe bağlı olarak arabelleği değiştirebilmeleri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d8371-110">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="d8371-111"><xref:System.Memory%601> ve ilgili türlerine birden çok bileşen veya birden çok iş parçacığı tarafından erişilebildiğinden, geliştiricilerin sağlam kod üretmek için bazı standart kullanım yönergelerini izlemesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d8371-111">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="d8371-112">Sahipler, tüketiciler ve ömür yönetimi</span><span class="sxs-lookup"><span data-stu-id="d8371-112">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="d8371-113">Arabellekler API 'Ler arasında geçirilebileceği ve arabelleklerin bazen birden fazla iş parçacığından erişilebilir olduğundan, ömür yönetimini göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d8371-113">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="d8371-114">Üç temel kavram vardır:</span><span class="sxs-lookup"><span data-stu-id="d8371-114">There are three core concepts:</span></span>

- <span data-ttu-id="d8371-115">**Sahiplik**.</span><span class="sxs-lookup"><span data-stu-id="d8371-115">**Ownership**.</span></span> <span data-ttu-id="d8371-116">Arabellek örneğinin sahibi, artık kullanımda olmadığında arabelleği yok etme da dahil olmak üzere ömür yönetiminden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="d8371-116">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="d8371-117">Tüm arabelleklerin tek bir sahibi vardır.</span><span class="sxs-lookup"><span data-stu-id="d8371-117">All buffers have a single owner.</span></span> <span data-ttu-id="d8371-118">Genellikle sahip, arabelleği oluşturan veya bir fabrikadan arabelleği alan bileşendir.</span><span class="sxs-lookup"><span data-stu-id="d8371-118">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="d8371-119">Sahiplik da aktarılabilir; **Bileşen-a** arabellek denetimini **bileşen-b**' y e yeniden denetleyebilir ve bu noktada, o nokta **bileşeni-A** artık arabellek kullanamaz ve **bileşen-b** artık kullanımda olmadığında arabelleği yok etmeden sorumlu olur.</span><span class="sxs-lookup"><span data-stu-id="d8371-119">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="d8371-120">**Tüketim**.</span><span class="sxs-lookup"><span data-stu-id="d8371-120">**Consumption**.</span></span> <span data-ttu-id="d8371-121">Bir arabellek örneğinin tüketicisi, onu okuyarak ve muhtemelen ona yazarak arabellek örneğini kullanmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="d8371-121">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="d8371-122">Bazı dış eşitleme mekanizması sağlanmadığı takdirde arabellekler tek seferde bir tüketiciye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8371-122">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="d8371-123">Bir arabelleğin etkin tüketicisinin, arabelleğin sahibi olması gerekmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d8371-123">Note that the active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="d8371-124">**Kira**.</span><span class="sxs-lookup"><span data-stu-id="d8371-124">**Lease**.</span></span> <span data-ttu-id="d8371-125">Kira, belirli bir bileşenin arabelleğin tüketicisi olmasına izin verilen süredir.</span><span class="sxs-lookup"><span data-stu-id="d8371-125">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="d8371-126">Aşağıdaki sözde kod örneğinde bu üç kavram gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d8371-126">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="d8371-127">Bu, <xref:System.Char>türünde bir <xref:System.Memory%601> arabelleğini örnekleyen `Main` yöntemi içerir, arabelleğe bir tamsayının dize gösterimini yazmak için `WriteInt32ToBuffer` yöntemini çağırır ve ardından arabelleğin değerini göstermek için `DisplayBufferToConsole` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="d8371-127">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

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

<span data-ttu-id="d8371-128">`Main` yöntemi, arabelleği oluşturur (Bu durumda bir <xref:System.Span%601> örneği) ve bu nedenle sahibidir.</span><span class="sxs-lookup"><span data-stu-id="d8371-128">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="d8371-129">Bu nedenle, `Main` artık kullanımda olmadığında arabelleği yok etmek sorumludur.</span><span class="sxs-lookup"><span data-stu-id="d8371-129">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="d8371-130">Bu, arabelleğin <xref:System.Span%601.Clear?displayProperty=nameWithType> yöntemini çağırarak yapar.</span><span class="sxs-lookup"><span data-stu-id="d8371-130">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d8371-131">(<xref:System.Span%601.Clear> yöntemi aslında arabelleğin belleğini temizler; <xref:System.Span%601> yapısı aslında arabelleği yok eden bir yönteme sahip değildir.)</span><span class="sxs-lookup"><span data-stu-id="d8371-131">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="d8371-132">Arabellekte iki tüketici vardır, `WriteInt32ToBuffer` ve `DisplayBufferToConsole`.</span><span class="sxs-lookup"><span data-stu-id="d8371-132">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="d8371-133">Tek seferde yalnızca bir tüketici vardır (ilk `WriteInt32ToBuffer`, sonra `DisplayBufferToConsole`) ve hiçbir tüketicisinin arabelleğin sahibi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d8371-133">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="d8371-134">Ayrıca, bu bağlamda "Consumer" öğesinin, arabelleğin salt okunurdur görünümünü göstermez; müşteriler, arabelleğin okuma/yazma görünümü verildiyse `WriteInt32ToBuffer` olduğu gibi arabelleğin içeriğini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="d8371-134">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="d8371-135">`WriteInt32ToBuffer` yöntemi, yöntem çağrısının başlangıcı ile yöntemin döndürdüğü süre arasındaki arabelleği (tüketebileceği) kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8371-135">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="d8371-136">Benzer şekilde, `DisplayBufferToConsole` yürütülürken arabellekte bir kiralama vardır ve kira yöntemi zaman içinde serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="d8371-136">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="d8371-137">(Kiralama Yönetimi için bir API yoktur; "Kira" kavramsal bir kavramdır.)</span><span class="sxs-lookup"><span data-stu-id="d8371-137">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="d8371-138">Bellek\<T > ve sahip/tüketici modeli</span><span class="sxs-lookup"><span data-stu-id="d8371-138">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="d8371-139">[Sahipler, tüketiciler ve ömür yönetimi](#owners-consumers-and-lifetime-management) bölümünde, bir arabelleğin her zaman bir sahibi vardır.</span><span class="sxs-lookup"><span data-stu-id="d8371-139">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="d8371-140">.NET Core iki sahiplik modelini destekler:</span><span class="sxs-lookup"><span data-stu-id="d8371-140">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="d8371-141">Tek sahipliği destekleyen bir model.</span><span class="sxs-lookup"><span data-stu-id="d8371-141">A model that supports single ownership.</span></span> <span data-ttu-id="d8371-142">Bir arabelleğin tüm ömrü için tek bir sahibi vardır.</span><span class="sxs-lookup"><span data-stu-id="d8371-142">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="d8371-143">Sahiplik aktarımını destekleyen bir model.</span><span class="sxs-lookup"><span data-stu-id="d8371-143">A model that supports ownership transfer.</span></span> <span data-ttu-id="d8371-144">Bir arabelleğin sahipliği, özgün sahibinden (Oluşturucu) başka bir bileşene aktarılabilir ve bu da arabelleğin yaşam süresi yönetiminden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="d8371-144">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="d8371-145">Bu sahip, sahipliği başka bir bileşene aktarabilir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="d8371-145">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="d8371-146">Bir arabelleğin sahipliğini açıkça yönetmek için <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> arabirimini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d8371-146">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="d8371-147"><xref:System.Buffers.IMemoryOwner%601> hem sahiplik modellerini destekler.</span><span class="sxs-lookup"><span data-stu-id="d8371-147"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="d8371-148"><xref:System.Buffers.IMemoryOwner%601> başvurusuna sahip olan bileşen arabelleğe aittir.</span><span class="sxs-lookup"><span data-stu-id="d8371-148">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="d8371-149">Aşağıdaki örnek, bir <xref:System.Memory%601> arabelleğinin sahipliğini yansıtmak için bir <xref:System.Buffers.IMemoryOwner%601?> örneği kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8371-149">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of an <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="d8371-150">Ayrıca, bu örneği [`using`](../../csharp/language-reference/keywords/using-statement.md)de yazalım:</span><span class="sxs-lookup"><span data-stu-id="d8371-150">We can also write this example with the [`using`](../../csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="d8371-151">Bu kodda:</span><span class="sxs-lookup"><span data-stu-id="d8371-151">In this code:</span></span>

- <span data-ttu-id="d8371-152">`Main` yöntemi <xref:System.Buffers.IMemoryOwner%601> örneğine başvuruyu barındırır, bu nedenle `Main` yöntemi arabelleğin sahibidir.</span><span class="sxs-lookup"><span data-stu-id="d8371-152">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="d8371-153">`WriteInt32ToBuffer` ve `DisplayBufferToConsole` yöntemleri ortak bir API olarak <xref:System.Memory%601> kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d8371-153">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="d8371-154">Bu nedenle, arabelleğin tüketicilerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="d8371-154">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="d8371-155">Ve tek seferde yalnızca bir tane tüketir.</span><span class="sxs-lookup"><span data-stu-id="d8371-155">And they only consume it one at a time.</span></span>

<span data-ttu-id="d8371-156">`WriteInt32ToBuffer` yöntemi arabelleğe bir değer yazmaya yönelik olarak olsa da, `DisplayBufferToConsole` yöntemi değildir.</span><span class="sxs-lookup"><span data-stu-id="d8371-156">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="d8371-157">Bunu yansıtmak için <xref:System.ReadOnlyMemory%601>türünde bir bağımsız değişkeni kabul etmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8371-157">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="d8371-158"><xref:System.ReadOnlyMemory%601>hakkında daha fazla bilgi için bkz. [Rule #2: ReadOnlySpan\<t > veya ReadOnlyMemory\<t > arabellek salt okunurdur](#rule-2).</span><span class="sxs-lookup"><span data-stu-id="d8371-158">For additional information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="d8371-159">"OwnerLeSs" bellek\<T > örnekleri</span><span class="sxs-lookup"><span data-stu-id="d8371-159">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="d8371-160"><xref:System.Buffers.IMemoryOwner%601>kullanmadan bir <xref:System.Memory%601> örneği oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8371-160">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="d8371-161">Bu durumda, arabelleğin sahipliği açık yerine örtük olur ve yalnızca tek sahip modeli desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d8371-161">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="d8371-162">Bunu şu şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d8371-162">You can do this by:</span></span>

- <span data-ttu-id="d8371-163">Aşağıdaki örnekte olduğu gibi, `T[]`geçirerek <xref:System.Memory%601> oluşturuculardan birini doğrudan çağırma.</span><span class="sxs-lookup"><span data-stu-id="d8371-163">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="d8371-164">Bir `ReadOnlyMemory<char>` örneği üretmek için [String. AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) genişletme yöntemi çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="d8371-164">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="d8371-165">Başlangıçta <xref:System.Memory%601> örneğini oluşturan Yöntem, arabelleğin örtük sahibidir.</span><span class="sxs-lookup"><span data-stu-id="d8371-165">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="d8371-166">Aktarımı kolaylaştırmak için <xref:System.Buffers.IMemoryOwner%601> bir örnek bulunmadığından, sahiplik başka bir bileşene aktarılamaz.</span><span class="sxs-lookup"><span data-stu-id="d8371-166">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="d8371-167">(Alternatif olarak, çalışma zamanının çöp toplayıcısının arabelleğe sahip olduğunu ve tüm yöntemlerin arabelleği tükettiği da hayal edebilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="d8371-167">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="d8371-168">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d8371-168">Usage guidelines</span></span>

<span data-ttu-id="d8371-169">Bir bellek bloğunun sahibi olduğu, ancak bazıları aynı anda belirli bir bellek bloğunun üzerinde çalışabilen birden çok bileşene geçirilmesi amaçlanan için, hem <xref:System.Memory%601> hem de <xref:System.Span%601>kullanımı için kılavuz oluşturulması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d8371-169">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="d8371-170">Şu nedenle yönergeler gereklidir:</span><span class="sxs-lookup"><span data-stu-id="d8371-170">Guidelines are necessary because:</span></span>

- <span data-ttu-id="d8371-171">Bir bileşenin sahibi serbest bırakıldıktan sonra bir bellek bloğunun başvurusunu bekletmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="d8371-171">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="d8371-172">Bir bileşenin, başka bir bileşenin üzerinde çalıştığı aynı anda bir arabellekte çalışması, işlemin arabellekteki verileri bozuyor olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="d8371-172">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="d8371-173">Yığın tarafından ayrılan <xref:System.Span%601> yapısı performansı iyileştirirken ve bir bellek bloğunda çalışan için tercih edilen türü <xref:System.Span%601> hale getirirken, bazı önemli kısıtlamalara <xref:System.Span%601> de konu alır.</span><span class="sxs-lookup"><span data-stu-id="d8371-173">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="d8371-174">Ne zaman <xref:System.Span%601> kullanacağınızı ve ne zaman <xref:System.Memory%601>kullanacağınızı bilmemiz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d8371-174">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="d8371-175"><xref:System.Memory%601> ve ilgili türlerini kullanarak başarıyla önerdiğimiz önerilerden bazıları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d8371-175">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="d8371-176"><xref:System.Memory%601> ve <xref:System.Span%601> için geçerli olan yönergelerin, açıkça aksi belirtilmedikçe <xref:System.ReadOnlyMemory%601> ve <xref:System.ReadOnlySpan%601> için de geçerli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d8371-176">Note that guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="d8371-177">**Kural #1: zaman uyumlu bir API Için, mümkünse bir parametre olarak >\<T >, bellek\<T yerine kullanın.**</span><span class="sxs-lookup"><span data-stu-id="d8371-177">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="d8371-178"><xref:System.Span%601>, <xref:System.Memory%601> daha çok daha hızlıdır ve çok sayıda bitişik bellek arabelleğini temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="d8371-178"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="d8371-179"><xref:System.Span%601> Ayrıca <xref:System.Memory%601>daha iyi performans sunar.</span><span class="sxs-lookup"><span data-stu-id="d8371-179"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="d8371-180">Son olarak, bir <xref:System.Memory%601> örneğini <xref:System.Span%601>dönüştürmek için <xref:System.Memory%601.Span?displayProperty=nameWithType> özelliğini kullanabilirsiniz,\<ancak > bellek\<T > dönüştürme mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="d8371-180">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="d8371-181">Bu nedenle, arayanların bir <xref:System.Memory%601> örneğine sahip olması durumunda, yöntemlerinizi <xref:System.Span%601> parametreleri ile çağırabilirler.</span><span class="sxs-lookup"><span data-stu-id="d8371-181">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="d8371-182"><xref:System.Memory%601> türü yerine <xref:System.Span%601> türünde bir parametre kullanılması, doğru bir tüketen Yöntem uygulamasını yazmanıza de yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d8371-182">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="d8371-183">Metodun kira süresinin ötesinde (daha sonra bu konuda daha fazla) arabelleğe erişmeye girişdiğinizden emin olmak için otomatik olarak derleme zamanı denetimleri alacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d8371-183">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="d8371-184">Bazen, tam olarak zaman uyumlu olsanız bile, <xref:System.Span%601> parametresi yerine bir <xref:System.Memory%601> parametresi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8371-184">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="d8371-185">Büyük olasılıkla bağlı olduğunuz bir API yalnızca <xref:System.Memory%601> bağımsız değişkenlerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d8371-185">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="d8371-186">Bu sorun iyidir, ancak <xref:System.Memory%601> zaman uyumlu olarak kullanılırken ilgili olan avantajları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d8371-186">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="d8371-187">**Kural #2: arabelleğin Salt okunabilir olması gerekiyorsa, ReadOnlySpan\<T > veya ReadOnlyMemory\<T > kullanın.**</span><span class="sxs-lookup"><span data-stu-id="d8371-187">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="d8371-188">Önceki örneklerde `DisplayBufferToConsole` yöntemi yalnızca arabellekten okur; arabelleğin içeriğini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="d8371-188">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="d8371-189">Yöntem imzası aşağıdaki şekilde değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d8371-189">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="d8371-190">Aslında, bu kuralı ve kuralı #1 birleştirirseniz, daha iyi bir şekilde yapabiliriz ve yöntem imzasını aşağıdaki gibi yeniden yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d8371-190">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="d8371-191">`DisplayBufferToConsole` yöntemi artık neredeyse her arabellek türü kodlamalardaki: `T[]`, [stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile ayrılmış depolama ve benzeri ile çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8371-191">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), and so on.</span></span> <span data-ttu-id="d8371-192">Hatta, bir <xref:System.String> doğrudan! ' a geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8371-192">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="d8371-193">**Kural #3: yönteminiz, bellek\<T > kabul eder ve `void`döndürürse, yöntemi döndürbaşladıktan sonra bellek\<T > örneğini kullanmamalıdır.**</span><span class="sxs-lookup"><span data-stu-id="d8371-193">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="d8371-194">Bu, daha önce bahsedilen "Kira" kavramıyla ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="d8371-194">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="d8371-195"><xref:System.Memory%601> örneği üzerinde void döndüren bir yöntemin kirası, yöntem girildiğinde başlar ve Yöntem çıktığında sonlanır.</span><span class="sxs-lookup"><span data-stu-id="d8371-195">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="d8371-196">Bir döngüsünde `Log`, konsoldan gelen girişe göre çağıran aşağıdaki örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d8371-196">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="d8371-197">`Log` tamamen zaman uyumlu bir yöntem ise, belirli bir zamanda bellek örneğinin yalnızca bir etkin tüketicisi olduğundan bu kod beklendiği gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="d8371-197">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="d8371-198">Ancak `Log` bu uygulamaya sahip olması yerine düşünün.</span><span class="sxs-lookup"><span data-stu-id="d8371-198">But imagine instead that `Log` has this implementation.</span></span>

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

<span data-ttu-id="d8371-199">Bu uygulamada, özgün Yöntem döndürülmeden sonra hala arka planda <xref:System.Memory%601> örneğini kullanmaya çalıştığı için `Log` kirayı ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="d8371-199">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="d8371-200">`Main` yöntemi, `Log` okumayı denediğinde arabelleği bir süre sonra da veri bozulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8371-200">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="d8371-201">Bu sorunu çözmek için birkaç yol vardır:</span><span class="sxs-lookup"><span data-stu-id="d8371-201">There are several ways to resolve this:</span></span>

- <span data-ttu-id="d8371-202">`Log` yönteminin aşağıdaki uygulanması `Log` yöntemi `void`yerine <xref:System.Threading.Tasks.Task> döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="d8371-202">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="d8371-203">`Log` bunun yerine aşağıdaki gibi uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="d8371-203">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="d8371-204">**Kural #4: yönteminiz bir bellek\<T > kabul ediyorsa ve bir görevi döndürürse, görev bir Terminal durumuna geçirdikten sonra, bellek\<T > örneğini kullanmanız gerekir.**</span><span class="sxs-lookup"><span data-stu-id="d8371-204">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="d8371-205">Bu yalnızca kural #3 zaman uyumsuz bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="d8371-205">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="d8371-206">Önceki örnekteki `Log` yöntemi bu kuralla uyum sağlamak için aşağıdaki gibi yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="d8371-206">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="d8371-207">Burada "Terminal durumu", görevin tamamlanmış, hatalı veya iptal edilmiş durumuna geçirdiğinin anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d8371-207">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="d8371-208">Diğer bir deyişle "Terminal durumu", "çalışmasına neden olan herhangi bir şey" anlamına gelir ve yürütme devam eder. "</span><span class="sxs-lookup"><span data-stu-id="d8371-208">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="d8371-209">Bu kılavuz <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>veya benzer bir tür döndüren yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d8371-209">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="d8371-210">**Kural #5: oluşturucunuz bir parametre olarak bellek\<T > kabul ediyorsa, oluşturulan nesnedeki örnek yöntemleri, bellek\<T > örneği olarak kabul edilir.**</span><span class="sxs-lookup"><span data-stu-id="d8371-210">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="d8371-211">Aşağıdaki örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d8371-211">Consider the following example:</span></span>

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

<span data-ttu-id="d8371-212">Burada `OddValueExtractor` Oluşturucu bir `ReadOnlyMemory<int>` Oluşturucu parametresi olarak kabul eder, bu nedenle oluşturucunun kendisi bir `ReadOnlyMemory<int>` örneğinin tüketicisidir ve döndürülen değer içindeki tüm örnek yöntemleri de orijinal `ReadOnlyMemory<int>` örneğinin tüketicisidir.</span><span class="sxs-lookup"><span data-stu-id="d8371-212">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="d8371-213">Yani, örnek doğrudan `TryReadNextOddValue` yöntemine geçirilmese de `TryReadNextOddValue` `ReadOnlyMemory<int>` örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8371-213">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="d8371-214">**Kural #6: türümde ayarlanabilir bir >\<belleğe (veya eşdeğer bir örnek yöntemi) sahipseniz, söz konusu nesnedeki örnek yöntemleri, bellek\<T > örneği olarak kabul edilir.**</span><span class="sxs-lookup"><span data-stu-id="d8371-214">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="d8371-215">Bu, yalnızca kural #5 bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="d8371-215">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="d8371-216">Bu kural, özellik ayarlayıcıları veya eşdeğer Yöntemler girdilerini yakalama ve kalıcı hale getirilemediği için vardır, bu nedenle aynı nesne üzerindeki örnek yöntemleri yakalanan durumu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d8371-216">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="d8371-217">Aşağıdaki örnek bu kuralı tetikler:</span><span class="sxs-lookup"><span data-stu-id="d8371-217">The following example triggers this rule:</span></span>

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

<span data-ttu-id="d8371-218">**Kural #7: bir ımemoryowner\<T > başvurunuz varsa, bu dosyanın bir noktası atılmalıdır ya da sahipliğini (her ikisi değil) aktarırsınız.**</span><span class="sxs-lookup"><span data-stu-id="d8371-218">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="d8371-219"><xref:System.Memory%601> bir örnek yönetilen veya yönetilmeyen bellek tarafından desteklenen olduğundan, <xref:System.Memory%601> örneğinde gerçekleştirilen iş tamamlandığında sahip <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8371-219">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="d8371-220">Alternatif olarak, sahip, <xref:System.Buffers.IMemoryOwner%601> örneğinin sahipliğini farklı bir bileşene aktarabilir, bu noktada alma bileşeni, uygun zamanda (daha sonra bu konuda daha fazla) <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> çağrılmadan sorumlu olur.</span><span class="sxs-lookup"><span data-stu-id="d8371-220">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="d8371-221"><xref:System.Buffers.MemoryPool%601.Dispose%2A> yöntemi çağıramaması, yönetilmeyen bellek sızıntılarına veya diğer performans düşüşüne neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8371-221">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="d8371-222">Bu kural, <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>gibi Fabrika yöntemlerini çağıran kod için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d8371-222">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d8371-223">Çağıran, döndürülen <xref:System.Buffers.IMemoryOwner%601> sahibi olur ve tamamlandığında örneği elden atma sorumludur.</span><span class="sxs-lookup"><span data-stu-id="d8371-223">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="d8371-224">**Kural #8: API yüzeyinizde ımemoryowner\<T > parametresi varsa, bu örneğin sahipliğini kabul etmiş olursunuz.**</span><span class="sxs-lookup"><span data-stu-id="d8371-224">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="d8371-225">Bu tür bir örneği kabul etmek, bileşeninizin bu örneğin sahipliğini almayı amaçladığı sinyallere işaret eder.</span><span class="sxs-lookup"><span data-stu-id="d8371-225">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="d8371-226">Bileşeniniz, kural #7 göre uygun elden çıkarılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="d8371-226">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="d8371-227"><xref:System.Buffers.IMemoryOwner%601> örneğinin sahipliğini farklı bir bileşene aktaran herhangi bir bileşen, yöntem çağrısının tamamlanmasından sonra bu örneği artık kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8371-227">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8371-228">Oluşturucu bir parametre olarak <xref:System.Buffers.IMemoryOwner%601> kabul ediyorsa, türü <xref:System.IDisposable>uygulamalıdır ve <xref:System.IDisposable.Dispose%2A> yönteminiz <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8371-228">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d8371-229">**Kural #9: zaman uyumlu bir p/Invoke yöntemini sardıysanız, API 'niz bir parametre olarak\<T > yayma kabul etmelidir.**</span><span class="sxs-lookup"><span data-stu-id="d8371-229">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="d8371-230">Kural #1 göre, <xref:System.Span%601> genellikle zaman uyumlu API 'Ler için kullanılacak doğru türdür.</span><span class="sxs-lookup"><span data-stu-id="d8371-230">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="d8371-231">Aşağıdaki örnekte olduğu gibi, [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) anahtar sözcüğü aracılığıyla <xref:System.Span%601> örnekleri sabitleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d8371-231">You can pin <xref:System.Span%601> instances via the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

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

<span data-ttu-id="d8371-232">Önceki örnekte, örneğin, giriş alanı boş ise `pbData` null olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8371-232">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="d8371-233">İhraç edilen yöntem, `cbData` 0 olsa bile null olmayan `pbData` gerektiriyorsa, yöntem aşağıdaki gibi uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="d8371-233">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

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

<span data-ttu-id="d8371-234">**Kural #10: zaman uyumsuz bir p/Invoke yöntemi sarmalandıysanız, API 'niz bir parametre olarak bellek\<T > kabul etmelidir.**</span><span class="sxs-lookup"><span data-stu-id="d8371-234">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="d8371-235">Zaman uyumsuz işlemler arasında [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) anahtar sözcüğünü kullanamıyorsanız, örneğin ardışık bellek türünden bağımsız olarak <xref:System.Memory%601> örnekleri sabitlemek için <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d8371-235">Since you cannot use the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="d8371-236">Aşağıdaki örnek, bu API 'nin zaman uyumsuz p/Invoke çağrısı gerçekleştirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8371-236">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d8371-237">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8371-237">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
