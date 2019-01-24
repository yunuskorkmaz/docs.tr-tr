---
title: 'Nasıl yapılır: - değişkenin adresini edinme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: cba33803c31ccc144479ad3e7b073ea7057495d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490564"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="b660f-102">Nasıl yapılır: değişkenin adresini edinme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b660f-102">How to: obtain the address of a variable (C# Programming Guide)</span></span>

<span data-ttu-id="b660f-103">Sabit bir değişkene değerlendirir, tekli ifade adresini almak için address-of işlecini kullanın `&`:</span><span class="sxs-lookup"><span data-stu-id="b660f-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator `&`:</span></span>  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="b660f-104">Address-of işleci yalnızca bir değişkene uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="b660f-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="b660f-105">Değişken taşınabilir bir değişken ise kullanabileceğiniz [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) adresini almadan önce değişkeni geçici olarak çözmek için.</span><span class="sxs-lookup"><span data-stu-id="b660f-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="b660f-106">Bu değişkeni başlatıldığından emin olmak sizin sorumluluğunuzdur.</span><span class="sxs-lookup"><span data-stu-id="b660f-106">It's your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="b660f-107">Değişken başlatılmadı, derleyici bir hata iletisi sorunu değildir.</span><span class="sxs-lookup"><span data-stu-id="b660f-107">The compiler doesn't issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="b660f-108">Bir sabit bir değer veya adresi alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="b660f-108">You can't get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b660f-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b660f-109">Example</span></span>  
 <span data-ttu-id="b660f-110">Bu örnekte, bir işaretçi `int`, `p`, bildirilmiş ve bir tamsayı değişkeninin adresi atanan `number`.</span><span class="sxs-lookup"><span data-stu-id="b660f-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="b660f-111">Değişken `number` atamaya sonucu olarak başlatılır `*p`.</span><span class="sxs-lookup"><span data-stu-id="b660f-111">The variable `number` is initialized as a result of the assignment to `*p`.</span></span> <span data-ttu-id="b660f-112">Bu atama deyimi, değişkenin başlatılması yorum `number` kaldırılır, ancak hiçbir derleme zamanı hata verilir.</span><span class="sxs-lookup"><span data-stu-id="b660f-112">If you comment out this assignment statement, the initialization of the variable `number` is removed, but no compile-time error is issued.</span></span>  

> [!NOTE]
> <span data-ttu-id="b660f-113">Bu örneği derlemek [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b660f-113">Compile this example with the [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="b660f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b660f-114">See also</span></span>

- [<span data-ttu-id="b660f-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b660f-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b660f-116">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="b660f-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="b660f-117">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="b660f-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="b660f-118">Türler</span><span class="sxs-lookup"><span data-stu-id="b660f-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="b660f-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="b660f-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="b660f-120">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="b660f-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="b660f-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="b660f-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
