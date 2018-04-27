---
title: 'Nasıl yapılır: Değişkenin Adresini Edinme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 63a49490effb8b7d365492e8518b7558ec03a705
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="4f152-102">Nasıl yapılır: Değişkenin Adresini Edinme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4f152-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="4f152-103">Address-of işleci sabit bir değişkene değerlendiren bir tek terimli ifadesi adresini elde etmek için kullanmak `&`:</span><span class="sxs-lookup"><span data-stu-id="4f152-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator `&`:</span></span>  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="4f152-104">Address-of işleci yalnızca bir değişkene uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="4f152-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="4f152-105">Değişken taşınabilir değişkeni ise kullanabileceğiniz [deyimi sabit](../../../csharp/language-reference/keywords/fixed-statement.md) değişkeni adresini almadan önce geçici olarak çözmek için.</span><span class="sxs-lookup"><span data-stu-id="4f152-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="4f152-106">Bu değişkeni başlatıldığından emin olun, sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="4f152-106">It's your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="4f152-107">Derleyici bir hata iletisi verilmediğine ve değişken başlatılmadı değil.</span><span class="sxs-lookup"><span data-stu-id="4f152-107">The compiler doesn't issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="4f152-108">Bir sabit ya da bir değer adresini alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="4f152-108">You can't get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f152-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f152-109">Example</span></span>  
 <span data-ttu-id="4f152-110">Bu örnekte, bir işaretçi `int`, `p`, bildirilmiş ve bir tamsayı değişken adresi atanmış `number`.</span><span class="sxs-lookup"><span data-stu-id="4f152-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="4f152-111">Değişkeni `number` atamayı sonucunda başlatılmış `*p`.</span><span class="sxs-lookup"><span data-stu-id="4f152-111">The variable `number` is initialized as a result of the assignment to `*p`.</span></span> <span data-ttu-id="4f152-112">Bu atama deyimi değişkeni başlatma açıklama varsa `number` kaldırılır, ancak hiçbir derleme zamanı hatası verilir.</span><span class="sxs-lookup"><span data-stu-id="4f152-112">If you comment out this assignment statement, the initialization of the variable `number` is removed, but no compile-time error is issued.</span></span>  

> [!NOTE]
> <span data-ttu-id="4f152-113">Bu örneği derlemek [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4f152-113">Compile this example with the [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="4f152-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f152-114">See Also</span></span>  
 [<span data-ttu-id="4f152-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4f152-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4f152-116">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="4f152-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="4f152-117">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="4f152-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="4f152-118">Türler</span><span class="sxs-lookup"><span data-stu-id="4f152-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="4f152-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="4f152-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="4f152-120">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f152-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="4f152-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="4f152-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
