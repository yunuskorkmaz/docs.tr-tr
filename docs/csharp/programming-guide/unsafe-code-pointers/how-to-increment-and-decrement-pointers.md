---
title: 'Nasıl yapılır: İşaretçileri Artırma ve Azaltma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: 39cefc5dcebf1331a5e0ac0fadb8284e9041eb27
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138246"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="2b9af-102">Nasıl yapılır: İşaretçileri Artırma ve Azaltma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2b9af-102">How to: Increment and Decrement Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="2b9af-103">Artırma ve azaltma işleçleri kullanan `++` ve `--`işaretçi konuma göre değişmesini [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) işaretçi işaretçisi-türü \*.</span><span class="sxs-lookup"><span data-stu-id="2b9af-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) for a pointer of type pointer-type\*.</span></span> <span data-ttu-id="2b9af-104">Artırma ve azaltma ifadeleri aşağıdaki biçiminde:</span><span class="sxs-lookup"><span data-stu-id="2b9af-104">The increment and decrement expressions take the following form:</span></span>  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="2b9af-105">Tür dışında herhangi bir türde işaretçileri artırma ve azaltma işleçleri uygulanabilir `void*`.</span><span class="sxs-lookup"><span data-stu-id="2b9af-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="2b9af-106">Artırım işleci türünde bir işaretçiye uygulamak etkisini `pointer-type` eklemektir [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) adresine işaretçi değişkeninde yer alır.</span><span class="sxs-lookup"><span data-stu-id="2b9af-106">The effect of applying the increment operator to a pointer of the type `pointer-type` is to add [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="2b9af-107">Azaltma işleci türünde bir işaretçiye uygulamak etkisini `pointer-type` çıkarılacak olan `sizeof` (`pointer-type`) adresinden işaretçi değişkeninde yer alır.</span><span class="sxs-lookup"><span data-stu-id="2b9af-107">The effect of applying the decrement operator to a pointer of the type `pointer-type` is to subtract `sizeof` (`pointer-type`) from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="2b9af-108">Hiçbir özel durum, etki alanı işaretçinin işlemi taşıyor ve sonuç uygulamasının bağlıdır, üretilir.</span><span class="sxs-lookup"><span data-stu-id="2b9af-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b9af-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b9af-109">Example</span></span>  
 <span data-ttu-id="2b9af-110">Bu örnekte, bir dizi aracılığıyla işaretçinin boyutuna artırılarak adım `int`.</span><span class="sxs-lookup"><span data-stu-id="2b9af-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="2b9af-111">Her adımda adresi ve dizi öğenin içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2b9af-111">With each step, you display the address and the content of the array element.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
<span data-ttu-id="2b9af-112">**Değer: 0 @ adresi: 12860272**
**değer: 1 @ adresi: 12860276**
**değer: 2 @ adresi: 12860280**
**değer: 3 @ adresi : 12860284**
**değer: 4 @ adresi: 12860288**</span><span class="sxs-lookup"><span data-stu-id="2b9af-112">**Value:0 @ Address:12860272**
**Value:1 @ Address:12860276**
**Value:2 @ Address:12860280**
**Value:3 @ Address:12860284**
**Value:4 @ Address:12860288**</span></span>

## <a name="see-also"></a><span data-ttu-id="2b9af-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b9af-113">See Also</span></span>

- [<span data-ttu-id="2b9af-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2b9af-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2b9af-115">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="2b9af-115">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="2b9af-116">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="2b9af-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="2b9af-117">İşaretçileri İşleme</span><span class="sxs-lookup"><span data-stu-id="2b9af-117">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="2b9af-118">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="2b9af-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="2b9af-119">Türler</span><span class="sxs-lookup"><span data-stu-id="2b9af-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="2b9af-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="2b9af-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="2b9af-121">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b9af-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="2b9af-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="2b9af-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
