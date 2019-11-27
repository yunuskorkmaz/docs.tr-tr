---
title: İşleç Önceliği
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
ms.openlocfilehash: 318fcc3f35276ba0b2061ba9677c5fde29429f6f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348273"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="cceb0-102">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="cceb0-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="cceb0-103">Bir ifadede birkaç işlem gerçekleştiğinde, her parça, *işleç önceliği*olarak adlandırılan önceden belirlenmiş bir sırada değerlendirilir ve çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="cceb0-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>

## <a name="precedence-rules"></a><span data-ttu-id="cceb0-104">Öncelik kuralları</span><span class="sxs-lookup"><span data-stu-id="cceb0-104">Precedence Rules</span></span>
 <span data-ttu-id="cceb0-105">İfadeler birden fazla kategoriden işleçler içerdiğinde, bunlar aşağıdaki kurallara göre değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="cceb0-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>

- <span data-ttu-id="cceb0-106">Aritmetik ve birleştirme işleçleri aşağıdaki bölümde açıklanan öncelik sırasına sahiptir ve tümü karşılaştırma, mantıksal ve bit düzeyinde operatörlerden daha önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="cceb0-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>

- <span data-ttu-id="cceb0-107">Tüm karşılaştırma işleçleri eşit önceliğe sahiptir ve tümü mantıksal ve bit düzeyinde operatörlerden daha önceliklidir, ancak aritmetik ve birleştirme işleçlerinden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cceb0-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>

- <span data-ttu-id="cceb0-108">Mantıksal ve bit düzeyinde işleçler aşağıdaki bölümde açıklanan öncelik sırasına sahiptir ve tümünün aritmetik, birleştirme ve karşılaştırma işleçlerinden daha düşük önceliği vardır.</span><span class="sxs-lookup"><span data-stu-id="cceb0-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>

- <span data-ttu-id="cceb0-109">Eşit önceliğe sahip işleçler, ifadede göründükleri sırada soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="cceb0-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>

## <a name="precedence-order"></a><span data-ttu-id="cceb0-110">Öncelik sırası</span><span class="sxs-lookup"><span data-stu-id="cceb0-110">Precedence Order</span></span>
 <span data-ttu-id="cceb0-111">İşleçler aşağıdaki öncelik sırasına göre değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="cceb0-111">Operators are evaluated in the following order of precedence:</span></span>

### <a name="await-operator"></a><span data-ttu-id="cceb0-112">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="cceb0-112">Await Operator</span></span>
 <span data-ttu-id="cceb0-113">Await</span><span class="sxs-lookup"><span data-stu-id="cceb0-113">Await</span></span>

### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="cceb0-114">Aritmetik ve birleştirme Işleçleri</span><span class="sxs-lookup"><span data-stu-id="cceb0-114">Arithmetic and Concatenation Operators</span></span>
 <span data-ttu-id="cceb0-115">Üs (`^`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-115">Exponentiation (`^`)</span></span>

 <span data-ttu-id="cceb0-116">Birli kimlik ve olumsuzlama (`+``–`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-116">Unary identity and negation (`+`, `–`)</span></span>

 <span data-ttu-id="cceb0-117">Çarpma ve kayan nokta bölme (`*``/`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-117">Multiplication and floating-point division (`*`, `/`)</span></span>

 <span data-ttu-id="cceb0-118">Tamsayı bölümü (`\`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-118">Integer division (`\`)</span></span>

 <span data-ttu-id="cceb0-119">Modüler aritmetik (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-119">Modular arithmetic (`Mod`)</span></span>

 <span data-ttu-id="cceb0-120">Toplama ve çıkarma (`+``–`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-120">Addition and subtraction (`+`, `–`)</span></span>

 <span data-ttu-id="cceb0-121">Dize birleştirme (`&`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-121">String concatenation (`&`)</span></span>

 <span data-ttu-id="cceb0-122">Aritmetik bit kaydırma (`<<`, `>>`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-122">Arithmetic bit shift (`<<`, `>>`)</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="cceb0-123">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="cceb0-123">Comparison Operators</span></span>
 <span data-ttu-id="cceb0-124">Tüm karşılaştırma işleçleri (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>

### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="cceb0-125">Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="cceb0-125">Logical and Bitwise Operators</span></span>
 <span data-ttu-id="cceb0-126">Değilleme (`Not`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-126">Negation (`Not`)</span></span>

 <span data-ttu-id="cceb0-127">Birlikte (`And``AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-127">Conjunction (`And`, `AndAlso`)</span></span>

 <span data-ttu-id="cceb0-128">Kapsamlı birleşim (`Or``OrElse`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>

 <span data-ttu-id="cceb0-129">Dışlamalı ayırıcı (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="cceb0-129">Exclusive disjunction (`Xor`)</span></span>

### <a name="comments"></a><span data-ttu-id="cceb0-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cceb0-130">Comments</span></span>
 <span data-ttu-id="cceb0-131">`=` işleci, atama işleci değil yalnızca eşitlik karşılaştırma işleçtir.</span><span class="sxs-lookup"><span data-stu-id="cceb0-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="cceb0-132">Dize birleştirme işleci (`&`) bir aritmetik işleç değil, ancak önceliğe göre Aritmetik işleçlerle gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="cceb0-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>

 <span data-ttu-id="cceb0-133">`Is` ve `IsNot` işleçleri nesne başvurusu karşılaştırma işleçleridir.</span><span class="sxs-lookup"><span data-stu-id="cceb0-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="cceb0-134">İki nesnenin değerlerini karşılaştırmazlar; yalnızca iki nesne değişkeninin aynı nesne örneğine başvurmadığını belirlemesini denetler.</span><span class="sxs-lookup"><span data-stu-id="cceb0-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>

## <a name="associativity"></a><span data-ttu-id="cceb0-135">İlişkilendirilebilirlik</span><span class="sxs-lookup"><span data-stu-id="cceb0-135">Associativity</span></span>
 <span data-ttu-id="cceb0-136">Eşit önceliğe sahip işleçler bir ifadede birlikte görüntülendiğinde, örneğin çarpma ve bölme gibi, derleyici, her işlemi soldan sağa karşılaştığı şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="cceb0-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="cceb0-137">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="cceb0-137">The following example illustrates this.</span></span>

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 <span data-ttu-id="cceb0-138">İlk ifade, Bölüm 96/8 ' i (12 ' de sonuç olarak) değerlendirir ve sonra Bölüm 12/4 ' dir ve bu da üç ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="cceb0-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="cceb0-139">Derleyici işlemleri soldan sağa `n1` değerlendirdiği için, bu sıra `n2`için açıkça belirtildiği zaman değerlendirme aynı olur.</span><span class="sxs-lookup"><span data-stu-id="cceb0-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="cceb0-140">Hem `n1` hem de `n2` üç ile oluşur.</span><span class="sxs-lookup"><span data-stu-id="cceb0-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="cceb0-141">Bunun aksine, `n3` 48 sonucunu elde ettiğinden, parantezler öncelikle derleyicinin 8/4 ' i değerlendirmesini zorlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="cceb0-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>

 <span data-ttu-id="cceb0-142">Bu davranış nedeniyle, operatörlerin Visual Basic olarak *sola ilişkilendirilebilir* olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="cceb0-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>

## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="cceb0-143">Öncelik ve birleşim özelliklerini geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="cceb0-143">Overriding Precedence and Associativity</span></span>
 <span data-ttu-id="cceb0-144">Bir ifadenin bazı bölümlerinin diğerlerinden önce değerlendirilmesini zorlamak için parantezleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cceb0-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="cceb0-145">Bu, hem öncelik sırasını hem de sola ilişkilendirilebilirliği geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="cceb0-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="cceb0-146">Visual Basic, dış öğelerden önce parantez içine alınmış işlemleri her zaman gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="cceb0-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="cceb0-147">Bununla birlikte, parantez içinde parantez kullanmadığınız müddetçe, parantez içinde normal öncelik ve ilişkilendirilebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="cceb0-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="cceb0-148">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="cceb0-148">The following example illustrates this.</span></span>

```vb
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

## <a name="see-also"></a><span data-ttu-id="cceb0-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cceb0-149">See also</span></span>

- [<span data-ttu-id="cceb0-150">= İşleci</span><span class="sxs-lookup"><span data-stu-id="cceb0-150">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="cceb0-151">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="cceb0-151">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="cceb0-152">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="cceb0-152">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="cceb0-153">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="cceb0-153">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="cceb0-154">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="cceb0-154">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="cceb0-155">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="cceb0-155">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="cceb0-156">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="cceb0-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="cceb0-157">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="cceb0-157">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
