---
title: Sabit boyutlu arabellekler- C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: b5be6892a265f0a2b7f3109321fdcf46d4b0ea22
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711850"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="d5334-102">Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d5334-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="d5334-103">İçinde C#, bir veri yapısında sabit boyutlu bir diziye sahip bir arabellek oluşturmak için [fixed](../../language-reference/keywords/fixed-statement.md) ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5334-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="d5334-104">Sabit boyutlu arabellekler, diğer dillerdeki veya platformlardaki veri kaynaklarıyla birlikte bulunan Yöntemler yazdığınızda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5334-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="d5334-105">Sabit dizi, normal yapı üyeleri için izin verilen herhangi bir özniteliği veya değiştiricilerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="d5334-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="d5334-106">Tek kısıtlama, dizi türünün `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`veya `double`olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5334-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="d5334-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5334-107">Remarks</span></span>

<span data-ttu-id="d5334-108">Güvenli kodda, dizi içeren C# bir struct dizi öğelerini içermez.</span><span class="sxs-lookup"><span data-stu-id="d5334-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="d5334-109">Bunun yerine, yapı öğelerine bir başvuru içerir.</span><span class="sxs-lookup"><span data-stu-id="d5334-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="d5334-110">[Güvenli olmayan](../../language-reference/keywords/unsafe.md) bir kod bloğunda kullanıldığında bir [yapıda](../../language-reference/keywords/struct.md) sabit boyutlu bir dizi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5334-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="d5334-111">Aşağıdaki `struct` boyutu 8 bayttır.</span><span class="sxs-lookup"><span data-stu-id="d5334-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="d5334-112">`pathName` dizi bir başvurudur:</span><span class="sxs-lookup"><span data-stu-id="d5334-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="d5334-113">`struct`, güvenli olmayan kodda gömülü bir dizi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d5334-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="d5334-114">Aşağıdaki örnekte, `fixedBuffer` dizisinin sabit bir boyutu vardır.</span><span class="sxs-lookup"><span data-stu-id="d5334-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="d5334-115">İlk öğe için bir işaretçi oluşturmak üzere bir `fixed` ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5334-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="d5334-116">Bu işaretçi aracılığıyla dizinin öğelerine erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5334-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="d5334-117">`fixed` ifade `fixedBuffer` örneği alanını bellekte belirli bir konuma sabitsabitler.</span><span class="sxs-lookup"><span data-stu-id="d5334-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="d5334-118">128 öğesi `char` dizi boyutu 256 bayttır.</span><span class="sxs-lookup"><span data-stu-id="d5334-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="d5334-119">Sabit boyutlu [char](../../language-reference/builtin-types/char.md) arabellekleri, kodlamadan bağımsız olarak her zaman karakter başına iki bayt alır.</span><span class="sxs-lookup"><span data-stu-id="d5334-119">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="d5334-120">Bu, karakter arabellekleri API yöntemlerine veya `CharSet = CharSet.Auto` ya da `CharSet = CharSet.Ansi`yapılar halinde Sıralansa bile geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d5334-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="d5334-121">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="d5334-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="d5334-122">Yukarıdaki örnekte, 7,3 ile C# başlayarak kullanılabilir olan sabitleme olmadan `fixed` alanlarına erişim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d5334-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="d5334-123">Diğer bir yaygın sabit boyutlu dizi [bool](../../language-reference/builtin-types/bool.md) dizidir.</span><span class="sxs-lookup"><span data-stu-id="d5334-123">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="d5334-124">Bir `bool` dizisindeki öğeler her zaman boyuttaki bir bayttır.</span><span class="sxs-lookup"><span data-stu-id="d5334-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="d5334-125">`bool` diziler, bit dizileri veya arabellekleri oluşturmak için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="d5334-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="d5334-126">[Stackalloc](../../language-reference/operators/stackalloc.md)kullanılarak oluşturulan bellek dışında, C# derleyici ve ortak DIL çalışma zamanı (CLR) herhangi bir güvenlik arabelleği taşma denetimi gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="d5334-126">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="d5334-127">Tüm güvenli olmayan kodlarda olduğu gibi dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="d5334-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="d5334-128">Güvenli olmayan arabellekler aşağıdaki yollarla normal dizilerden farklıdır:</span><span class="sxs-lookup"><span data-stu-id="d5334-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="d5334-129">Güvenli olmayan arabellekleri yalnızca güvenli olmayan bir bağlamda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5334-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="d5334-130">Güvenli olmayan arabellekler her zaman vektörlerdir veya tek boyutlu dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="d5334-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="d5334-131">Dizi bildirimi, `char id[8]`gibi bir sayı içermelidir.</span><span class="sxs-lookup"><span data-stu-id="d5334-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="d5334-132">`char id[]`kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d5334-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="d5334-133">Güvenli olmayan arabellekler yalnızca güvenli olmayan bağlamdaki yapıların örnek alanları olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5334-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="d5334-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5334-134">See also</span></span>

- [<span data-ttu-id="d5334-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d5334-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d5334-136">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="d5334-136">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="d5334-137">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="d5334-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="d5334-138">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="d5334-138">Interoperability</span></span>](../interop/index.md)
