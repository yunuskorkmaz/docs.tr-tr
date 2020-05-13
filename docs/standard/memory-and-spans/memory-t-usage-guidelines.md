---
title: Memory<T> ve Span<T> kullanım yönergeleri
description: Bu makalede <T> <T> , .NET Core 'da işlem hatları 'nda kullanılabilecek yapılandırılmış verilerin arabellekleri olan bellek ve yayılma açıklanmaktadır.
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: b9405d746c141308c7d984dac9da0d65d1048d1e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380008"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="5253d-103">Memory\<T > ve Span\<T > kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5253d-103">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="5253d-104">.NET Core, belleğin rastgele bir bitişik bölgesini temsil eden bir dizi tür içerir.</span><span class="sxs-lookup"><span data-stu-id="5253d-104">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="5253d-105">.NET Core 2,0 <xref:System.Span%601> <xref:System.ReadOnlySpan%601> , yönetilen veya yönetilmeyen bellekle desteklenen basit bellek arabellekleri olan ve tarafından kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5253d-105">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="5253d-106">Bu türler yalnızca yığında depolanabileceğinden, zaman uyumsuz yöntem çağrıları dahil olmak üzere çok sayıda senaryo için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="5253d-106">Because these types can only be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="5253d-107">.NET Core 2,1,,, ve dahil olmak üzere çeşitli ek türler ekler <xref:System.Memory%601> <xref:System.ReadOnlyMemory%601> <xref:System.Buffers.IMemoryOwner%601> <xref:System.Buffers.MemoryPool%601> .</span><span class="sxs-lookup"><span data-stu-id="5253d-107">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="5253d-108">Benzer <xref:System.Span%601> şekilde <xref:System.Memory%601> ve ilgili türleri hem yönetilen hem de yönetilmeyen bellekle desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5253d-108">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="5253d-109">Aksine <xref:System.Span%601> , <xref:System.Memory%601> yönetilen yığında depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="5253d-109">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can be stored on the managed heap.</span></span>

<span data-ttu-id="5253d-110">Her ikisi de, işlem hatlarında <xref:System.Span%601> <xref:System.Memory%601> kullanılabilecek yapılandırılmış verilerin arabelleklerdir.</span><span class="sxs-lookup"><span data-stu-id="5253d-110">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="5253d-111">Diğer bir deyişle, verilerin bazılarının veya tümünün işlem hattındaki bileşenlere etkin bir şekilde geçirilmesi için tasarlanmaları ve isteğe bağlı olarak arabelleği değiştirebilmeleri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5253d-111">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="5253d-112"><xref:System.Memory%601>Ve ilgili türlerine birden çok bileşen veya birden çok iş parçacığı tarafından erişilebildiğinden, geliştiricilerin sağlam kod üretmek için bazı standart kullanım yönergelerini izlemesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5253d-112">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="5253d-113">Sahipler, tüketiciler ve ömür yönetimi</span><span class="sxs-lookup"><span data-stu-id="5253d-113">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="5253d-114">Arabellekler API 'Ler arasında geçirilebileceği ve arabelleklerin bazen birden fazla iş parçacığından erişilebilir olduğundan, ömür yönetimini göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5253d-114">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="5253d-115">Üç temel kavram vardır:</span><span class="sxs-lookup"><span data-stu-id="5253d-115">There are three core concepts:</span></span>

