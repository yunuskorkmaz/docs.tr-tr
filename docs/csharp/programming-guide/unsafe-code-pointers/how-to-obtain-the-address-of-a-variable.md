---
title: 'Nasıl yapılır: Değişkenin Adresini Edinme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: bb52aee3341194697b40b30ec14afced61a200be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340131"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="5f2fc-102">Nasıl yapılır: Değişkenin Adresini Edinme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5f2fc-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="5f2fc-103">Address-of işleci sabit bir değişkene değerlendiren bir tek terimli ifadesi adresini elde etmek için kullanmak `&`:</span><span class="sxs-lookup"><span data-stu-id="5f2fc-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator `&`:</span></span>  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="5f2fc-104">Address-of işleci yalnızca bir değişkene uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="5f2fc-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="5f2fc-105">Değişken taşınabilir değişkeni ise kullanabileceğiniz [deyimi sabit](../../../csharp/language-reference/keywords/fixed-statement.md) değişkeni adresini almadan önce geçici olarak çözmek için.</span><span class="sxs-lookup"><span data-stu-id="5f2fc-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="5f2fc-106">Bu değişkeni başlatıldığından emin olun, sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="5f2fc-106">It's your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="5f2fc-107">Derleyici bir hata iletisi verilmediğine ve değişken başlatılmadı değil.</span><span class="sxs-lookup"><span data-stu-id="5f2fc-107">The compiler doesn't issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="5f2fc-108">Bir sabit ya da bir değer adresini alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="5f2fc-108">You can't get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f2fc-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f2fc-109">Example</span></span>  
 <span data-ttu-id="5f2fc-110">Bu örnekte, bir işaretçi `int`, `p`, bildirilmiş ve bir tamsayı değişken adresi atanmış `number`.</span><span class="sxs-lookup"><span data-stu-id="5f2fc-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="5f2fc-111">Değişkeni `number` atamayı sonucunda başlatılmış `*p`.</span><span class="sxs-lookup"><span data-stu-id="5f2fc-111">The variable `number` is initialized as a result of the assignment to `*p`.</span></span> <span data-ttu-id="5f2fc-112">Bu atama deyimi değişkeni başlatma açıklama varsa `number` kaldırılır, ancak hiçbir derleme zamanı hatası verilir.</span><span class="sxs-lookup"><span data-stu-id="5f2fc-112">If you comment out this assignment statement, the initialization of the variable `number` is removed, but no compile-time error is issued.</span></span>  

> [!NOTE]
> <span data-ttu-id="5f2fc-113">Bu örneği derlemek [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5f2fc-113">Compile this example with the [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="5f2fc-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f2fc-114">See Also</span></span>  
 [<span data-ttu-id="5f2fc-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5f2fc-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5f2fc-116">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="5f2fc-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="5f2fc-117">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="5f2fc-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="5f2fc-118">Türler</span><span class="sxs-lookup"><span data-stu-id="5f2fc-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="5f2fc-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="5f2fc-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="5f2fc-120">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="5f2fc-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="5f2fc-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="5f2fc-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
