---
title: + İşleci (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb0d66db2d777c046ccec69acc1f2069d21baf6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="1e2d4-102">+ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e2d4-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="1e2d4-103">İki sayı ekleyen ya da pozitif sayısal ifadenin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="1e2d4-104">Ayrıca iki dize ifadeleri birleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e2d4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e2d4-105">Syntax</span></span>  
  
```  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="1e2d4-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="1e2d4-106">Parts</span></span>  
  
|<span data-ttu-id="1e2d4-107">Terim</span><span class="sxs-lookup"><span data-stu-id="1e2d4-107">Term</span></span>|<span data-ttu-id="1e2d4-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="1e2d4-108">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="1e2d4-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-109">Required.</span></span> <span data-ttu-id="1e2d4-110">Tüm sayısal veya dize ifadesi.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-110">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="1e2d4-111">Sürece gerekli `+` işleci negatif bir değer hesaplıyor.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-111">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="1e2d4-112">Tüm sayısal veya dize ifadesi.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-112">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="1e2d4-113">Sonuç</span><span class="sxs-lookup"><span data-stu-id="1e2d4-113">Result</span></span>  
 <span data-ttu-id="1e2d4-114">Varsa `expression1` ve `expression2` hem de sayısal sonucudur kendi aritmetik toplam olması.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-114">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="1e2d4-115">Varsa `expression2` yoksa, `+` işlecidir *birli* değişmez değeri ifade kimlik işleci.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-115">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="1e2d4-116">İşaretini korur işlem bu anlamda oluşur `expression1`sonucu negatif gelir, `expression1` negatiftir.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-116">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="1e2d4-117">Varsa `expression1` ve `expression2` hem dizelerdir değerlerine birleşimini sonucudur.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-117">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="1e2d4-118">Varsa `expression1` ve `expression2` olan karma türleri, gerçekleştirilecek eylem türlerini, içeriklerini ve ayarını bağlıdır [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1e2d4-118">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="1e2d4-119">Daha fazla bilgi için bkz: "Açıklamalar" ın tabloları</span><span class="sxs-lookup"><span data-stu-id="1e2d4-119">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="1e2d4-120">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="1e2d4-120">Supported Types</span></span>  
 <span data-ttu-id="1e2d4-121">İmzasız ve kayan nokta türleri dahil olmak üzere tüm sayısal türler ve `Decimal`, ve `String`.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-121">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e2d4-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e2d4-122">Remarks</span></span>  
 <span data-ttu-id="1e2d4-123">Genel olarak, `+` aritmetik toplama mümkün olduğunda gerçekleştirir ve yalnızca her iki ifade dizeleri olduğunda art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-123">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="1e2d4-124">Hiçbiri ifade ise bir `Object`, Visual Basic aşağıdaki eylemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-124">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="1e2d4-125">İfade veri türleri</span><span class="sxs-lookup"><span data-stu-id="1e2d4-125">Data types of expressions</span></span>|<span data-ttu-id="1e2d4-126">Derleyici tarafından eylemi</span><span class="sxs-lookup"><span data-stu-id="1e2d4-126">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="1e2d4-127">Her iki ifadelerini sayısal veri türleri (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, veya `Double`)</span><span class="sxs-lookup"><span data-stu-id="1e2d4-127">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="1e2d4-128">Ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-128">Add.</span></span> <span data-ttu-id="1e2d4-129">Sonuç veri türü sayısal bir tür veri türleri için uygun değil `expression1` ve `expression2`.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-129">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="1e2d4-130">"Tamsayı aritmetiğini" tablolarda bkz [işleci sonuçlarını veri türleri](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="1e2d4-130">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="1e2d4-131">Her iki ifadelerini türü`String`</span><span class="sxs-lookup"><span data-stu-id="1e2d4-131">Both expressions are of type `String`</span></span>|<span data-ttu-id="1e2d4-132">Art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-132">Concatenate.</span></span>|  
|<span data-ttu-id="1e2d4-133">Bir ifade sayısal veri türüne ve diğer bir dizedir</span><span class="sxs-lookup"><span data-stu-id="1e2d4-133">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="1e2d4-134">Varsa `Option Strict` olan `On`, derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-134">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="1e2d4-135">Varsa `Option Strict` olan `Off`, örtük dönüştürme `String` için `Double` ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-135">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="1e2d4-136">Varsa `String` dönüştürülemiyor `Double`, ardından throw bir <xref:System.InvalidCastException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-136">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="1e2d4-137">Bir ifade sayısal veri türüne ve diğer [hiçbir şey](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="1e2d4-137">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="1e2d4-138">Ekleme, ile `Nothing` sıfır olarak değerli.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-138">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="1e2d4-139">Bir ifadenin bir dize ve diğer`Nothing`</span><span class="sxs-lookup"><span data-stu-id="1e2d4-139">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="1e2d4-140">Birleştir ile `Nothing` değerli olarak "".</span><span class="sxs-lookup"><span data-stu-id="1e2d4-140">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="1e2d4-141">Bir ifade olması durumunda bir `Object` ifadesi, Visual Basic, aşağıdaki eylemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-141">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="1e2d4-142">İfade veri türleri</span><span class="sxs-lookup"><span data-stu-id="1e2d4-142">Data types of expressions</span></span>|<span data-ttu-id="1e2d4-143">Derleyici tarafından eylemi</span><span class="sxs-lookup"><span data-stu-id="1e2d4-143">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="1e2d4-144">`Object`ifade sayısal bir değer içerir ve diğeri sayısal veri türüne</span><span class="sxs-lookup"><span data-stu-id="1e2d4-144">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="1e2d4-145">Varsa `Option Strict` olan `On`, derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-145">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="1e2d4-146">Varsa `Option Strict` olan `Off`, sonra ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-146">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="1e2d4-147">`Object`sayısal bir değer ifadesi tutar ve diğer türüdür`String`</span><span class="sxs-lookup"><span data-stu-id="1e2d4-147">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="1e2d4-148">Varsa `Option Strict` olan `On`, derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-148">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="1e2d4-149">Varsa `Option Strict` olan `Off`, örtük dönüştürme `String` için `Double` ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-149">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="1e2d4-150">Varsa `String` dönüştürülemiyor `Double`, ardından throw bir <xref:System.InvalidCastException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-150">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="1e2d4-151">`Object`bir dize ifadesi tutar ve diğer sayısal veri türü</span><span class="sxs-lookup"><span data-stu-id="1e2d4-151">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="1e2d4-152">Varsa `Option Strict` olan `On`, derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-152">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="1e2d4-153">Varsa `Option Strict` olan `Off`, dize örtük dönüştürme `Object` için `Double` ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-153">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="1e2d4-154">Varsa dize `Object` dönüştürülemiyor `Double`, ardından throw bir <xref:System.InvalidCastException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-154">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="1e2d4-155">`Object`bir dize ifadesi tutar ve diğer türüdür`String`</span><span class="sxs-lookup"><span data-stu-id="1e2d4-155">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="1e2d4-156">Varsa `Option Strict` olan `On`, derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-156">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="1e2d4-157">Varsa `Option Strict` olan `Off`, örtük dönüştürme `Object` için `String` ve art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-157">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="1e2d4-158">Her iki ifadeler `Object` ifadeleri, Visual Basic, aşağıdaki eylemleri gerçekleştirir (`Option Strict Off` yalnızca).</span><span class="sxs-lookup"><span data-stu-id="1e2d4-158">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="1e2d4-159">İfade veri türleri</span><span class="sxs-lookup"><span data-stu-id="1e2d4-159">Data types of expressions</span></span>|<span data-ttu-id="1e2d4-160">Derleyici tarafından eylemi</span><span class="sxs-lookup"><span data-stu-id="1e2d4-160">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="1e2d4-161">Her ikisi de `Object` ifadeleri sayısal değerleri tutun</span><span class="sxs-lookup"><span data-stu-id="1e2d4-161">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="1e2d4-162">Ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-162">Add.</span></span>|  
|<span data-ttu-id="1e2d4-163">Her ikisi de `Object` ifadelerini türü`String`</span><span class="sxs-lookup"><span data-stu-id="1e2d4-163">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="1e2d4-164">Art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-164">Concatenate.</span></span>|  
|<span data-ttu-id="1e2d4-165">Bir `Object` ifade sayısal bir değer tutar ve diğer bir dize tutar</span><span class="sxs-lookup"><span data-stu-id="1e2d4-165">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="1e2d4-166">Örtük olarak dize dönüştürme `Object` için `Double` ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-166">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="1e2d4-167">Varsa dize `Object` sayısal bir değere dönüştürülemez sonra throw bir <xref:System.InvalidCastException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-167">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="1e2d4-168">Her iki `Object` ifadeyi hesaplar için [hiçbir şey](../../../visual-basic/language-reference/nothing.md) veya <xref:System.DBNull>, `+` işleci da işler bir `String` değerini "".</span><span class="sxs-lookup"><span data-stu-id="1e2d4-168">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e2d4-169">Kullandığınızda `+` işleci, eklenmesi veya dize birleştirme oluşacaktır olup olmadığını belirlemek kuramıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-169">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="1e2d4-170">Kullanım `&` belirsizliği ortadan kaldırmak ve kendi kendine belgelendirme kod sağlamak için birleştirme için işleci.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-170">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1e2d4-171">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="1e2d4-171">Overloading</span></span>  
 <span data-ttu-id="1e2d4-172">`+` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-172">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1e2d4-173">Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-173">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1e2d4-174">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1e2d4-174">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e2d4-175">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e2d4-175">Example</span></span>  
 <span data-ttu-id="1e2d4-176">Aşağıdaki örnek kullanır `+` sayıları işleci.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-176">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="1e2d4-177">İşlenen her ikisi de sayısal olursa, Visual Basic Aritmetik sonuç hesaplar.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-177">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="1e2d4-178">Aritmetik sonuç iki işlenen toplamını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-178">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 <span data-ttu-id="1e2d4-179">Aynı zamanda `+` dizeyi birleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-179">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="1e2d4-180">Visual Basic bunları işlenen iki dize olursa, art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-180">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="1e2d4-181">Birleştirme sonucu art arda iki işlenen bir içeriğini oluşan tek bir dize temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-181">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="1e2d4-182">İşlenen karma türlerini olursa, sonuç olarak ayarına bağlıdır [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1e2d4-182">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="1e2d4-183">Aşağıdaki örnek sonucu gösterilmektedir, `Option Strict` olan `On`.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-183">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 <span data-ttu-id="1e2d4-184">Aşağıdaki örnek sonucu gösterilmektedir, `Option Strict` olan `Off`.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-184">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 <span data-ttu-id="1e2d4-185">Belirsizliği ortadan kaldırmak için kullanmanız `&` operatörü yerine `+` birleştirme için.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-185">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e2d4-186">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e2d4-186">See Also</span></span>  
 [<span data-ttu-id="1e2d4-187">& İşleci</span><span class="sxs-lookup"><span data-stu-id="1e2d4-187">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [<span data-ttu-id="1e2d4-188">Birleştirme işleçleri</span><span class="sxs-lookup"><span data-stu-id="1e2d4-188">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="1e2d4-189">Aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="1e2d4-189">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="1e2d4-190">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="1e2d4-190">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="1e2d4-191">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="1e2d4-191">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="1e2d4-192">Visual Basic'de aritmetik işleçler</span><span class="sxs-lookup"><span data-stu-id="1e2d4-192">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="1e2d4-193">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="1e2d4-193">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
