---
title: as (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: cc5bb62d94e6999bf9174bd2221fb68e7c711588
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208412"
---
# <a name="as-c-reference"></a><span data-ttu-id="65e25-102">as (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="65e25-102">as (C# Reference)</span></span>
<span data-ttu-id="65e25-103">Kullanabileceğiniz `as` belirli türde bir uyumlu başvuru türleri arasında dönüştürme gerçekleştirmek için işleci veya [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="65e25-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="65e25-104">Aşağıdaki kod örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="65e25-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]
  
## <a name="remarks"></a><span data-ttu-id="65e25-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65e25-105">Remarks</span></span>  
 <span data-ttu-id="65e25-106">`as` İşlecidir gibi bir dönüştürme işlemi.</span><span class="sxs-lookup"><span data-stu-id="65e25-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="65e25-107">Ancak, dönüştürme mümkün değilse `as` döndürür `null` yerine bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65e25-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="65e25-108">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="65e25-108">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="65e25-109">Kod aşağıdaki ifade, dışında eşdeğerdir `expression` değişken yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="65e25-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="65e25-110">Unutmayın `as` işleci yalnızca başvuru dönüşümleri, boş değer atanabilir dönüşümler ve kutulamayı dönüşümleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="65e25-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="65e25-111">`as` İşleci cast ifadeler kullanarak yerine gerçekleştirilmesi gereken kullanıcı tanımlı dönüşümler gibi diğer dönüştürme gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="65e25-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65e25-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="65e25-112">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="65e25-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="65e25-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="65e25-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65e25-114">See Also</span></span>  
 [<span data-ttu-id="65e25-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="65e25-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="65e25-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="65e25-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="65e25-117">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="65e25-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="65e25-118">is</span><span class="sxs-lookup"><span data-stu-id="65e25-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="65e25-119">?: İşleci</span><span class="sxs-lookup"><span data-stu-id="65e25-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
 [<span data-ttu-id="65e25-120">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="65e25-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
