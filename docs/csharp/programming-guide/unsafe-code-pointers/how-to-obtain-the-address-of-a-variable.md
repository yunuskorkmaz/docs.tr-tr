---
title: "Nasıl yapılır: Değişkenin Adresini Edinme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="5a362-102">Nasıl yapılır: Değişkenin Adresini Edinme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5a362-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="5a362-103">Sabit bir değişkene değerlendiren bir tek terimli ifadesi adresini elde etmek için address-of işleci kullanın:</span><span class="sxs-lookup"><span data-stu-id="5a362-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator:</span></span>  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="5a362-104">Address-of işleci yalnızca bir değişkene uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5a362-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="5a362-105">Değişken taşınabilir değişkeni ise kullanabileceğiniz [deyimi sabit](../../../csharp/language-reference/keywords/fixed-statement.md) değişkeni adresini almadan önce geçici olarak çözmek için.</span><span class="sxs-lookup"><span data-stu-id="5a362-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="5a362-106">Bu değişkeni başlatıldığından emin olun, sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="5a362-106">It is your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="5a362-107">Değişkeni başlatılmadı, derleyici bir hata iletisi veremez.</span><span class="sxs-lookup"><span data-stu-id="5a362-107">The compiler will not issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="5a362-108">Bir sabit ya da bir değer adresini alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="5a362-108">You cannot get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a362-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a362-109">Example</span></span>  
 <span data-ttu-id="5a362-110">Bu örnekte, bir işaretçi `int`, `p`, bildirilmiş ve bir tamsayı değişken adresi atanmış `number`.</span><span class="sxs-lookup"><span data-stu-id="5a362-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="5a362-111">Değişkeni `number` atamayı sonucunda başlatılmış * p.</span><span class="sxs-lookup"><span data-stu-id="5a362-111">The variable `number` is initialized as a result of the assignment to *p.</span></span> <span data-ttu-id="5a362-112">Bu atama deyimi bir yorum, değişkeni başlatma yaptığınız varsa `number` kaldırılacak, ancak hiçbir derleme zamanı hatası verilir.</span><span class="sxs-lookup"><span data-stu-id="5a362-112">If you make this assignment statement a comment, the initialization of the variable `number` will be removed, but no compile-time error is issued.</span></span> <span data-ttu-id="5a362-113">Kullanımına dikkat edin [üye erişimi](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) işleci `->` elde edilir ve işaretçiyi depolanan adresini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5a362-113">Notice the use of the [Member Access](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operator `->` to obtain and display the address stored in the pointer.</span></span>  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5a362-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a362-114">See Also</span></span>  
 [<span data-ttu-id="5a362-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5a362-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5a362-116">İşaretçi ifadeleri</span><span class="sxs-lookup"><span data-stu-id="5a362-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="5a362-117">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="5a362-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="5a362-118">Türler</span><span class="sxs-lookup"><span data-stu-id="5a362-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="5a362-119">güvenli olmayan</span><span class="sxs-lookup"><span data-stu-id="5a362-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="5a362-120">fixed deyimi</span><span class="sxs-lookup"><span data-stu-id="5a362-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="5a362-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="5a362-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
