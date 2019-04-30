---
title: 'Nasıl yapılır: - değişkenin adresini edinme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: b12d3bf99f32a3526bd4a1ec8c49b1fd88afd68a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61708802"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="2283c-102">Nasıl yapılır: değişkenin adresini edinme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2283c-102">How to: obtain the address of a variable (C# Programming Guide)</span></span>

<span data-ttu-id="2283c-103">Sabit bir değişkene değerlendirir, tekli ifade adresini almak için address-of işlecini kullanın `&`:</span><span class="sxs-lookup"><span data-stu-id="2283c-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator `&`:</span></span>  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="2283c-104">Address-of işleci yalnızca bir değişkene uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="2283c-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="2283c-105">Değişken taşınabilir bir değişken ise kullanabileceğiniz [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) adresini almadan önce değişkeni geçici olarak çözmek için.</span><span class="sxs-lookup"><span data-stu-id="2283c-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span> <span data-ttu-id="2283c-106">Taşınabilir değişkenleri hakkında daha fazla bilgi için bkz. [sabit ve taşınabilir değişkenleri](/dotnet/csharp/language-reference/language-specification/unsafe-code#fixed-and-moveable-variables).</span><span class="sxs-lookup"><span data-stu-id="2283c-106">For more information about moveable variables, see [Fixed and moveable variables](/dotnet/csharp/language-reference/language-specification/unsafe-code#fixed-and-moveable-variables).</span></span> 
  
 <span data-ttu-id="2283c-107">Bu değişkeni başlatıldığından emin olmak sizin sorumluluğunuzdur.</span><span class="sxs-lookup"><span data-stu-id="2283c-107">It's your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="2283c-108">Değişken başlatılmadı, derleyici bir hata iletisi sorunu değildir.</span><span class="sxs-lookup"><span data-stu-id="2283c-108">The compiler doesn't issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="2283c-109">Bir sabit bir değer veya adresi alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="2283c-109">You can't get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2283c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="2283c-110">Example</span></span>  
 <span data-ttu-id="2283c-111">Bu örnekte, bir işaretçi `int`, `p`, bildirilmiş ve bir tamsayı değişkeninin adresi atanan `number`.</span><span class="sxs-lookup"><span data-stu-id="2283c-111">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="2283c-112">Değişken `number` atamaya sonucu olarak başlatılır `*p`.</span><span class="sxs-lookup"><span data-stu-id="2283c-112">The variable `number` is initialized as a result of the assignment to `*p`.</span></span> <span data-ttu-id="2283c-113">Bu atama deyimi, değişkenin başlatılması yorum `number` kaldırılır, ancak hiçbir derleme zamanı hata verilir.</span><span class="sxs-lookup"><span data-stu-id="2283c-113">If you comment out this assignment statement, the initialization of the variable `number` is removed, but no compile-time error is issued.</span></span>  

> [!NOTE]
> <span data-ttu-id="2283c-114">Bu örneği derlemek [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="2283c-114">Compile this example with the [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="2283c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2283c-115">See also</span></span>

- [<span data-ttu-id="2283c-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2283c-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2283c-117">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="2283c-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="2283c-118">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="2283c-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="2283c-119">Türler</span><span class="sxs-lookup"><span data-stu-id="2283c-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="2283c-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="2283c-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="2283c-121">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="2283c-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="2283c-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="2283c-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
