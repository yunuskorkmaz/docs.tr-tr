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
ms.openlocfilehash: eef6314f5fc1f5a7fffa7997559f697130f6f755
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401452"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="213d3-102">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="213d3-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="213d3-103">Bir ifadede birkaç işlem gerçekleştiğinde, her parça, *işleç önceliği*olarak adlandırılan önceden belirlenmiş bir sırada değerlendirilir ve çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="213d3-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>

## <a name="precedence-rules"></a><span data-ttu-id="213d3-104">Öncelik kuralları</span><span class="sxs-lookup"><span data-stu-id="213d3-104">Precedence Rules</span></span>
 <span data-ttu-id="213d3-105">İfadeler birden fazla kategoriden işleçler içerdiğinde, bunlar aşağıdaki kurallara göre değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="213d3-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>

- <span data-ttu-id="213d3-106">Aritmetik ve birleştirme işleçleri aşağıdaki bölümde açıklanan öncelik sırasına sahiptir ve tümü karşılaştırma, mantıksal ve bit düzeyinde operatörlerden daha önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="213d3-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>

- <span data-ttu-id="213d3-107">Tüm karşılaştırma işleçleri eşit önceliğe sahiptir ve tümü mantıksal ve bit düzeyinde operatörlerden daha önceliklidir, ancak aritmetik ve birleştirme işleçlerinden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="213d3-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>

- <span data-ttu-id="213d3-108">Mantıksal ve bit düzeyinde işleçler aşağıdaki bölümde açıklanan öncelik sırasına sahiptir ve tümünün aritmetik, birleştirme ve karşılaştırma işleçlerinden daha düşük önceliği vardır.</span><span class="sxs-lookup"><span data-stu-id="213d3-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>

- <span data-ttu-id="213d3-109">Eşit önceliğe sahip işleçler, ifadede göründükleri sırada soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="213d3-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>

## <a name="precedence-order"></a><span data-ttu-id="213d3-110">Öncelik sırası</span><span class="sxs-lookup"><span data-stu-id="213d3-110">Precedence Order</span></span>
 <span data-ttu-id="213d3-111">İşleçler aşağıdaki öncelik sırasına göre değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="213d3-111">Operators are evaluated in the following order of precedence:</span></span>

### <a name="await-operator"></a><span data-ttu-id="213d3-112">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="213d3-112">Await Operator</span></span>
 <span data-ttu-id="213d3-113">Await</span><span class="sxs-lookup"><span data-stu-id="213d3-113">Await</span></span>

### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="213d3-114">Aritmetik ve birleştirme Işleçleri</span><span class="sxs-lookup"><span data-stu-id="213d3-114">Arithmetic and Concatenation Operators</span></span>
 <span data-ttu-id="213d3-115">Üs ( `^` )</span><span class="sxs-lookup"><span data-stu-id="213d3-115">Exponentiation (`^`)</span></span>

 <span data-ttu-id="213d3-116">Birli kimlik ve olumsuzlama ( `+` , `–` )</span><span class="sxs-lookup"><span data-stu-id="213d3-116">Unary identity and negation (`+`, `–`)</span></span>

 <span data-ttu-id="213d3-117">Çarpma ve kayan nokta bölmesi ( `*` , `/` )</span><span class="sxs-lookup"><span data-stu-id="213d3-117">Multiplication and floating-point division (`*`, `/`)</span></span>

 <span data-ttu-id="213d3-118">Tamsayı bölümü ( `\` )</span><span class="sxs-lookup"><span data-stu-id="213d3-118">Integer division (`\`)</span></span>

 <span data-ttu-id="213d3-119">Modüler aritmetik ( `Mod` )</span><span class="sxs-lookup"><span data-stu-id="213d3-119">Modular arithmetic (`Mod`)</span></span>

 <span data-ttu-id="213d3-120">Toplama ve çıkarma ( `+` , `–` )</span><span class="sxs-lookup"><span data-stu-id="213d3-120">Addition and subtraction (`+`, `–`)</span></span>

 <span data-ttu-id="213d3-121">Dize birleştirme ( `&` )</span><span class="sxs-lookup"><span data-stu-id="213d3-121">String concatenation (`&`)</span></span>

 <span data-ttu-id="213d3-122">Aritmetik bit kaydırma ( `<<` , `>>` )</span><span class="sxs-lookup"><span data-stu-id="213d3-122">Arithmetic bit shift (`<<`, `>>`)</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="213d3-123">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="213d3-123">Comparison Operators</span></span>
 <span data-ttu-id="213d3-124">Tüm karşılaştırma işleçleri ( `=` , `<>` , `<` , `<=` , `>` , `>=` , `Is` , `IsNot` , `Like` , `TypeOf` ... `Is` )</span><span class="sxs-lookup"><span data-stu-id="213d3-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>

### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="213d3-125">Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="213d3-125">Logical and Bitwise Operators</span></span>
 <span data-ttu-id="213d3-126">Değilleme ( `Not` )</span><span class="sxs-lookup"><span data-stu-id="213d3-126">Negation (`Not`)</span></span>

 <span data-ttu-id="213d3-127">Birlikte ( `And` , `AndAlso` )</span><span class="sxs-lookup"><span data-stu-id="213d3-127">Conjunction (`And`, `AndAlso`)</span></span>

 <span data-ttu-id="213d3-128">Kapsamlı ayırıcı ( `Or` , `OrElse` )</span><span class="sxs-lookup"><span data-stu-id="213d3-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>

 <span data-ttu-id="213d3-129">Dışlamalı ayırıcı ( `Xor` )</span><span class="sxs-lookup"><span data-stu-id="213d3-129">Exclusive disjunction (`Xor`)</span></span>

### <a name="comments"></a><span data-ttu-id="213d3-130">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="213d3-130">Comments</span></span>
 <span data-ttu-id="213d3-131">`=`İşleci atama işleci değil yalnızca eşitlik karşılaştırma işleçtir.</span><span class="sxs-lookup"><span data-stu-id="213d3-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="213d3-132">Dize birleştirme işleci ( `&` ) bir aritmetik işleç değil, ancak önceliğe göre Aritmetik işleçlerle gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="213d3-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>

 <span data-ttu-id="213d3-133">`Is`Ve `IsNot` işleçleri nesne başvurusu karşılaştırma işleçleridir.</span><span class="sxs-lookup"><span data-stu-id="213d3-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="213d3-134">İki nesnenin değerlerini karşılaştırmazlar; yalnızca iki nesne değişkeninin aynı nesne örneğine başvurmadığını belirlemesini denetler.</span><span class="sxs-lookup"><span data-stu-id="213d3-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>

## <a name="associativity"></a><span data-ttu-id="213d3-135">İlişkilendirilebilirlik</span><span class="sxs-lookup"><span data-stu-id="213d3-135">Associativity</span></span>
 <span data-ttu-id="213d3-136">Eşit önceliğe sahip işleçler bir ifadede birlikte görüntülendiğinde, örneğin çarpma ve bölme gibi, derleyici, her işlemi soldan sağa karşılaştığı şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="213d3-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="213d3-137">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="213d3-137">The following example illustrates this.</span></span>

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 <span data-ttu-id="213d3-138">İlk ifade, Bölüm 96/8 ' i (12 ' de sonuç olarak) değerlendirir ve sonra Bölüm 12/4 ' dir ve bu da üç ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="213d3-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="213d3-139">Derleyici işlemleri soldan sağa değerlendirdiği için `n1` , bu sıra için açıkça belirtildiği zaman değerlendirme aynı olur `n2` .</span><span class="sxs-lookup"><span data-stu-id="213d3-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="213d3-140">Her ikisi de `n1` üç ile oluşur `n2` .</span><span class="sxs-lookup"><span data-stu-id="213d3-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="213d3-141">Bunun aksine `n3` 48 sonucu vardır, çünkü parantezler derleyicinin önce 8/4 ' i değerlendirmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="213d3-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>

 <span data-ttu-id="213d3-142">Bu davranış nedeniyle, operatörlerin Visual Basic olarak *sola ilişkilendirilebilir* olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="213d3-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>

## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="213d3-143">Öncelik ve birleşim özelliklerini geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="213d3-143">Overriding Precedence and Associativity</span></span>
 <span data-ttu-id="213d3-144">Bir ifadenin bazı bölümlerinin diğerlerinden önce değerlendirilmesini zorlamak için parantezleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="213d3-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="213d3-145">Bu, hem öncelik sırasını hem de sola ilişkilendirilebilirliği geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="213d3-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="213d3-146">Visual Basic, dış öğelerden önce parantez içine alınmış işlemleri her zaman gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="213d3-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="213d3-147">Bununla birlikte, parantez içinde parantez kullanmadığınız müddetçe, parantez içinde normal öncelik ve ilişkilendirilebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="213d3-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="213d3-148">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="213d3-148">The following example illustrates this.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="213d3-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="213d3-149">See also</span></span>

- [<span data-ttu-id="213d3-150">= İşleci</span><span class="sxs-lookup"><span data-stu-id="213d3-150">= Operator</span></span>](assignment-operator.md)
- [<span data-ttu-id="213d3-151">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="213d3-151">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="213d3-152">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="213d3-152">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="213d3-153">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="213d3-153">Like Operator</span></span>](like-operator.md)
- [<span data-ttu-id="213d3-154">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="213d3-154">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="213d3-155">Await Işleci</span><span class="sxs-lookup"><span data-stu-id="213d3-155">Await Operator</span></span>](await-operator.md)
- [<span data-ttu-id="213d3-156">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="213d3-156">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="213d3-157">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="213d3-157">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