- <span data-ttu-id="5253d-116">**Sahiplik**.</span><span class="sxs-lookup"><span data-stu-id="5253d-116">**Ownership**.</span></span> <span data-ttu-id="5253d-117">Arabellek örneğinin sahibi, artık kullanımda olmadığında arabelleği yok etme da dahil olmak üzere ömür yönetiminden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="5253d-117">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="5253d-118">Tüm arabelleklerin tek bir sahibi vardır.</span><span class="sxs-lookup"><span data-stu-id="5253d-118">All buffers have a single owner.</span></span> <span data-ttu-id="5253d-119">Genellikle sahip, arabelleği oluşturan veya bir fabrikadan arabelleği alan bileşendir.</span><span class="sxs-lookup"><span data-stu-id="5253d-119">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="5253d-120">Sahiplik da aktarılabilir; **Bileşen-a** arabellek denetimini **bileşen-b**' y e yeniden denetleyebilir ve bu noktada, o nokta **bileşeni-A** artık arabellek kullanamaz ve **bileşen-b** artık kullanımda olmadığında arabelleği yok etmeden sorumlu olur.</span><span class="sxs-lookup"><span data-stu-id="5253d-120">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="5253d-121">**Tüketim**.</span><span class="sxs-lookup"><span data-stu-id="5253d-121">**Consumption**.</span></span> <span data-ttu-id="5253d-122">Bir arabellek örneğinin tüketicisi, onu okuyarak ve muhtemelen ona yazarak arabellek örneğini kullanmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="5253d-122">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="5253d-123">Bazı dış eşitleme mekanizması sağlanmadığı takdirde arabellekler tek seferde bir tüketiciye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="5253d-123">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="5253d-124">Bir arabelleğin etkin tüketicisi, arabelleğin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="5253d-124">The active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="5253d-125">**Kira**.</span><span class="sxs-lookup"><span data-stu-id="5253d-125">**Lease**.</span></span> <span data-ttu-id="5253d-126">Kira, belirli bir bileşenin arabelleğin tüketicisi olmasına izin verilen süredir.</span><span class="sxs-lookup"><span data-stu-id="5253d-126">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="5253d-127">Aşağıdaki sözde kod örneğinde bu üç kavram gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5253d-127">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="5253d-128">Bu `Main` , türünde bir arabellek örnekleyen bir yöntemi içerir <xref:System.Memory%601> <xref:System.Char> , `WriteInt32ToBuffer` arabelleğe bir tamsayının dize gösterimini yazmak için yöntemini çağırır ve ardından `DisplayBufferToConsole` arabelleğin değerini göstermek için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="5253d-128">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

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

