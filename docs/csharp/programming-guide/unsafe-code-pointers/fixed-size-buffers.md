---
title: Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 310c5eed5507f75239efc78b6132fbc91211d29e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339598"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="231e1-102">Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="231e1-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="231e1-103">C# ' ta kullanabileceğiniz [sabit](../../language-reference/keywords/fixed-statement.md) ifadesi bir veri yapısında bir sabit boyutlu bir diziye sahip bir arabellek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="231e1-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="231e1-104">Bu veri kaynakları birlikte çalışma yöntemlerini diğer diller veya platformları yazdığınızda, sabit boyutlu arabellekler yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="231e1-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="231e1-105">Sabit dizi öznitelik ya da normal Yapı üyeleri için izin verilen değiştiricileri alabilir.</span><span class="sxs-lookup"><span data-stu-id="231e1-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="231e1-106">Yalnızca dizi türü olmalıdır kısıtlamadır `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, veya `double`.</span><span class="sxs-lookup"><span data-stu-id="231e1-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="231e1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="231e1-107">Remarks</span></span>

<span data-ttu-id="231e1-108">Güvenli kodda bir dizi içeren bir C# yapı dizi öğeleri içermiyor.</span><span class="sxs-lookup"><span data-stu-id="231e1-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="231e1-109">Bunun yerine, yapı öğeleri bir başvuru içeriyor.</span><span class="sxs-lookup"><span data-stu-id="231e1-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="231e1-110">İçinde sabit boyutlu bir dizi eklenebilir bir [yapısı](../../language-reference/keywords/struct.md) içinde kullanıldığında bir [güvensiz](../../language-reference/keywords/unsafe.md) kod bloğu.</span><span class="sxs-lookup"><span data-stu-id="231e1-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="231e1-111">Aşağıdaki `struct` boyutu 8 bayt'tır.</span><span class="sxs-lookup"><span data-stu-id="231e1-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="231e1-112">`pathName` Dizidir başvuru:</span><span class="sxs-lookup"><span data-stu-id="231e1-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="231e1-113">A `struct` güvenli olmayan kod katıştırılmış bir dizide içerebilir.</span><span class="sxs-lookup"><span data-stu-id="231e1-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="231e1-114">Aşağıdaki örnekte, `fixedBuffer` dizi sabit bir boyuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="231e1-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="231e1-115">Kullandığınız bir `fixed` deyimi ilk öğe için bir işaretçi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="231e1-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="231e1-116">Dizideki öğeler bu işaretçinin erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="231e1-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="231e1-117">`fixed` Deyimi PIN'ler `fixedBuffer` bellekte belirli bir konuma örnek alanı.</span><span class="sxs-lookup"><span data-stu-id="231e1-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="231e1-118">128 öğe boyutunu `char` 256 baytı dizisidir.</span><span class="sxs-lookup"><span data-stu-id="231e1-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="231e1-119">Boyutu sabit [char](../../language-reference/keywords/char.md) arabellekleri her zaman karakter kodlama bağımsız olarak, her iki byte uygulamanız.</span><span class="sxs-lookup"><span data-stu-id="231e1-119">Fixed size [char](../../language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="231e1-120">Bu bile zaman char arabellekleri API yöntemlerini veya yapılar ile sıralanmış geçerlidir `CharSet = CharSet.Auto` veya `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="231e1-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="231e1-121">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="231e1-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="231e1-122">Önceki örnekte erişme gösterir `fixed` C# ile 7.3 itibaren kullanılabilir sabitleme, olmadan alanları...</span><span class="sxs-lookup"><span data-stu-id="231e1-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3..</span></span>

<span data-ttu-id="231e1-123">Başka bir ortak sabit boyutlu dizi [bool](../../language-reference/keywords/bool.md) dizi.</span><span class="sxs-lookup"><span data-stu-id="231e1-123">Another common fixed-size array is the [bool](../../language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="231e1-124">Öğeleri bir `bool` dizi her zaman bir bayt boyutunda.</span><span class="sxs-lookup"><span data-stu-id="231e1-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="231e1-125">`bool` diziler bit dizileri veya arabelleklerinin oluşturmak için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="231e1-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="231e1-126">Kullanılarak oluşturulan bellek dışında [stackalloc](../../language-reference/keywords/stackalloc.md), C# Derleyici ve ortak dil çalışma zamanı (CLR) tüm güvenlik arabellek taşması denetimlerini gerçekleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="231e1-126">Except for memory created by using [stackalloc](../../language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="231e1-127">Tüm güvenli olmayan kod ile dikkatli olarak.</span><span class="sxs-lookup"><span data-stu-id="231e1-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="231e1-128">Güvenli olmayan arabellekler normal diziler de aşağıdaki yollarla farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="231e1-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="231e1-129">Bu gibi durumlarda, güvenli olmayan arabellekler yalnızca güvensiz bir bağlamda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="231e1-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="231e1-130">Güvenli olmayan arabellekler her zaman vektörlerinin ya da tek boyutlu diziler olur.</span><span class="sxs-lookup"><span data-stu-id="231e1-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="231e1-131">Dizi bildirimi gibi bir sayı bulunması `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="231e1-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="231e1-132">Kullanamazsınız `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="231e1-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="231e1-133">Güvenli olmayan arabellekler yalnızca güvenli olmayan bir bağlamda yapılar örneği alanları olabilir.</span><span class="sxs-lookup"><span data-stu-id="231e1-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="231e1-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="231e1-134">See Also</span></span>

[<span data-ttu-id="231e1-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="231e1-135">C# Programming Guide</span></span>](../index.md)  
[<span data-ttu-id="231e1-136">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="231e1-136">Unsafe Code and Pointers</span></span>](index.md)  
[<span data-ttu-id="231e1-137">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="231e1-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)  
[<span data-ttu-id="231e1-138">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="231e1-138">Interoperability</span></span>](../interop/index.md)
