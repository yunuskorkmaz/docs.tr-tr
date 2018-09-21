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
ms.openlocfilehash: aee80b3262ccd9432d7c311dddec47185b66d05f
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46470733"
---
# <a name="as-c-reference"></a><span data-ttu-id="95af2-102">as (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="95af2-102">as (C# Reference)</span></span>
<span data-ttu-id="95af2-103">Kullanabileceğiniz `as` belirli türlerdeki uyumlu başvuru türleri arasında dönüştürmeler gerçekleştirmek için işleci veya [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="95af2-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="95af2-104">Aşağıdaki kod örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="95af2-104">The following code shows an example.</span></span>  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]
  
## <a name="remarks"></a><span data-ttu-id="95af2-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95af2-105">Remarks</span></span>  
 <span data-ttu-id="95af2-106">`as` İşleci, bir tür dönüştürme işlemini gibi.</span><span class="sxs-lookup"><span data-stu-id="95af2-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="95af2-107">Ancak, dönüştürme mümkün değilse `as` döndürür `null` yerine bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95af2-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="95af2-108">Aşağıdaki örnek göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="95af2-108">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="95af2-109">Kod, aşağıdaki ifade hariç eşdeğerdir `expression` değişken yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="95af2-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="95af2-110">Unutmayın `as` işleci, yalnızca başvuru dönüşümleri, boş değer atanabilir dönüştürmeler ve kutulama dönüştürmeleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="95af2-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="95af2-111">`as` İşleci, bunun yerine cast ifadeleri kullanarak gerçekleştirilmelidir kullanıcı tanımlı dönüşümler gibi diğer dönüştürmeler gerçekleştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="95af2-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95af2-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="95af2-112">Example</span></span>  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a><span data-ttu-id="95af2-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="95af2-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="95af2-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95af2-114">See Also</span></span>  
- [<span data-ttu-id="95af2-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="95af2-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="95af2-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="95af2-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="95af2-117">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="95af2-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="95af2-118">is</span><span class="sxs-lookup"><span data-stu-id="95af2-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="95af2-119">?: İşleci</span><span class="sxs-lookup"><span data-stu-id="95af2-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
- [<span data-ttu-id="95af2-120">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="95af2-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
