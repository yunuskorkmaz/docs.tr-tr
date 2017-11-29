---
title: "?? İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a49d36b8580812c08e9ee080a9602d9fc2027ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6c62d-103">??</span><span class="sxs-lookup"><span data-stu-id="6c62d-103">??</span></span> <span data-ttu-id="6c62d-104">İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6c62d-104">Operator (C# Reference)</span></span>
<span data-ttu-id="6c62d-105">`??` İşleci, null birleşim işlecinin çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6c62d-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="6c62d-106">İşlenen null değilse, sol taraf işlenenini döndürür; tersi durumda, sağ el işlenenini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c62d-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c62d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c62d-107">Remarks</span></span>  
 <span data-ttu-id="6c62d-108">Null yapılabilir bir tür, türün etki alanından bir değeri gösterebilir veya değer tanımsız olabilir (bu durumda, değer null olur).</span><span class="sxs-lookup"><span data-stu-id="6c62d-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="6c62d-109">Kullanabileceğiniz `??` işlecin söz dizimi anlamlılık uygun bir değer (sağ işleneni) dönmek için sol işleneni null atanabilir bir tür değeri null olduğunda.</span><span class="sxs-lookup"><span data-stu-id="6c62d-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="6c62d-110">Bir boş değer atanabilen değer atanamayan değer türüne kullanmadan atamak üzere çalışırsanız `??` işleci, derleme zamanı hata üretir.</span><span class="sxs-lookup"><span data-stu-id="6c62d-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="6c62d-111">Bir cast kullanıyorsanız ve boş değer atanabilen değer türü şu anda tanımlanmamış bir `InvalidOperationException` özel durum.</span><span class="sxs-lookup"><span data-stu-id="6c62d-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="6c62d-112">Daha fazla bilgi için bkz: [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="6c62d-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="6c62d-113">Sonucunu bir??</span><span class="sxs-lookup"><span data-stu-id="6c62d-113">The result of a ??</span></span> <span data-ttu-id="6c62d-114">işleç iki bağımsız değişkenlerini sabitleri olsa bile bir sabit olarak kabul değil.</span><span class="sxs-lookup"><span data-stu-id="6c62d-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c62d-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c62d-115">Example</span></span>  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6c62d-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c62d-116">See Also</span></span>  
 [<span data-ttu-id="6c62d-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6c62d-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6c62d-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6c62d-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6c62d-119">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="6c62d-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="6c62d-120">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="6c62d-120">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="6c62d-121">Hangi tam olarak 'Kaldırılmış' anlamına mu?</span><span class="sxs-lookup"><span data-stu-id="6c62d-121">What Exactly Does 'Lifted' mean?</span></span>](http://go.microsoft.com/fwlink/?LinkID=112382)
