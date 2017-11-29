---
title: "Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3f99c2c6d477fca988fcca77de5ca5c2f8addd4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="c0e97-102">Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c0e97-102">Fixed Size Buffers (C# Programming Guide)</span></span>
<span data-ttu-id="c0e97-103">C# ' ta kullanabileceğiniz [sabit](../../../csharp/language-reference/keywords/fixed-statement.md) ifadesi bir veri yapısında bir sabit boyutlu bir diziye sahip bir arabellek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c0e97-103">In C#, you can use the [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="c0e97-104">Diğer diller önceden varolan DLL'leri veya COM projeleri yazılan kod gibi var olan kodu ile çalışırken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="c0e97-104">This is useful when you are working with existing code, such as code written in other languages, pre-existing DLLs or COM projects.</span></span> <span data-ttu-id="c0e97-105">Sabit dizi öznitelik ya da normal Yapı üyeleri için izin verilen değiştiricileri alabilir.</span><span class="sxs-lookup"><span data-stu-id="c0e97-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="c0e97-106">Yalnızca dizi türü olmalıdır kısıtlamadır `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, veya `double`.</span><span class="sxs-lookup"><span data-stu-id="c0e97-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a><span data-ttu-id="c0e97-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0e97-107">Remarks</span></span>  
 <span data-ttu-id="c0e97-108">Bir dizi içeren bir C# yapı dizi öğeleri içermediğinden erken sürümlerinde C#, C++ stili sabit boyutlu yapısı bildirme zordu.</span><span class="sxs-lookup"><span data-stu-id="c0e97-108">In early versions of C#, declaring a C++ style fixed-size structure was difficult because a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="c0e97-109">Bunun yerine, yapı öğeleri bir başvuru içeriyor.</span><span class="sxs-lookup"><span data-stu-id="c0e97-109">Instead, the struct contains a reference to the elements.</span></span>  
  
 <span data-ttu-id="c0e97-110">C# 2.0 içinde sabit boyutlu bir dizi ekleme yeteneği eklenen bir [yapısı](../../../csharp/language-reference/keywords/struct.md) içinde kullanıldığında bir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) kod bloğu.</span><span class="sxs-lookup"><span data-stu-id="c0e97-110">C# 2.0 added the ability to embed an array of fixed size in a [struct](../../../csharp/language-reference/keywords/struct.md) when it is used in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) code block.</span></span>  
  
 <span data-ttu-id="c0e97-111">Örneğin, C# 2.0, aşağıdaki önce `struct` 8 bayt boyutunda olabilir.</span><span class="sxs-lookup"><span data-stu-id="c0e97-111">For example, before C# 2.0, the following `struct` would be 8 bytes in size.</span></span> <span data-ttu-id="c0e97-112">`pathName` Dizidir yığında ayrılmış dizi başvurusu:</span><span class="sxs-lookup"><span data-stu-id="c0e97-112">The `pathName` array is a reference to the heap-allocated array:</span></span>  
  
 [!code-csharp[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 <span data-ttu-id="c0e97-113">C# 2.0 ile başlayan bir `struct` katıştırılmış bir dizi içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c0e97-113">Beginning with C# 2.0, a `struct` can contain an embedded array.</span></span> <span data-ttu-id="c0e97-114">Aşağıdaki örnekte, `fixedBuffer` dizi sabit bir boyuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c0e97-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="c0e97-115">Dizideki öğeler erişmek için kullandığınız bir `fixed` deyimi ilk öğe için bir işaretçi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c0e97-115">To access the elements of the array, you use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="c0e97-116">`fixed` Deyimi sabitler örneği `fixedBuffer` bellekte belirli bir konuma.</span><span class="sxs-lookup"><span data-stu-id="c0e97-116">The `fixed` statement pins an instance of `fixedBuffer` to a specific location in memory.</span></span>  
  
 [!code-csharp[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 <span data-ttu-id="c0e97-117">128 öğe boyutunu `char` 256 baytı dizisidir.</span><span class="sxs-lookup"><span data-stu-id="c0e97-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="c0e97-118">Boyutu sabit [char](../../../csharp/language-reference/keywords/char.md) arabellekleri her zaman karakter kodlama bağımsız olarak, her iki byte uygulamanız.</span><span class="sxs-lookup"><span data-stu-id="c0e97-118">Fixed size [char](../../../csharp/language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="c0e97-119">Bu bile zaman char arabellekleri API yöntemlerini veya yapılar ile sıralanmış geçerlidir `CharSet = CharSet.Auto` veya `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="c0e97-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="c0e97-120">Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="c0e97-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>  
  
 <span data-ttu-id="c0e97-121">Başka bir ortak sabit boyutlu dizi [bool](../../../csharp/language-reference/keywords/bool.md) dizi.</span><span class="sxs-lookup"><span data-stu-id="c0e97-121">Another common fixed-size array is the [bool](../../../csharp/language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="c0e97-122">Öğeleri bir `bool` dizi her zaman bir bayt boyutunda.</span><span class="sxs-lookup"><span data-stu-id="c0e97-122">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="c0e97-123">`bool`diziler bit dizileri veya arabelleklerinin oluşturmak için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="c0e97-123">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0e97-124">Kullanılarak oluşturulan bellek dışında [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), C# Derleyici ve ortak dil çalışma zamanı (CLR) tüm güvenlik arabellek taşması denetimlerini gerçekleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="c0e97-124">Except for memory created by using [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="c0e97-125">Tüm güvenli olmayan kod ile dikkatli olarak.</span><span class="sxs-lookup"><span data-stu-id="c0e97-125">As with all unsafe code, use caution.</span></span>  
  
 <span data-ttu-id="c0e97-126">Güvenli olmayan arabellekler normal diziler de aşağıdaki yollarla farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="c0e97-126">Unsafe buffers differ from regular arrays in the following ways:</span></span>  
  
-   <span data-ttu-id="c0e97-127">Bu gibi durumlarda, güvenli olmayan arabellekler yalnızca güvensiz bir bağlamda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0e97-127">You can only use unsafe buffers in an unsafe context.</span></span>  
  
-   <span data-ttu-id="c0e97-128">Güvenli olmayan arabellekler her zaman vektörlerinin ya da tek boyutlu diziler olur.</span><span class="sxs-lookup"><span data-stu-id="c0e97-128">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="c0e97-129">Dizi bildirimi gibi bir sayı bulunması `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="c0e97-129">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="c0e97-130">Kullanamazsınız `char id[]` yerine.</span><span class="sxs-lookup"><span data-stu-id="c0e97-130">You cannot use `char id[]` instead.</span></span>  
  
-   <span data-ttu-id="c0e97-131">Güvenli olmayan arabellekler yalnızca güvenli olmayan bir bağlamda yapılar örneği alanları olabilir.</span><span class="sxs-lookup"><span data-stu-id="c0e97-131">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e97-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0e97-132">See Also</span></span>  
 [<span data-ttu-id="c0e97-133">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c0e97-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c0e97-134">Güvenli olmayan kod ve işaretçiler</span><span class="sxs-lookup"><span data-stu-id="c0e97-134">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="c0e97-135">fixed deyimi</span><span class="sxs-lookup"><span data-stu-id="c0e97-135">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="c0e97-136">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="c0e97-136">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)
