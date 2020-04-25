---
title: Sabit boyutlu arabellekler-C# Programlama Kılavuzu
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 5920dd125ded34969d60feb299568b56402056ab
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140553"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="25350-102">Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="25350-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="25350-103">C# ' de, bir veri yapısında sabit boyutlu bir diziye sahip bir arabellek oluşturmak için [fixed](../../language-reference/keywords/fixed-statement.md) ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25350-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="25350-104">Sabit boyutlu arabellekler, diğer dillerdeki veya platformlardaki veri kaynaklarıyla birlikte bulunan Yöntemler yazdığınızda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="25350-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="25350-105">Sabit dizi, normal yapı üyeleri için izin verilen herhangi bir özniteliği veya değiştiricilerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="25350-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="25350-106">Tek kısıtlama `bool`, dizi türünün, `byte` `char` `short` `int` `long` `sbyte` `uint` `ulong` `float` `double`,,,,,,,,,, veya olması olabilir. `ushort`</span><span class="sxs-lookup"><span data-stu-id="25350-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="25350-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25350-107">Remarks</span></span>

<span data-ttu-id="25350-108">Güvenli kodda, bir dizi içeren bir C# yapısı dizi öğelerini içermez.</span><span class="sxs-lookup"><span data-stu-id="25350-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="25350-109">Bunun yerine, yapı öğelerine bir başvuru içerir.</span><span class="sxs-lookup"><span data-stu-id="25350-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="25350-110">[Güvenli olmayan](../../language-reference/keywords/unsafe.md) bir kod bloğunda kullanıldığında bir [yapıda](../../language-reference/builtin-types/struct.md) sabit boyutlu bir dizi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25350-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="25350-111">Aşağıdaki `struct` boyut, başvuru `pathName` olduğundan dizideki öğelerin sayısına bağlı değildir:</span><span class="sxs-lookup"><span data-stu-id="25350-111">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="25350-112">`struct` , Güvenli olmayan kodda gömülü bir dizi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="25350-112">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="25350-113">Aşağıdaki örnekte, `fixedBuffer` dizisinin sabit bir boyutu vardır.</span><span class="sxs-lookup"><span data-stu-id="25350-113">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="25350-114">İlk öğe için `fixed` bir işaretçi oluşturmak üzere bir ifade kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="25350-114">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="25350-115">Bu işaretçi aracılığıyla dizinin öğelerine erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25350-115">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="25350-116">`fixed` İfade, `fixedBuffer` örnek alanını bellekte belirli bir konuma sabitsabitler.</span><span class="sxs-lookup"><span data-stu-id="25350-116">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="25350-117">128 öğe `char` dizisinin boyutu 256 bayttır.</span><span class="sxs-lookup"><span data-stu-id="25350-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="25350-118">Sabit boyutlu [char](../../language-reference/builtin-types/char.md) arabellekleri, kodlamadan bağımsız olarak her zaman karakter başına iki bayt alır.</span><span class="sxs-lookup"><span data-stu-id="25350-118">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="25350-119">Bu, karakter arabellekleri API yöntemlerine veya `CharSet = CharSet.Auto` ya da `CharSet = CharSet.Ansi`yapıları için Sıralansa bile geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="25350-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="25350-120">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="25350-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="25350-121">Yukarıdaki örnekte, C# 7,3 `fixed` ile başlayarak kullanılabilir olan sabitleme olmadan alanlara erişme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25350-121">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="25350-122">Diğer bir yaygın sabit boyutlu dizi [bool](../../language-reference/builtin-types/bool.md) dizidir.</span><span class="sxs-lookup"><span data-stu-id="25350-122">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="25350-123">Bir `bool` dizideki öğeler her zaman boyuttaki bir bayttır.</span><span class="sxs-lookup"><span data-stu-id="25350-123">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="25350-124">`bool`diziler, bit dizileri veya arabellekleri oluşturmak için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="25350-124">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

<span data-ttu-id="25350-125">Sabit boyutlu arabellekler ile <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>derlenir ve bu, ortak dil çalışma zamanına (CLR) bir türün, bulunabilecek bir yönetilmeyen dizi içerdiğini söyler.</span><span class="sxs-lookup"><span data-stu-id="25350-125">Fixed size buffers are compiled with the <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, which instructs the common language runtime (CLR) that a type contains an unmanaged array that can potentially overflow.</span></span> <span data-ttu-id="25350-126">Bu, CLR 'de arabellek taşması algılama özelliklerini otomatik olarak sağlayan [stackalloc](../../language-reference/operators/stackalloc.md)kullanılarak oluşturulan belleğe benzerdir.</span><span class="sxs-lookup"><span data-stu-id="25350-126">This is similar to memory created using [stackalloc](../../language-reference/operators/stackalloc.md), which automatically enables buffer overrun detection features in the CLR.</span></span> <span data-ttu-id="25350-127">Önceki örnekte, bir sabit boyut arabelleğinin bir `unsafe struct`içinde nasıl yer aldığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="25350-127">The previous example shows how a fixed size buffer could exist in an `unsafe struct`.</span></span>

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

<span data-ttu-id="25350-128">Için `Buffer`C# tarafından oluşturulan derleyici, aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="25350-128">The compiler generated C# for `Buffer`, is attributed as follows:</span></span>

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

<span data-ttu-id="25350-129">Sabit boyutlu arabellekler aşağıdaki yollarla normal dizilerden farklıdır:</span><span class="sxs-lookup"><span data-stu-id="25350-129">Fixed size buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="25350-130">Yalnızca [güvenli olmayan](../../language-reference/keywords/unsafe.md) bir bağlamda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25350-130">May only be used in an [unsafe](../../language-reference/keywords/unsafe.md) context.</span></span>
- <span data-ttu-id="25350-131">Yalnızca yapıların örnek alanları olabilir.</span><span class="sxs-lookup"><span data-stu-id="25350-131">May only be instance fields of structs.</span></span>
- <span data-ttu-id="25350-132">Bunlar her zaman vektörleridir veya tek boyutlu dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="25350-132">They're always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="25350-133">Bildirimin uzunluğu içermesi gerekir, örneğin `fixed char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="25350-133">The declaration should include the length, such as `fixed char id[8]`.</span></span> <span data-ttu-id="25350-134">Kullanamazsınız `fixed char id[]`.</span><span class="sxs-lookup"><span data-stu-id="25350-134">You cannot use `fixed char id[]`.</span></span>

## <a name="see-also"></a><span data-ttu-id="25350-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25350-135">See also</span></span>

- [<span data-ttu-id="25350-136">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="25350-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="25350-137">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="25350-137">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="25350-138">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="25350-138">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="25350-139">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="25350-139">Interoperability</span></span>](../interop/index.md)