<span data-ttu-id="5253d-129">`Main`Yöntemi, arabelleği oluşturur (Bu durumda bir <xref:System.Span%601> örnek) ve bu nedenle sahibi olur.</span><span class="sxs-lookup"><span data-stu-id="5253d-129">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="5253d-130">Bu nedenle, `Main` artık kullanımda olmadığında arabelleği yok etmek sorumludur.</span><span class="sxs-lookup"><span data-stu-id="5253d-130">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="5253d-131">Bunu, arabelleğin yöntemini çağırarak yapar <xref:System.Span%601.Clear?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5253d-131">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5253d-132">( <xref:System.Span%601.Clear> Buradaki Yöntem, arabelleğin belleğini temizler; <xref:System.Span%601> yapının aslında arabelleği yok eden bir yöntemi yoktur.)</span><span class="sxs-lookup"><span data-stu-id="5253d-132">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="5253d-133">Arabellek iki tüketiciye sahiptir `WriteInt32ToBuffer` ve `DisplayBufferToConsole` .</span><span class="sxs-lookup"><span data-stu-id="5253d-133">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="5253d-134">Tek seferde yalnızca bir tüketici vardır (ilk `WriteInt32ToBuffer` , sonra `DisplayBufferToConsole` ) ve hiçbir tüketicisinin arabelleğe sahip olmadığı.</span><span class="sxs-lookup"><span data-stu-id="5253d-134">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="5253d-135">Ayrıca, bu bağlamda "Consumer" öğesinin, arabelleğin salt okunurdur görünümünü göstermez; müşteriler, arabelleğin `WriteInt32ToBuffer` okuma/yazma görünümü verildiyse, olduğu gibi arabelleğin içeriğini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="5253d-135">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="5253d-136">Yöntemi, `WriteInt32ToBuffer` yöntem çağrısının başlangıcı ve yöntemin döndürdüğü zaman arasındaki arabelleği (tüketebilir) üzerinde bir kira içerir.</span><span class="sxs-lookup"><span data-stu-id="5253d-136">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="5253d-137">Benzer şekilde, `DisplayBufferToConsole` yürütülürken arabellekte bir kiralama vardır ve kira yöntemi zaman içinde serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="5253d-137">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="5253d-138">(Kiralama Yönetimi için bir API yoktur; "Kira" kavramsal bir kavramdır.)</span><span class="sxs-lookup"><span data-stu-id="5253d-138">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="5253d-139">Bellek \< T> ve sahip/tüketici modeli</span><span class="sxs-lookup"><span data-stu-id="5253d-139">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="5253d-140">[Sahipler, tüketiciler ve ömür yönetimi](#owners-consumers-and-lifetime-management) bölümünde, bir arabelleğin her zaman bir sahibi vardır.</span><span class="sxs-lookup"><span data-stu-id="5253d-140">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="5253d-141">.NET Core iki sahiplik modelini destekler:</span><span class="sxs-lookup"><span data-stu-id="5253d-141">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="5253d-142">Tek sahipliği destekleyen bir model.</span><span class="sxs-lookup"><span data-stu-id="5253d-142">A model that supports single ownership.</span></span> <span data-ttu-id="5253d-143">Bir arabelleğin tüm ömrü için tek bir sahibi vardır.</span><span class="sxs-lookup"><span data-stu-id="5253d-143">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="5253d-144">Sahiplik aktarımını destekleyen bir model.</span><span class="sxs-lookup"><span data-stu-id="5253d-144">A model that supports ownership transfer.</span></span> <span data-ttu-id="5253d-145">Bir arabelleğin sahipliği, özgün sahibinden (Oluşturucu) başka bir bileşene aktarılabilir ve bu da arabelleğin yaşam süresi yönetiminden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="5253d-145">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="5253d-146">Bu sahip, sahipliği başka bir bileşene aktarabilir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="5253d-146">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="5253d-147"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>Bir arabelleğin sahipliğini açıkça yönetmek için arabirimini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5253d-147">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="5253d-148"><xref:System.Buffers.IMemoryOwner%601>Her iki sahiplik modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="5253d-148"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="5253d-149">Bir başvurusuna sahip olan bileşen <xref:System.Buffers.IMemoryOwner%601> , arabelleğe aittir.</span><span class="sxs-lookup"><span data-stu-id="5253d-149">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="5253d-150">Aşağıdaki örnek, bir <xref:System.Buffers.IMemoryOwner%601?> arabelleğin sahipliğini yansıtmak için bir örneği kullanır <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="5253d-150">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of an <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="5253d-151">Bu örneği ile de yazalım [`using`](../../csharp/language-reference/keywords/using-statement.md) :</span><span class="sxs-lookup"><span data-stu-id="5253d-151">We can also write this example with the [`using`](../../csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="5253d-152">Bu kodda:</span><span class="sxs-lookup"><span data-stu-id="5253d-152">In this code:</span></span>

- <span data-ttu-id="5253d-153">`Main`Yöntemi örneğin başvurusunu barındırır <xref:System.Buffers.IMemoryOwner%601> , bu nedenle `Main` Yöntem arabelleğin sahibidir.</span><span class="sxs-lookup"><span data-stu-id="5253d-153">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="5253d-154">`WriteInt32ToBuffer`Ve `DisplayBufferToConsole` yöntemleri <xref:System.Memory%601> ortak bir API olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="5253d-154">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="5253d-155">Bu nedenle, arabelleğin tüketicilerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="5253d-155">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="5253d-156">Ve tek seferde yalnızca bir tane tüketir.</span><span class="sxs-lookup"><span data-stu-id="5253d-156">And they only consume it one at a time.</span></span>

<span data-ttu-id="5253d-157">Yöntemi, `WriteInt32ToBuffer` arabelleğe bir değer yazmaya yönelik olarak düşünülse de `DisplayBufferToConsole` yöntem değildir.</span><span class="sxs-lookup"><span data-stu-id="5253d-157">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="5253d-158">Bunu yansıtmak için, türünde bir bağımsız değişkeni kabul etmiş olabilir <xref:System.ReadOnlyMemory%601> .</span><span class="sxs-lookup"><span data-stu-id="5253d-158">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="5253d-159">Hakkında daha fazla bilgi için <xref:System.ReadOnlyMemory%601> bkz. [Kural #2: \< \< arabelleğin Salt-okunabilir olması gerekiyorsa, readonlyspan t> veya readonlymemory t> kullanın](#rule-2).</span><span class="sxs-lookup"><span data-stu-id="5253d-159">For more information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="5253d-160">"OwnerLeSs" bellek \< T> örnekleri</span><span class="sxs-lookup"><span data-stu-id="5253d-160">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="5253d-161">Kullanmadan bir örnek oluşturabilirsiniz <xref:System.Memory%601> <xref:System.Buffers.IMemoryOwner%601> .</span><span class="sxs-lookup"><span data-stu-id="5253d-161">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="5253d-162">Bu durumda, arabelleğin sahipliği açık yerine örtük olur ve yalnızca tek sahip modeli desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5253d-162">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="5253d-163">Bunu şu şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5253d-163">You can do this by:</span></span>

- <span data-ttu-id="5253d-164"><xref:System.Memory%601>Oluşturuculardan birini doğrudan çağırmak, `T[]` Aşağıdaki örnekte olduğu gibi bir ' a geçirerek.</span><span class="sxs-lookup"><span data-stu-id="5253d-164">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="5253d-165">Bir örnek oluşturmak için [String. AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) genişletme yöntemi çağrılıyor `ReadOnlyMemory<char>` .</span><span class="sxs-lookup"><span data-stu-id="5253d-165">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="5253d-166">İlk olarak örneği oluşturan yöntemi, <xref:System.Memory%601> arabelleğin örtük sahibidir.</span><span class="sxs-lookup"><span data-stu-id="5253d-166">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="5253d-167">Aktarımı kolaylaştırmak için bir örnek bulunmadığından, sahiplik başka bir bileşene aktarılamaz <xref:System.Buffers.IMemoryOwner%601> .</span><span class="sxs-lookup"><span data-stu-id="5253d-167">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="5253d-168">(Alternatif olarak, çalışma zamanının çöp toplayıcısının arabelleğe sahip olduğunu ve tüm yöntemlerin arabelleği tükettiği da hayal edebilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="5253d-168">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="5253d-169">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5253d-169">Usage guidelines</span></span>

<span data-ttu-id="5253d-170">Bir bellek bloğunun sahibi olduğu, ancak bazıları aynı anda belirli bir bellek bloğunun üzerinde çalışabilen birden çok bileşene geçirilmesi amaçlanan için, hem hem de kullanımı için kılavuz oluşturulması önemlidir <xref:System.Memory%601> <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="5253d-170">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="5253d-171">Şu nedenle yönergeler gereklidir:</span><span class="sxs-lookup"><span data-stu-id="5253d-171">Guidelines are necessary because:</span></span>

- <span data-ttu-id="5253d-172">Bir bileşenin sahibi serbest bırakıldıktan sonra bir bellek bloğunun başvurusunu bekletmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5253d-172">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="5253d-173">Bir bileşenin, başka bir bileşenin üzerinde çalıştığı aynı anda bir arabellekte çalışması, işlemin arabellekteki verileri bozuyor olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5253d-173">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="5253d-174">Yığın tarafından ayrılan doğası <xref:System.Span%601> performansı iyileştirir ve <xref:System.Span%601> tercih edilen türü bir bellek bloğunda çalıştırmak için, bu da <xref:System.Span%601> bazı önemli kısıtlamalara de neden olur.</span><span class="sxs-lookup"><span data-stu-id="5253d-174">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="5253d-175">Ne zaman kullanacağınızı ve ne zaman kullanılacağını bilmemiz önemlidir <xref:System.Span%601> <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="5253d-175">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="5253d-176">Aşağıdakiler ve ilgili türleri başarıyla kullanılarak önerimlerimiz aşağıda verilmiştir <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="5253d-176">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="5253d-177">İçin geçerli olan <xref:System.Memory%601> ve <xref:System.Span%601> Ayrıca <xref:System.ReadOnlyMemory%601> , <xref:System.ReadOnlySpan%601> açıkça aksi belirtilmedikçe ve için geçerli olan rehberlik.</span><span class="sxs-lookup"><span data-stu-id="5253d-177">Guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="5253d-178">**Kural #1: zaman uyumlu bir API Için, \< \< Mümkünse bir parametre olarak> bellek t yerine> span t kullanın.**</span><span class="sxs-lookup"><span data-stu-id="5253d-178">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="5253d-179"><xref:System.Span%601>daha çok daha hızlıdır <xref:System.Memory%601> ve çok sayıda bitişik bellek arabelleğini temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="5253d-179"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="5253d-180"><xref:System.Span%601>Ayrıca, daha iyi performans sunar <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="5253d-180"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="5253d-181">Son olarak, <xref:System.Memory%601.Span?displayProperty=nameWithType> özelliği <xref:System.Memory%601> bir örneği bir örneğine dönüştürmek için kullanabilirsiniz <xref:System.Span%601> , ancak \< t>-bellek \< t> dönüştürme mümkün olmaz.</span><span class="sxs-lookup"><span data-stu-id="5253d-181">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="5253d-182">Bu nedenle, arayanların bir örneği varsa <xref:System.Memory%601> , yöntemlerinizi <xref:System.Span%601> yine de parametrelerle çağırabileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5253d-182">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="5253d-183">Türü yerine türünde bir parametre kullanılması <xref:System.Span%601> <xref:System.Memory%601> , doğru bir tüketen Yöntem uygulamasını yazmanıza de yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="5253d-183">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="5253d-184">Metodun kira süresinin ötesinde (daha sonra bu konuda daha fazla) arabelleğe erişmeye girişdiğinizden emin olmak için otomatik olarak derleme zamanı denetimleri alacaksınız.</span><span class="sxs-lookup"><span data-stu-id="5253d-184">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="5253d-185">Bazen, <xref:System.Memory%601> <xref:System.Span%601> tam olarak zaman uyumlu olsanız bile parametre yerine bir parametre kullanmanız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="5253d-185">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="5253d-186">Büyük olasılıkla bağlı olduğunuz bir API yalnızca <xref:System.Memory%601> bağımsız değişkenleri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="5253d-186">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="5253d-187">Bu sorun iyidir, ancak eşzamanlı olarak kullanılırken ilgili olan avantajları göz önünde bulundurun <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="5253d-187">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="5253d-188">**Kural #2: \< \< arabelleğin Salt okunabilir olması gerekiyorsa ReadOnlySpan t> veya ReadOnlyMemory t> kullanın.**</span><span class="sxs-lookup"><span data-stu-id="5253d-188">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="5253d-189">Önceki örneklerde `DisplayBufferToConsole` Yöntem yalnızca arabellekten okur; arabelleğin içeriğini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="5253d-189">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="5253d-190">Yöntem imzası aşağıdaki şekilde değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5253d-190">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="5253d-191">Aslında, bu kuralı ve kuralı #1 birleştirirseniz, daha iyi bir şekilde yapabiliriz ve yöntem imzasını aşağıdaki gibi yeniden yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5253d-191">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="5253d-192">`DisplayBufferToConsole`Yöntemi artık hemen her arabellek türü kodlamalardaki: `T[]` , [stackalloc](../../csharp/language-reference/operators/stackalloc.md)ile ayrılmış depolama ve benzeri ile çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5253d-192">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), and so on.</span></span> <span data-ttu-id="5253d-193">Hatta doğrudan ' a geçirebilirsiniz <xref:System.String> !</span><span class="sxs-lookup"><span data-stu-id="5253d-193">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="5253d-194">**Kural #3: yönteminiz \< , bellek t> ve döndürürse `void` , \< yönteminizin döndürdüğü bir bellek t> örneğini kullanmamalıdır.**</span><span class="sxs-lookup"><span data-stu-id="5253d-194">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="5253d-195">Bu, daha önce bahsedilen "Kira" kavramıyla ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="5253d-195">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="5253d-196">Örnek üzerinde void döndüren bir yöntemin kirası, <xref:System.Memory%601> Yöntem girildiğinde başlar ve Yöntem çıktığında sonlanır.</span><span class="sxs-lookup"><span data-stu-id="5253d-196">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="5253d-197">`Log`Bir döngüde konsolundan gelen giriş temelinde çağıran aşağıdaki örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5253d-197">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="5253d-198">`Log`Tamamen zaman uyumlu bir yöntem ise, belirli bir zamanda bellek örneğinin yalnızca bir etkin tüketicisi olduğundan bu kod beklendiği gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="5253d-198">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="5253d-199">Ancak bu uygulamayı içeren yerine Imagine `Log` .</span><span class="sxs-lookup"><span data-stu-id="5253d-199">But imagine instead that `Log` has this implementation.</span></span>

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

<span data-ttu-id="5253d-200">Bu uygulamada, `Log` <xref:System.Memory%601> özgün Yöntem döndürülbaşladıktan sonra örneği hala arka planda kullanmaya çalıştığı için kiralamasını ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="5253d-200">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="5253d-201">Yöntem, bir `Main` arabelleği `Log` okumaya çalışırken, veri bozulmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="5253d-201">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="5253d-202">Bu sorunu çözmek için birkaç yol vardır:</span><span class="sxs-lookup"><span data-stu-id="5253d-202">There are several ways to resolve this:</span></span>

- <span data-ttu-id="5253d-203">Yöntemi, `Log` <xref:System.Threading.Tasks.Task> `void` yönteminin aşağıdaki uygulanması olduğundan, yerine bir döndürebilir `Log` .</span><span class="sxs-lookup"><span data-stu-id="5253d-203">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="5253d-204">`Log`Bunun yerine, aşağıdaki gibi uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="5253d-204">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="5253d-205">**Kural #4: yönteminiz bir bellek \< t> kabul eder ve bir görevi döndürürse, \< görev bir Terminal durumuna geçirdikten sonra bellek t> örneğini kullanmanız gerekir.**</span><span class="sxs-lookup"><span data-stu-id="5253d-205">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="5253d-206">Bu yalnızca kural #3 zaman uyumsuz bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="5253d-206">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="5253d-207">`Log`Önceki örnekteki yöntem bu kurala uymak için aşağıdaki gibi yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="5253d-207">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="5253d-208">Burada "Terminal durumu", görevin tamamlanmış, hatalı veya iptal edilmiş durumuna geçirdiğinin anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5253d-208">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="5253d-209">Diğer bir deyişle "Terminal durumu", "çalışmasına neden olan herhangi bir şey" anlamına gelir ve yürütme devam eder. "</span><span class="sxs-lookup"><span data-stu-id="5253d-209">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="5253d-210">Bu kılavuz,,, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.ValueTask%601> veya benzer bir tür döndüren yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5253d-210">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="5253d-211">**Kural #5: oluşturucunuz \< bir parametre olarak bellek t> kabul ediyorsa, oluşturulan nesnedeki örnek yöntemlerinin, bellek t> örneğinin tüketicileri olduğu varsayılır \< .**</span><span class="sxs-lookup"><span data-stu-id="5253d-211">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="5253d-212">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="5253d-212">Consider the following example:</span></span>

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

<span data-ttu-id="5253d-213">Burada Oluşturucu bir `OddValueExtractor` `ReadOnlyMemory<int>` Oluşturucu parametresi olarak kabul eder, bu nedenle oluşturucunun kendisi `ReadOnlyMemory<int>` Örneğin bir tüketicisidir ve döndürülen değer içindeki tüm örnek yöntemleri de orijinal Örneğin tüketicisidir `ReadOnlyMemory<int>` .</span><span class="sxs-lookup"><span data-stu-id="5253d-213">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="5253d-214">Bu, `TryReadNextOddValue` `ReadOnlyMemory<int>` Örneğin, örnek doğrudan yöntemine geçirilmese de örneği tükettiği anlamına gelir `TryReadNextOddValue` .</span><span class="sxs-lookup"><span data-stu-id="5253d-214">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="5253d-215">**Kural #6: türinizde ayarlanabilir bir> bellek \< (veya eşdeğer bir örnek yöntemi) varsa, söz konusu nesnedeki örnek yöntemleri bellek t> örneğinin tüketicileri olduğu varsayılır \< .**</span><span class="sxs-lookup"><span data-stu-id="5253d-215">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="5253d-216">Bu, yalnızca kural #5 bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="5253d-216">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="5253d-217">Bu kural, özellik ayarlayıcıları veya eşdeğer Yöntemler girdilerini yakalama ve kalıcı hale getirilemediği için vardır, bu nedenle aynı nesne üzerindeki örnek yöntemleri yakalanan durumu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5253d-217">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="5253d-218">Aşağıdaki örnek bu kuralı tetikler:</span><span class="sxs-lookup"><span data-stu-id="5253d-218">The following example triggers this rule:</span></span>

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

<span data-ttu-id="5253d-219">**Kural #7: bir ımemoryowner \< T> başvurunuz varsa, bu dosyanın bir noktası atılmalıdır veya sahipliğini (her ikisi de değil) aktarırsınız.**</span><span class="sxs-lookup"><span data-stu-id="5253d-219">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="5253d-220">Bir <xref:System.Memory%601> örnek yönetilen veya yönetilmeyen bellek tarafından yönetilebileceği için, <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> örnek üzerinde gerçekleştirilen iş tamamlandığında sahip çağrısı gerekir <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="5253d-220">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="5253d-221">Alternatif olarak, sahip, <xref:System.Buffers.IMemoryOwner%601> Örneğin sahipliğini farklı bir bileşene aktarabilir, bu noktada alma bileşeni <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> uygun zamanda (Bu daha sonra daha fazla) (daha fazla daha fazla) çağrı yapmaktan sorumlu olur.</span><span class="sxs-lookup"><span data-stu-id="5253d-221">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="5253d-222">Yöntemi çağıramaması, <xref:System.Buffers.MemoryPool%601.Dispose%2A> yönetilmeyen bellek sızıntılarına veya diğer performans düşüşüne neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="5253d-222">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="5253d-223">Bu kural, gibi Fabrika yöntemlerini çağıran kod için de geçerlidir <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5253d-223">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5253d-224">Çağıran, döndürülen sahibi olur <xref:System.Buffers.IMemoryOwner%601> ve tamamlandığında örneği elden atma sorumludur.</span><span class="sxs-lookup"><span data-stu-id="5253d-224">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="5253d-225">**Kural #8: API yüzeyinizde bir ımemoryowner \< T> parametresi varsa, bu örneğin sahipliğini kabul etmiş olursunuz.**</span><span class="sxs-lookup"><span data-stu-id="5253d-225">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="5253d-226">Bu tür bir örneği kabul etmek, bileşeninizin bu örneğin sahipliğini almayı amaçladığı sinyallere işaret eder.</span><span class="sxs-lookup"><span data-stu-id="5253d-226">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="5253d-227">Bileşeniniz, kural #7 göre uygun elden çıkarılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="5253d-227">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="5253d-228">Örneğin sahipliğini farklı bir bileşene aktaran herhangi bir bileşen <xref:System.Buffers.IMemoryOwner%601> , yöntem çağrısının tamamlanmasından sonra bu örneği artık kullanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5253d-228">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5253d-229">Oluşturucunuzu <xref:System.Buffers.IMemoryOwner%601> bir parametre olarak kabul ediyorsa, türünün uygulanması gerekir <xref:System.IDisposable> ve <xref:System.IDisposable.Dispose%2A> yöntemi çağırmalıdır <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5253d-229">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="5253d-230">**Kural #9: zaman uyumlu bir p/Invoke yöntemini sardıysanız, API 'niz \< bir parametre olarak span T> kabul etmelidir.**</span><span class="sxs-lookup"><span data-stu-id="5253d-230">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="5253d-231">Kural #1 göre <xref:System.Span%601> genellikle zaman uyumlu API 'ler için kullanılan doğru türdür.</span><span class="sxs-lookup"><span data-stu-id="5253d-231">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="5253d-232"><xref:System.Span%601> [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) Aşağıdaki örnekte olduğu gibi, örnekleri anahtar sözcük aracılığıyla sabitleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5253d-232">You can pin <xref:System.Span%601> instances via the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

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

<span data-ttu-id="5253d-233">`pbData`Örneğin, giriş alanı boş ise, önceki örnekte null olabilir.</span><span class="sxs-lookup"><span data-stu-id="5253d-233">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="5253d-234">İçe aktarılmış Yöntem, `pbData` 0 olsa bile null olmayan bir değer gerektiriyorsa, `cbData` yöntemi aşağıdaki gibi uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="5253d-234">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

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

<span data-ttu-id="5253d-235">**Kural #10: zaman uyumsuz bir p/Invoke yöntemi sarmalandıysanız, API 'niz \< bir parametre olarak bellek T> kabul etmelidir.**</span><span class="sxs-lookup"><span data-stu-id="5253d-235">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="5253d-236">[`fixed`](../../csharp/language-reference/keywords/fixed-statement.md)Anahtar sözcüğünü zaman uyumsuz işlemler arasında kullanamıyorsanız, <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> <xref:System.Memory%601> Örneğin ardışık bellek türünden bağımsız olarak örnekleri sabitlemek için yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5253d-236">Since you cannot use the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="5253d-237">Aşağıdaki örnek, bu API 'nin zaman uyumsuz p/Invoke çağrısı gerçekleştirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5253d-237">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

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
    var actualState = (MyCompletedCallbackState)(handle.Target);
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

## <a name="see-also"></a><span data-ttu-id="5253d-238">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5253d-238">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
