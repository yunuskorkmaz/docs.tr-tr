---
title: 'Nasıl yapılır: işaretçileri artırma ve azaltma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: c75432d88a1e96742573a6e69a4e035066a387c4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128342"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="ea0f4-102">Nasıl yapılır: işaretçileri artırma ve azaltma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ea0f4-102">How to: increment and decrement pointers (C# Programming Guide)</span></span>

<span data-ttu-id="ea0f4-103">Artırma ve azaltma işleçleri kullanan `++` ve `--`işaretçi konuma göre değişmesini `sizeof(pointer-type)` türünde bir işaretçi için `pointer-type*`.</span><span class="sxs-lookup"><span data-stu-id="ea0f4-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by `sizeof(pointer-type)` for a pointer of the type `pointer-type*`.</span></span> <span data-ttu-id="ea0f4-104">Artırma ve azaltma ifadeleri aşağıdaki biçiminde:</span><span class="sxs-lookup"><span data-stu-id="ea0f4-104">The increment and decrement expressions take the following form:</span></span>  
  
```csharp
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="ea0f4-105">Tür dışında herhangi bir türde işaretçileri artırma ve azaltma işleçleri uygulanabilir `void*`.</span><span class="sxs-lookup"><span data-stu-id="ea0f4-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="ea0f4-106">Artırım işleci türünde bir işaretçiye uygulamak etkisini `pointer-type*` eklemektir `sizeof(pointer-type)` adresine işaretçi değişkeninde yer alır.</span><span class="sxs-lookup"><span data-stu-id="ea0f4-106">The effect of applying the increment operator to a pointer of the type `pointer-type*` is to add `sizeof(pointer-type)` to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="ea0f4-107">Azaltma işleci türünde bir işaretçiye uygulamak etkisini `pointer-type*` çıkarılacak olan `sizeof(pointer-type)` adresinden işaretçi değişkeninde yer alır.</span><span class="sxs-lookup"><span data-stu-id="ea0f4-107">The effect of applying the decrement operator to a pointer of the type `pointer-type*` is to subtract `sizeof(pointer-type)` from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="ea0f4-108">Hiçbir özel durum, etki alanı işaretçinin işlemi taşıyor ve sonuç uygulamasının bağlıdır, üretilir.</span><span class="sxs-lookup"><span data-stu-id="ea0f4-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea0f4-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea0f4-109">Example</span></span>  
 <span data-ttu-id="ea0f4-110">Bu örnekte, bir dizi aracılığıyla işaretçinin boyutuna artırılarak adım `int`.</span><span class="sxs-lookup"><span data-stu-id="ea0f4-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="ea0f4-111">Her adımda adresi ve dizi öğenin içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ea0f4-111">With each step, you display the address and the content of the array element.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
<span data-ttu-id="ea0f4-112">**Değer: 0 @ adresi: 12860272**
**değer: 1 @ adresi: 12860276**
**değer: 2 @ adresi: 12860280**
**değer: 3 @ adresi : 12860284**
**değer: 4 @ adresi: 12860288**</span><span class="sxs-lookup"><span data-stu-id="ea0f4-112">**Value:0 @ Address:12860272**
**Value:1 @ Address:12860276**
**Value:2 @ Address:12860280**
**Value:3 @ Address:12860284**
**Value:4 @ Address:12860288**</span></span>

## <a name="see-also"></a><span data-ttu-id="ea0f4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea0f4-113">See also</span></span>

- [<span data-ttu-id="ea0f4-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ea0f4-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ea0f4-115">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="ea0f4-115">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="ea0f4-116">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="ea0f4-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="ea0f4-117">İşaretçileri İşleme</span><span class="sxs-lookup"><span data-stu-id="ea0f4-117">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="ea0f4-118">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="ea0f4-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="ea0f4-119">Türler</span><span class="sxs-lookup"><span data-stu-id="ea0f4-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="ea0f4-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="ea0f4-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="ea0f4-121">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="ea0f4-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="ea0f4-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="ea0f4-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
- [<span data-ttu-id="ea0f4-123">sizeof</span><span class="sxs-lookup"><span data-stu-id="ea0f4-123">sizeof</span></span>](../../../csharp/language-reference/keywords/sizeof.md)
