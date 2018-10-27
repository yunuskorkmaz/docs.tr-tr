---
title: Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 134a219acd02caa2b16c5a6e8716c3245579ecca
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50049561"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="47ae8-102">Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="47ae8-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="47ae8-103">C# ' ta kullanabileceğiniz [sabit](../../language-reference/keywords/fixed-statement.md) deyimini bir sabit boyutlu diziye bir veri yapısına sahip bir arabellek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47ae8-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="47ae8-104">Sabit boyutlu arabellekler, yöntemler diğer dillerde veya platformlarda veri kaynaklarıyla bu birlikte çalışma yazmak olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="47ae8-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="47ae8-105">Sabit dizi herhangi bir öznitelik veya normal Yapı üyeleri için izin verilen değiştiriciler alabilir.</span><span class="sxs-lookup"><span data-stu-id="47ae8-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="47ae8-106">Yalnızca dizi türü olmalıdır kısıtlamadır `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, veya `double`.</span><span class="sxs-lookup"><span data-stu-id="47ae8-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="47ae8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47ae8-107">Remarks</span></span>

<span data-ttu-id="47ae8-108">Güvenli kod içinde bir dizi içeren bir C# yapı dizi öğeleri içermiyor.</span><span class="sxs-lookup"><span data-stu-id="47ae8-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="47ae8-109">Bunun yerine, yapı öğeleri bir başvuru içeriyor.</span><span class="sxs-lookup"><span data-stu-id="47ae8-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="47ae8-110">İçinde sabit boyutlu bir dizi katıştırabilirsiniz bir [yapı](../../language-reference/keywords/struct.md) içinde kullanıldığında bir [güvenli](../../language-reference/keywords/unsafe.md) kod bloğu.</span><span class="sxs-lookup"><span data-stu-id="47ae8-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="47ae8-111">Aşağıdaki `struct` 8 bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="47ae8-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="47ae8-112">`pathName` Başvuru dizisidir:</span><span class="sxs-lookup"><span data-stu-id="47ae8-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="47ae8-113">A `struct` güvenli olmayan kod içinde gömülü bir dizi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="47ae8-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="47ae8-114">Aşağıdaki örnekte, `fixedBuffer` dizi sabit bir boyuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="47ae8-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="47ae8-115">Kullandığınız bir `fixed` ilk öğeye bir işaretçi kurmak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="47ae8-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="47ae8-116">Bu işaretçiyle dizinin öğeleri eriştiğinize.</span><span class="sxs-lookup"><span data-stu-id="47ae8-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="47ae8-117">`fixed` Deyimi PIN'ler `fixedBuffer` bellekte belirli bir konuma örnek alanı.</span><span class="sxs-lookup"><span data-stu-id="47ae8-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="47ae8-118">128 öğe `char` 256 bayt dizisidir.</span><span class="sxs-lookup"><span data-stu-id="47ae8-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="47ae8-119">Boyutu sabit [char](../../language-reference/keywords/char.md) arabellekler her zaman, bağımsız olarak kodlama karakter başına iki bayttan yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="47ae8-119">Fixed size [char](../../language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="47ae8-120">Bu da zaman char arabellekler API yöntemleri veya yapılar ile sıralanmış geçerlidir `CharSet = CharSet.Auto` veya `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="47ae8-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="47ae8-121">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="47ae8-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="47ae8-122">Yukarıdaki örnekte erişme gösterir `fixed` sürümünden itibaren kullanılabilir olan sabitleme, olmadan alanları C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="47ae8-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="47ae8-123">Başka bir ortak sabit boyutlu dizi [bool](../../language-reference/keywords/bool.md) dizisi.</span><span class="sxs-lookup"><span data-stu-id="47ae8-123">Another common fixed-size array is the [bool](../../language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="47ae8-124">Öğeleri bir `bool` dizi her zaman tek bir bayt boyutunda.</span><span class="sxs-lookup"><span data-stu-id="47ae8-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="47ae8-125">`bool` diziler bit diziler veya arabellekler oluşturmak için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="47ae8-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="47ae8-126">Kullanılarak oluşturulan bellek dışında [stackalloc](../../language-reference/keywords/stackalloc.md), C# Derleyici ve ortak dil çalışma zamanı (CLR) herhangi bir güvenlik arabellek taşma denetimi gerçekleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="47ae8-126">Except for memory created by using [stackalloc](../../language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="47ae8-127">Tüm güvenli olmayan kod gibi dikkatli kullanın.</span><span class="sxs-lookup"><span data-stu-id="47ae8-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="47ae8-128">Güvenli olmayan arabellekler normal dizilerden şu bakımlardan ayrılır:</span><span class="sxs-lookup"><span data-stu-id="47ae8-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="47ae8-129">Bu gibi durumlarda, güvenli olmayan arabellekler yalnızca güvenli olmayan bir bağlamda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47ae8-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="47ae8-130">Güvenli olmayan arabellekler, vektör veya tek boyutlu diziler her zaman olur.</span><span class="sxs-lookup"><span data-stu-id="47ae8-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="47ae8-131">Dizi bildirimi bir sayı gibi bulunması `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="47ae8-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="47ae8-132">Kullanamazsınız `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="47ae8-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="47ae8-133">Güvenli olmayan arabellekler yalnızca güvenli olmayan bir bağlamda yapılar örnek alanları olabilir.</span><span class="sxs-lookup"><span data-stu-id="47ae8-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="47ae8-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47ae8-134">See Also</span></span>

- [<span data-ttu-id="47ae8-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="47ae8-135">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="47ae8-136">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="47ae8-136">Unsafe Code and Pointers</span></span>](index.md)  
- [<span data-ttu-id="47ae8-137">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="47ae8-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="47ae8-138">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="47ae8-138">Interoperability</span></span>](../interop/index.md)
