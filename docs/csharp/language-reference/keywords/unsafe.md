---
title: "unsafe (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords: unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fffbe36e39d279b2364b178188381a403c8ff86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="46fd9-102">unsafe (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="46fd9-102">unsafe (C# Reference)</span></span>
<span data-ttu-id="46fd9-103">`unsafe` Anahtar sözcüğü işaretçileri içeren herhangi bir işlem için gereken bir güvenli bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="46fd9-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="46fd9-104">Daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="46fd9-104">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="46fd9-105">Kullanabileceğiniz `unsafe` bir tür ya da bir üye bildiriminde değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="46fd9-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="46fd9-106">Bu nedenle tür veya üye tüm metinsel kapsamını güvenli olmayan içerik olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="46fd9-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="46fd9-107">Örneğin, aşağıdaki ile bildirilen bir yöntemdir `unsafe` değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="46fd9-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>  
  
```  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="46fd9-108">İşaretçileri parametre listesinde de kullanılabilmesi için güvenli olmayan içerik kapsamını parametre listeden yönteminin sonuna genişletir:</span><span class="sxs-lookup"><span data-stu-id="46fd9-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>  
  
```  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 <span data-ttu-id="46fd9-109">Güvenli olmayan bir blok, bir güvenli olmayan kod bu bloktaki kullanımını etkinleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46fd9-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="46fd9-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="46fd9-110">For example:</span></span>  
  
```  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="46fd9-111">Güvenli olmayan kod derlemek için belirtmeniz gerekir [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="46fd9-111">To compile unsafe code, you must specify the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="46fd9-112">Güvenli olmayan kod ortak dil çalışma zamanı tarafından doğrulanabilen değil.</span><span class="sxs-lookup"><span data-stu-id="46fd9-112">Unsafe code is not verifiable by the common language runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46fd9-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="46fd9-113">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="46fd9-114">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="46fd9-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="46fd9-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46fd9-115">See Also</span></span>  
 [<span data-ttu-id="46fd9-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="46fd9-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="46fd9-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="46fd9-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="46fd9-118">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="46fd9-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="46fd9-119">fixed deyimi</span><span class="sxs-lookup"><span data-stu-id="46fd9-119">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="46fd9-120">Güvenli olmayan kod ve işaretçiler</span><span class="sxs-lookup"><span data-stu-id="46fd9-120">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="46fd9-121">Sabit boyutlu arabellekler</span><span class="sxs-lookup"><span data-stu-id="46fd9-121">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
