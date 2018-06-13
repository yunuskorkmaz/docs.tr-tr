---
title: Visual Basic'de İşleç Önceliği
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: 211a710f4dba2310ea1ae74decdb1926ce612a62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605010"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="4e0d8-102">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="4e0d8-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="4e0d8-103">Çeşitli işlemler bir ifadede gerçekleştiğinde, her bölüm değerlendirilir ve adlı önceden belirlenmiş bir sırayla çözülmüş *İşleç önceliği*.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>  
  
## <a name="precedence-rules"></a><span data-ttu-id="4e0d8-104">Öncelik kuralları</span><span class="sxs-lookup"><span data-stu-id="4e0d8-104">Precedence Rules</span></span>  
 <span data-ttu-id="4e0d8-105">İfadeleri birden fazla kategorisinden işleçler içeriyorsa, bunlar aşağıdaki kurallara göre değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="4e0d8-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>  
  
-   <span data-ttu-id="4e0d8-106">Aritmetik ve birleştirme işleçleri aşağıdaki bölümde açıklanan öncelik sırasını yoksa ve tüm mantıksal, karşılaştırma büyük önceliğe ve bit düzeyinde işleçler.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>  
  
-   <span data-ttu-id="4e0d8-107">Tüm Karşılaştırma işleçleri eşit önceliğe ve tüm mantıksal ve bit düzeyinde işleçler büyük önceliğe ancak aritmetik ve birleştirme işleçleri daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>  
  
-   <span data-ttu-id="4e0d8-108">Aşağıdaki bölümde açıklanan öncelik sırasını mantıksal ve bit düzeyinde işleçler sahiptir ve tüm aritmetik, birleştirme ve Karşılaştırma işleçleri daha düşük önceliğe sahip.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>  
  
-   <span data-ttu-id="4e0d8-109">Eşit önceliğe sahip işleçler soldan sağa değerlendirilen ifade göründükleri sırada.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>  
  
## <a name="precedence-order"></a><span data-ttu-id="4e0d8-110">Öncelik sırası</span><span class="sxs-lookup"><span data-stu-id="4e0d8-110">Precedence Order</span></span>  
 <span data-ttu-id="4e0d8-111">İşleç önceliği aşağıdaki sırayla değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="4e0d8-111">Operators are evaluated in the following order of precedence:</span></span>  
  
### <a name="await-operator"></a><span data-ttu-id="4e0d8-112">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="4e0d8-112">Await Operator</span></span>  
 <span data-ttu-id="4e0d8-113">await</span><span class="sxs-lookup"><span data-stu-id="4e0d8-113">Await</span></span>  
  
### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="4e0d8-114">Aritmetik ve birleştirme işleçleri</span><span class="sxs-lookup"><span data-stu-id="4e0d8-114">Arithmetic and Concatenation Operators</span></span>  
 <span data-ttu-id="4e0d8-115">Üs (`^`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-115">Exponentiation (`^`)</span></span>  
  
 <span data-ttu-id="4e0d8-116">Birli kimlik ve değilleme (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-116">Unary identity and negation (`+`, `–`)</span></span>  
  
 <span data-ttu-id="4e0d8-117">Çarpma ve kayan nokta bölme (`*`, `/`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-117">Multiplication and floating-point division (`*`, `/`)</span></span>  
  
 <span data-ttu-id="4e0d8-118">Tamsayı bölme (`\`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-118">Integer division (`\`)</span></span>  
  
 <span data-ttu-id="4e0d8-119">Modulus aritmetik (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-119">Modulus arithmetic (`Mod`)</span></span>  
  
 <span data-ttu-id="4e0d8-120">Toplama ve çıkarma (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-120">Addition and subtraction (`+`, `–`)</span></span>  
  
 <span data-ttu-id="4e0d8-121">Dize birleştirmesi (`&`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-121">String concatenation (`&`)</span></span>  
  
 <span data-ttu-id="4e0d8-122">Aritmetik bit kaydırma (`<<`, `>>`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-122">Arithmetic bit shift (`<<`, `>>`)</span></span>  
  
### <a name="comparison-operators"></a><span data-ttu-id="4e0d8-123">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="4e0d8-123">Comparison Operators</span></span>  
 <span data-ttu-id="4e0d8-124">Tüm Karşılaştırma işleçleri (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>  
  
### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="4e0d8-125">Mantıksal ve bit düzeyinde işleçler</span><span class="sxs-lookup"><span data-stu-id="4e0d8-125">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="4e0d8-126">Değilleme (`Not`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-126">Negation (`Not`)</span></span>  
  
 <span data-ttu-id="4e0d8-127">Birlikte (`And`, `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-127">Conjunction (`And`, `AndAlso`)</span></span>  
  
 <span data-ttu-id="4e0d8-128">Kapsayıcı ayrım (`Or`, `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>  
  
 <span data-ttu-id="4e0d8-129">Özel ayrım (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="4e0d8-129">Exclusive disjunction (`Xor`)</span></span>  
  
### <a name="comments"></a><span data-ttu-id="4e0d8-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e0d8-130">Comments</span></span>  
 <span data-ttu-id="4e0d8-131">`=` İşlecidir yalnızca eşitlik karşılaştırma işleci, atama işleci.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="4e0d8-132">Dize birleştirme işleci (`&`) bir aritmetik işleç değildir, ancak içinde öncelik aritmetik işleçler gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>  
  
 <span data-ttu-id="4e0d8-133">`Is` Ve `IsNot` işleçler şunlardır: nesne başvurusu Karşılaştırma işleçleri.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="4e0d8-134">İki nesnenin değerlerini karşılaştırmak değil; yalnızca iki nesne değişkenleri aynı nesne örneğine başvuru olup olmadığını belirlemek için denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>  
  
## <a name="associativity"></a><span data-ttu-id="4e0d8-135">İlişkilendirilebilirlik</span><span class="sxs-lookup"><span data-stu-id="4e0d8-135">Associativity</span></span>  
 <span data-ttu-id="4e0d8-136">Eşit öncelik işleçleri birlikte bir ifade örneğin çarpma ve bölme göründüğünde, soldan sağa karşılaştığında gibi derleyici her işlemi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="4e0d8-137">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-137">The following example illustrates this.</span></span>  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 <span data-ttu-id="4e0d8-138">İlk ifade 96 bölme değerlendirir / (12'de sonuçlarını) 8'i ve ardından bölme 12 / üç içinde sonuçları 4.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="4e0d8-139">Derleyici işlemler için değerlendirildiği `n1` Bu sipariş için açıkça belirtildiğinde soldan sağa değerlendirme aynıdır `n2`.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="4e0d8-140">Her ikisi de `n1` ve `n2` üç sonucunu sahip.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="4e0d8-141">Bunun aksine, `n3` 48, sonucunu sahip parantez 8 değerlendirmek için derleyici zorla olduğundan / 4 ilk.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>  
  
 <span data-ttu-id="4e0d8-142">Bu davranış nedeniyle işleçleri yereldir *ilişkilendirilebilir sol* Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>  
  
## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="4e0d8-143">Öncelik ve birleşim geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="4e0d8-143">Overriding Precedence and Associativity</span></span>  
 <span data-ttu-id="4e0d8-144">Başkalarının önce değerlendirilecek bir ifade bazı bölümleri zorlamak için parantez kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="4e0d8-145">Bu öncelik sırasını ve sol birleşim geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="4e0d8-146">Visual Basic her zaman dışındaki önce parantez içine işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="4e0d8-147">Parantez içinde parantez kullanmadığınız sürece ancak parantez içinde normal öncelik ve birleşim, tutar.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="4e0d8-148">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-148">The following example illustrates this.</span></span>  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e0d8-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e0d8-149">See Also</span></span>  
 [<span data-ttu-id="4e0d8-150">= İşleci</span><span class="sxs-lookup"><span data-stu-id="4e0d8-150">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [<span data-ttu-id="4e0d8-151">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="4e0d8-151">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="4e0d8-152">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="4e0d8-152">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="4e0d8-153">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="4e0d8-153">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="4e0d8-154">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="4e0d8-154">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="4e0d8-155">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="4e0d8-155">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="4e0d8-156">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="4e0d8-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="4e0d8-157">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="4e0d8-157">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
