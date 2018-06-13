---
title: 'Nasıl yapılır: İşaretçileri Artırma ve Azaltma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: e1c3ac12a126450781d0ce78e788f39c740b5279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324291"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="ae7cc-102">Nasıl yapılır: İşaretçileri Artırma ve Azaltma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ae7cc-102">How to: Increment and Decrement Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="ae7cc-103">Artırma ve azaltma işleçleri kullanmak `++` ve `--`, işaretçi konuma göre değiştirmek için [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) için bir işaretçi türü işaretçinin-türü \*.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) for a pointer of type pointer-type\*.</span></span> <span data-ttu-id="ae7cc-104">Artırma ve azaltma ifadeleri aşağıdaki biçimde alın:</span><span class="sxs-lookup"><span data-stu-id="ae7cc-104">The increment and decrement expressions take the following form:</span></span>  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="ae7cc-105">Türü dışında herhangi bir türde işaretçileri artırma ve azaltma işleçleri uygulanabilir `void*`.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="ae7cc-106">Artış işleci türü için bir işaretçi uygulama etkisini `pointer-type` eklemektir [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) işaretçi değişkeninde bulunan adresine.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-106">The effect of applying the increment operator to a pointer of the type `pointer-type` is to add [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="ae7cc-107">Uygulamanın etkisini azaltma işleci türü için bir işaretçi uygulama `pointer-type` çıkarmak için `sizeof` (`pointer-type`) işaretçi değişkeninde bulunan adresinden.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-107">The effect of applying the decrement operator to a pointer of the type `pointer-type` is to subtract `sizeof` (`pointer-type`) from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="ae7cc-108">Hiçbir özel durum, etki alanı işaretçinin işlemi taşar ve sonucu uygulamasına bağlıdır, üretilir.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae7cc-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae7cc-109">Example</span></span>  
 <span data-ttu-id="ae7cc-110">Bu örnekte, bir dizi boyunca boyutuyla işaretçinin artırılarak adım `int`.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="ae7cc-111">Her adım ile adres ve dizi öğenin içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-111">With each step, you display the address and the content of the array element.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
 <span data-ttu-id="ae7cc-112">**Değer: 0 @ adresi: 12860272**</span><span class="sxs-lookup"><span data-stu-id="ae7cc-112">**Value:0 @ Address:12860272**</span></span>  
<span data-ttu-id="ae7cc-113">**Değer: 1 @ adresi: 12860276**</span><span class="sxs-lookup"><span data-stu-id="ae7cc-113">**Value:1 @ Address:12860276**</span></span>  
<span data-ttu-id="ae7cc-114">**Değer: 2 @ adresi: 12860280**</span><span class="sxs-lookup"><span data-stu-id="ae7cc-114">**Value:2 @ Address:12860280**</span></span>  
<span data-ttu-id="ae7cc-115">**Değer: 3 @ adresi: 12860284**</span><span class="sxs-lookup"><span data-stu-id="ae7cc-115">**Value:3 @ Address:12860284**</span></span>  
<span data-ttu-id="ae7cc-116">**Değer: 4 @ adresi: 12860288**</span><span class="sxs-lookup"><span data-stu-id="ae7cc-116">**Value:4 @ Address:12860288**</span></span>   
## <a name="see-also"></a><span data-ttu-id="ae7cc-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-117">See Also</span></span>  
 [<span data-ttu-id="ae7cc-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ae7cc-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ae7cc-119">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="ae7cc-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="ae7cc-120">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="ae7cc-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="ae7cc-121">İşaretçileri İşleme</span><span class="sxs-lookup"><span data-stu-id="ae7cc-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="ae7cc-122">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="ae7cc-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="ae7cc-123">Türler</span><span class="sxs-lookup"><span data-stu-id="ae7cc-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="ae7cc-124">unsafe</span><span class="sxs-lookup"><span data-stu-id="ae7cc-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="ae7cc-125">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="ae7cc-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="ae7cc-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="ae7cc-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
