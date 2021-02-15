---
description: 'Hakkında daha fazla bilgi edinin: etkin Işleçler birleşimi (Visual Basic)'
title: İşleçlerin Etkili Bileşimi
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: a4d2d0c1caeea95dd8d34b2033a398d26bcf63ef
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476273"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="214db-103">İşleçlerin Etkili Bileşimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="214db-103">Efficient Combination of Operators (Visual Basic)</span></span>

<span data-ttu-id="214db-104">Karmaşık ifadelerde birçok farklı işleç bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="214db-104">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="214db-105">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="214db-105">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="214db-106">Önceki örnekteki gibi karmaşık ifadelerin oluşturulması, işleç önceliği kurallarının eksiksiz bir şekilde anlaşılmasına gerek duyar.</span><span class="sxs-lookup"><span data-stu-id="214db-106">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="214db-107">Daha fazla bilgi için [Visual Basic operatör önceliği](../../../language-reference/operators/operator-precedence.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="214db-107">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="214db-108">Parantez içinde Ifadeler</span><span class="sxs-lookup"><span data-stu-id="214db-108">Parenthetical Expressions</span></span>  

 <span data-ttu-id="214db-109">Genellikle işlemlerin operatör önceliğine göre belirlenen şekilde farklı bir sırada devam etmesini istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="214db-109">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="214db-110">Aşağıdaki örneği inceleyin.</span><span class="sxs-lookup"><span data-stu-id="214db-110">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="214db-111">Önceki örnek ile çarpar `z` `y` , sonra sonucunu öğesine ekler `4` .</span><span class="sxs-lookup"><span data-stu-id="214db-111">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="214db-112">Ancak `y` `4` , sonucu çarpmadan önce eklemek istiyorsanız `z` , parantez kullanarak normal operatör önceliğini geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="214db-112">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="214db-113">Bir ifadeyi parantez içine alarak, işleç önceliği ne olursa olsun, bu ifadenin ilk olarak değerlendirilmesini zorlarsınız.</span><span class="sxs-lookup"><span data-stu-id="214db-113">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="214db-114">Önceki örneği öncelikle eklemeyi zorlamak için, aşağıdaki örnekte olduğu gibi yeniden yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="214db-114">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="214db-115">Yukarıdaki örnek, `y` ve `4` sonra bu toplamı ile çarpar `z` .</span><span class="sxs-lookup"><span data-stu-id="214db-115">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="214db-116">İç içe geçmiş parantez Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="214db-116">Nested Parenthetical Expressions</span></span>  

 <span data-ttu-id="214db-117">Daha da fazla öncelik vermek için ifadeleri birden çok parantez düzeyinde iç içe yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="214db-117">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="214db-118">Parantez içinde en derin iç içe yerleştirilmiş ifadeler önce değerlendirilir, ardından sonraki en derin iç içe geçmiş ve bu, en az derin iç içe, son olarak da parantez dışında ifadeler.</span><span class="sxs-lookup"><span data-stu-id="214db-118">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="214db-119">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="214db-119">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="214db-120">Önceki örnekte, `z + 2` önce değerlendirilir, sonra diğer parantez içinde ifadeler.</span><span class="sxs-lookup"><span data-stu-id="214db-120">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="214db-121">Normalde ekleme veya çarpmayla daha yüksek önceliğe sahip olan üs, bu örnekte en son değerlendirilir çünkü diğer ifadeler parantez içine alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="214db-121">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="214db-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="214db-122">See also</span></span>

- [<span data-ttu-id="214db-123">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="214db-123">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="214db-124">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="214db-124">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="214db-125">Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="214db-125">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="214db-126">Mantıksal/Bit Düzeyinde İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="214db-126">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="214db-127">Boole Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="214db-127">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="214db-128">Değer Karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="214db-128">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="214db-129">Nasıl yapılır: Sayısal Değerleri Hesaplama</span><span class="sxs-lookup"><span data-stu-id="214db-129">How to: Calculate Numeric Values</span></span>](how-to-calculate-numeric-values.md)
- [<span data-ttu-id="214db-130">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="214db-130">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
