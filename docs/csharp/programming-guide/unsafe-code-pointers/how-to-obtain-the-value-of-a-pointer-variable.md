---
title: 'Nasıl yapılır: İşaretçi Değişkeninin Değerini Edinme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: c53026149837681235c6d1001707a25b9c8b40b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322958"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="a8054-102">Nasıl yapılır: İşaretçi Değişkeninin Değerini Edinme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a8054-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="a8054-103">İşaretçi indirection işleci değişkeni için bir işaretçi işaret konumda almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8054-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="a8054-104">Şu biçimi ifade alır nerede `p` bir işaretçi türü:</span><span class="sxs-lookup"><span data-stu-id="a8054-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="a8054-105">İşaretçi türünün dışında herhangi bir türde bir ifade birli indirection işleci kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a8054-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="a8054-106">Ayrıca, kendisine uygulanamıyor bir [void](../../../csharp/language-reference/keywords/void.md) işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a8054-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="a8054-107">İndirection işleci uyguladığınızda bir [null](../../../csharp/language-reference/keywords/null.md) işaretçisi sonucu uygulamasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a8054-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8054-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8054-108">Example</span></span>  
 <span data-ttu-id="a8054-109">Aşağıdaki örnekte, türünde bir değişken `char` farklı türlerde işaretçileri kullanılarak erişilir.</span><span class="sxs-lookup"><span data-stu-id="a8054-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="a8054-110">Unutmayın adresi `theChar` bir değişkene ayrılan fiziksel adresi değişebildiğinden gelen çalıştırma için Çalıştır ' farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8054-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 <span data-ttu-id="a8054-111">**TheChar değerini Z =**</span><span class="sxs-lookup"><span data-stu-id="a8054-111">**Value of theChar = Z**</span></span>  
<span data-ttu-id="a8054-112">**TheChar adresini 12F718 =**</span><span class="sxs-lookup"><span data-stu-id="a8054-112">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="a8054-113">**PChar değerini Z =** </span><span class="sxs-lookup"><span data-stu-id="a8054-113">**Value of pChar = Z** </span></span>  
<span data-ttu-id="a8054-114">**PInt değerini 90 =**</span><span class="sxs-lookup"><span data-stu-id="a8054-114">**Value of pInt = 90**</span></span>    
## <a name="see-also"></a><span data-ttu-id="a8054-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8054-115">See Also</span></span>  
 [<span data-ttu-id="a8054-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a8054-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a8054-117">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="a8054-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="a8054-118">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="a8054-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="a8054-119">Türler</span><span class="sxs-lookup"><span data-stu-id="a8054-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="a8054-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="a8054-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="a8054-121">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="a8054-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="a8054-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="a8054-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
