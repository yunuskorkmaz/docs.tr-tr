---
title: Sabit Boyut Arabellekleri - C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 6770497b23212f1786b4f4a620ed2b650079c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157032"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="29137-102">Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="29137-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="29137-103">C#'da, veri yapısında sabit boyut dizilimi olan bir arabellek oluşturmak için [sabit](../../language-reference/keywords/fixed-statement.md) ifadeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29137-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="29137-104">Sabit boyut arabellekleri, diğer dillerden veya platformlardan gelen veri kaynaklarıyla kesişen yöntemler yazarken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="29137-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="29137-105">Sabit dizi, normal yapı üyeleri için izin verilen öznitelikleri veya değiştiriciler alabilir.</span><span class="sxs-lookup"><span data-stu-id="29137-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="29137-106">Tek kısıtlama, dizi türünün `bool`, `byte` `char`, `short` `int`, `long` `sbyte` `ushort` `uint` `ulong`, , `float`, `double`, , , veya .</span><span class="sxs-lookup"><span data-stu-id="29137-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="29137-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29137-107">Remarks</span></span>

<span data-ttu-id="29137-108">Güvenli kodda, dizi içeren bir C# struct dizi öğelerini içermez.</span><span class="sxs-lookup"><span data-stu-id="29137-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="29137-109">Bunun yerine, yapı öğeleri için bir başvuru içerir.</span><span class="sxs-lookup"><span data-stu-id="29137-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="29137-110">[Güvenli olmayan](../../language-reference/keywords/unsafe.md) bir kod bloğunda kullanıldığında bir [yapıya](../../language-reference/builtin-types/struct.md) sabit boyut dizisini katıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29137-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="29137-111">Aşağıdakilerin `struct` boyutu dizideki öğe sayısına bağlı değildir, `pathName` çünkü bir başvurudur:</span><span class="sxs-lookup"><span data-stu-id="29137-111">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="29137-112">A, `struct` güvenli olmayan kodda gömülü bir dizi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="29137-112">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="29137-113">Aşağıdaki örnekte, `fixedBuffer` dizi sabit bir boyuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="29137-113">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="29137-114">İlk öğeye işaretçi oluşturmak için bir `fixed` deyim kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="29137-114">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="29137-115">Bu işaretçi aracılığıyla dizinin öğelerine erişin.</span><span class="sxs-lookup"><span data-stu-id="29137-115">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="29137-116">İfade, `fixed` `fixedBuffer` örnek alanını bellekte belirli bir konuma sabitler.</span><span class="sxs-lookup"><span data-stu-id="29137-116">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="29137-117">128 öğe `char` dizisinin boyutu 256 bayttır.</span><span class="sxs-lookup"><span data-stu-id="29137-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="29137-118">Sabit boyutlu [char](../../language-reference/builtin-types/char.md) arabellekleri, kodlamadan bağımsız olarak her zaman karakter başına iki bayt alır.</span><span class="sxs-lookup"><span data-stu-id="29137-118">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="29137-119">Bu, char arabellekleri API yöntemlerine veya structs'a marshaled olduğunda bile `CharSet = CharSet.Auto` geçerlidir. `CharSet = CharSet.Ansi`</span><span class="sxs-lookup"><span data-stu-id="29137-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="29137-120">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="29137-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="29137-121">Önceki örnek, C# `fixed` 7.3'ten başlayarak kullanılabilen sabitleme olmadan alanlara erişmelerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="29137-121">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="29137-122">Başka bir ortak sabit boyutlu dizi [bool](../../language-reference/builtin-types/bool.md) dizisidir.</span><span class="sxs-lookup"><span data-stu-id="29137-122">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="29137-123">Dizideki `bool` öğeler her zaman bir bayt boyutundadır.</span><span class="sxs-lookup"><span data-stu-id="29137-123">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="29137-124">`bool`diziler bit dizileri veya arabellekoluşturmak için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="29137-124">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="29137-125">[Stackalloc](../../language-reference/operators/stackalloc.md)kullanılarak oluşturulan bellek dışında, C# derleyicisi ve ortak dil çalışma süresi (CLR) herhangi bir güvenlik arabellek taşma denetimleri gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="29137-125">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="29137-126">Tüm güvenli olmayan kodda olduğu gibi dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="29137-126">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="29137-127">Güvenli olmayan arabellekler aşağıdaki şekillerde normal dizilerden farklıdır:</span><span class="sxs-lookup"><span data-stu-id="29137-127">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="29137-128">Yalnızca güvenli olmayan bir bağlamda güvenli olmayan arabellekler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29137-128">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="29137-129">Güvenli olmayan arabellekler her zaman vektörveya tek boyutlu dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="29137-129">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="29137-130">Dizinin bildirimi, `char id[8]`'.</span><span class="sxs-lookup"><span data-stu-id="29137-130">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="29137-131">Bunu kullanamazsınız. `char id[]`</span><span class="sxs-lookup"><span data-stu-id="29137-131">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="29137-132">Güvenli olmayan arabellekler yalnızca güvenli olmayan bir bağlamda yapı alanları olabilir.</span><span class="sxs-lookup"><span data-stu-id="29137-132">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="29137-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29137-133">See also</span></span>

- [<span data-ttu-id="29137-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="29137-134">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="29137-135">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="29137-135">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="29137-136">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="29137-136">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="29137-137">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="29137-137">Interoperability</span></span>](../interop/index.md)
