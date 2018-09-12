---
title: unsafe (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: b4615021a4fc3391ac0ae703b6c97301b44aa60e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508406"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="9d630-102">unsafe (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9d630-102">unsafe (C# Reference)</span></span>
<span data-ttu-id="9d630-103">`unsafe` Anahtar sözcüğü, işaretçileri içeren tüm işlemler için gerekli olan güvensiz bir bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d630-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="9d630-104">Daha fazla bilgi için [güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="9d630-104">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="9d630-105">Kullanabileceğiniz `unsafe` bildirimi bir tür veya üye değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="9d630-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="9d630-106">Türe veya üyeye tüm metinsel kapsamını, bu nedenle güvenli olmayan bir bağlam kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="9d630-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="9d630-107">Örneğin, aşağıdaki ile bildirilen bir yöntemi olan `unsafe` değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="9d630-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>  
  
```csharp  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="9d630-108">İşaretçiler, parametre listesinde kullanılabilmesi için güvenli olmayan bir bağlam kapsamını parametre listesinden, yöntemin sonuna kadar genişletir:</span><span class="sxs-lookup"><span data-stu-id="9d630-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>  
  
```csharp  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 <span data-ttu-id="9d630-109">Güvenli olmayan bir blok, bu blok içinde bir güvenli olmayan kod kullanımını etkinleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d630-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="9d630-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9d630-110">For example:</span></span>  
  
```csharp  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="9d630-111">Güvenli olmayan kod olarak derlemek için belirtmelisiniz [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9d630-111">To compile unsafe code, you must specify the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="9d630-112">Güvenli olmayan kod ortak dil çalışma zamanı tarafından doğrulanabilir değil.</span><span class="sxs-lookup"><span data-stu-id="9d630-112">Unsafe code is not verifiable by the common language runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d630-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d630-113">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9d630-114">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9d630-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9d630-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d630-115">See Also</span></span>

- [<span data-ttu-id="9d630-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9d630-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9d630-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9d630-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9d630-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9d630-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="9d630-119">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="9d630-119">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="9d630-120">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="9d630-120">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="9d630-121">Sabit Boyutlu Arabellekler</span><span class="sxs-lookup"><span data-stu-id="9d630-121">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
