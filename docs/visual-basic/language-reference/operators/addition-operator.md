---
title: + İşleç (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 3187551afb7d25470f48dad894188766a811bb0a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701004"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b83b8-102">+ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b83b8-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="b83b8-103">İki sayı ekler veya sayısal bir ifadenin pozitif değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b83b8-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="b83b8-104">, İki dize ifadesini birleştirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b83b8-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b83b8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b83b8-105">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="b83b8-106">veya</span><span class="sxs-lookup"><span data-stu-id="b83b8-106">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="b83b8-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="b83b8-107">Parts</span></span>  
  
|<span data-ttu-id="b83b8-108">Terim</span><span class="sxs-lookup"><span data-stu-id="b83b8-108">Term</span></span>|<span data-ttu-id="b83b8-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="b83b8-109">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="b83b8-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b83b8-110">Required.</span></span> <span data-ttu-id="b83b8-111">Herhangi bir sayısal veya dize ifadesi.</span><span class="sxs-lookup"><span data-stu-id="b83b8-111">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="b83b8-112">@No__t-0 işleci negatif bir değer hesaplanmadığı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b83b8-112">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="b83b8-113">Herhangi bir sayısal veya dize ifadesi.</span><span class="sxs-lookup"><span data-stu-id="b83b8-113">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="b83b8-114">Sonuç</span><span class="sxs-lookup"><span data-stu-id="b83b8-114">Result</span></span>  
 <span data-ttu-id="b83b8-115">@No__t-0 ve `expression2` her ikisi de sayısal ise, sonuç Aritmetik toplamdır.</span><span class="sxs-lookup"><span data-stu-id="b83b8-115">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="b83b8-116">@No__t-0 yoksa, `+` işleci bir ifadenin değiştirilmemiş değeri için *birli* kimlik işleçtir.</span><span class="sxs-lookup"><span data-stu-id="b83b8-116">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="b83b8-117">Bu anlamda, işlem `expression1` ' ın işaretini korur, bu nedenle `expression1` negatifse sonuç negatif olur.</span><span class="sxs-lookup"><span data-stu-id="b83b8-117">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="b83b8-118">@No__t-0 ve `expression2` her iki dizise sonuç, değerlerinin birleştirilmesiyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="b83b8-118">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="b83b8-119">@No__t-0 ve `expression2` karma türdaysa, uygulanan eylem türlerine, içeriklerine ve [seçenek katı deyimin](../../../visual-basic/language-reference/statements/option-strict-statement.md)ayarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b83b8-119">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="b83b8-120">Daha fazla bilgi için "Notlar" içindeki tablolara bakın.</span><span class="sxs-lookup"><span data-stu-id="b83b8-120">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="b83b8-121">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="b83b8-121">Supported Types</span></span>  
 <span data-ttu-id="b83b8-122">İşaretsiz ve kayan nokta türleri ve `Decimal` ve `String` dahil tüm sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="b83b8-122">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b83b8-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b83b8-123">Remarks</span></span>  
 <span data-ttu-id="b83b8-124">Genellikle `+`, mümkün olduğunda aritmetik ekleme gerçekleştirir ve yalnızca her iki ifade de dizeler olduğunda art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="b83b8-124">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="b83b8-125">Hiçbir ifade bir `Object` değilse, Visual Basic aşağıdaki eylemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="b83b8-125">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="b83b8-126">İfadelerin veri türleri</span><span class="sxs-lookup"><span data-stu-id="b83b8-126">Data types of expressions</span></span>|<span data-ttu-id="b83b8-127">Derleyiciye göre eylem</span><span class="sxs-lookup"><span data-stu-id="b83b8-127">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="b83b8-128">Her iki ifade de sayısal veri türleridir (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single` ya da 0)</span><span class="sxs-lookup"><span data-stu-id="b83b8-128">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="b83b8-129">Ekleyemiyorum.</span><span class="sxs-lookup"><span data-stu-id="b83b8-129">Add.</span></span> <span data-ttu-id="b83b8-130">Sonuç veri türü, `expression1` ve `expression2` veri türleri için uygun bir sayısal türdür.</span><span class="sxs-lookup"><span data-stu-id="b83b8-130">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="b83b8-131">[Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.</span><span class="sxs-lookup"><span data-stu-id="b83b8-131">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="b83b8-132">Her iki ifade @no__t türündedir-0</span><span class="sxs-lookup"><span data-stu-id="b83b8-132">Both expressions are of type `String`</span></span>|<span data-ttu-id="b83b8-133">Karakter.</span><span class="sxs-lookup"><span data-stu-id="b83b8-133">Concatenate.</span></span>|  
|<span data-ttu-id="b83b8-134">Bir ifade sayısal bir veri türü ve diğeri bir dizedir</span><span class="sxs-lookup"><span data-stu-id="b83b8-134">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="b83b8-135">@No__t-0 ise-1 @no__t ve ardından bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b83b8-135">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="b83b8-136">@No__t-0 `Off` ise, `String` ' yi örtülü olarak `Double` ' e dönüştürün ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b83b8-136">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="b83b8-137">@No__t-0 ' ı `Double` ' e dönüştürülemiyorsa, <xref:System.InvalidCastException> özel durumu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b83b8-137">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="b83b8-138">Bir ifade sayısal bir veri türüdür ve diğeri [Nothing](../../../visual-basic/language-reference/nothing.md) değildir</span><span class="sxs-lookup"><span data-stu-id="b83b8-138">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="b83b8-139">@No__t-0 değeri sıfır olarak değer ile ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b83b8-139">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="b83b8-140">Bir ifade bir dizedir ve diğeri `Nothing` ' dır</span><span class="sxs-lookup"><span data-stu-id="b83b8-140">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="b83b8-141">Birleştir, `Nothing` ile "" olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b83b8-141">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="b83b8-142">Bir ifade `Object` ifadesiyse Visual Basic aşağıdaki eylemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="b83b8-142">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="b83b8-143">İfadelerin veri türleri</span><span class="sxs-lookup"><span data-stu-id="b83b8-143">Data types of expressions</span></span>|<span data-ttu-id="b83b8-144">Derleyiciye göre eylem</span><span class="sxs-lookup"><span data-stu-id="b83b8-144">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="b83b8-145">`Object` ifadesi sayısal bir değer ve diğeri ise sayısal bir veri türüdür</span><span class="sxs-lookup"><span data-stu-id="b83b8-145">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="b83b8-146">@No__t-0 ise-1 @no__t ve ardından bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b83b8-146">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="b83b8-147">@No__t-0 `Off` ise ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b83b8-147">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="b83b8-148">`Object` ifadesi sayısal bir değer ve diğeri tür `String` ' i barındırır</span><span class="sxs-lookup"><span data-stu-id="b83b8-148">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="b83b8-149">@No__t-0 ise-1 @no__t ve ardından bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b83b8-149">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="b83b8-150">@No__t-0 `Off` ise, `String` ' yi örtülü olarak `Double` ' e dönüştürün ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b83b8-150">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="b83b8-151">@No__t-0 ' ı `Double` ' e dönüştürülemiyorsa, <xref:System.InvalidCastException> özel durumu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b83b8-151">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="b83b8-152">`Object` ifadesi bir dize ve diğeri ise sayısal bir veri türüdür</span><span class="sxs-lookup"><span data-stu-id="b83b8-152">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="b83b8-153">@No__t-0 ise-1 @no__t ve ardından bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b83b8-153">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="b83b8-154">@No__t-0 `Off` ise, `Object` dizesini örtülü olarak `Double` ' e dönüştürün ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b83b8-154">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="b83b8-155">@No__t-0 dizesi `Double` ' e dönüştürülemiyorsa, <xref:System.InvalidCastException> özel durumu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b83b8-155">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="b83b8-156">`Object` ifadesi bir dize ve diğeri tür `String` ' i barındırır</span><span class="sxs-lookup"><span data-stu-id="b83b8-156">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="b83b8-157">@No__t-0 ise-1 @no__t ve ardından bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b83b8-157">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="b83b8-158">@No__t-0 `Off` ise, örtük olarak `Object` ' ye `String` ' e dönüştürün ve birleştirme.</span><span class="sxs-lookup"><span data-stu-id="b83b8-158">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="b83b8-159">Her iki ifade `Object` ifadeleridir, Visual Basic aşağıdaki eylemleri gerçekleştirir (yalnızca `Option Strict Off`).</span><span class="sxs-lookup"><span data-stu-id="b83b8-159">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="b83b8-160">İfadelerin veri türleri</span><span class="sxs-lookup"><span data-stu-id="b83b8-160">Data types of expressions</span></span>|<span data-ttu-id="b83b8-161">Derleyiciye göre eylem</span><span class="sxs-lookup"><span data-stu-id="b83b8-161">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="b83b8-162">@No__t-0 ifadeleri sayısal değerleri tutar</span><span class="sxs-lookup"><span data-stu-id="b83b8-162">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="b83b8-163">Ekleyemiyorum.</span><span class="sxs-lookup"><span data-stu-id="b83b8-163">Add.</span></span>|  
|<span data-ttu-id="b83b8-164">@No__t-0 ifadesi her ikisi de `String` türündedir</span><span class="sxs-lookup"><span data-stu-id="b83b8-164">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="b83b8-165">Karakter.</span><span class="sxs-lookup"><span data-stu-id="b83b8-165">Concatenate.</span></span>|  
|<span data-ttu-id="b83b8-166">Bir `Object` ifadesi sayısal bir değer ve diğeri bir dize tutar</span><span class="sxs-lookup"><span data-stu-id="b83b8-166">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="b83b8-167">@No__t-0 dizesini örtük olarak `Double` ' e dönüştürün ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b83b8-167">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="b83b8-168">@No__t-0 dizesi sayısal bir değere dönüştürülemiyorsa, bir <xref:System.InvalidCastException> özel durumu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b83b8-168">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="b83b8-169">@No__t-0 ifadesi [Nothing](../../../visual-basic/language-reference/nothing.md) veya <xref:System.DBNull> olarak değerlendirilirse, `+` işleci bunu "" değeriyle `String` olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b83b8-169">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b83b8-170">@No__t-0 işlecini kullandığınızda, ekleme veya dize birleştirme işleminin yapılıp yapılmayacağını belirleyemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b83b8-170">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="b83b8-171">Belirsizliği ortadan kaldırmak ve kendi kendine belgeleme kodu sağlamak için, birleştirmek üzere `&` işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b83b8-171">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b83b8-172">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="b83b8-172">Overloading</span></span>  
 <span data-ttu-id="b83b8-173">@No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b83b8-173">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b83b8-174">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b83b8-174">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b83b8-175">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b83b8-175">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b83b8-176">Örnek</span><span class="sxs-lookup"><span data-stu-id="b83b8-176">Example</span></span>  
 <span data-ttu-id="b83b8-177">Aşağıdaki örnek, sayı eklemek için `+` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b83b8-177">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="b83b8-178">İşlenenler her ikisi de sayısal ise, Visual Basic aritmetik sonucu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="b83b8-178">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="b83b8-179">Aritmetik sonuç, iki işlenenin toplamını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b83b8-179">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="b83b8-180">Dizeleri birleştirmek için `+` işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b83b8-180">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="b83b8-181">İşlenenler her iki dizise, Visual Basic bunları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="b83b8-181">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="b83b8-182">Birleştirme sonucu, iki işleneninin içeriğinden oluşan tek bir dizeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b83b8-182">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="b83b8-183">İşlenenler karışık türlerinise, sonuç, [Option Strict deyimin](../../../visual-basic/language-reference/statements/option-strict-statement.md)ayarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b83b8-183">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="b83b8-184">Aşağıdaki örnekte `Option Strict` `On` olduğunda sonuç gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b83b8-184">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="b83b8-185">Aşağıdaki örnekte `Option Strict` `Off` olduğunda sonuç gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b83b8-185">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="b83b8-186">Belirsizliği ortadan kaldırmak için, birleştirme için `+` yerine `&` işlecini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b83b8-186">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b83b8-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b83b8-187">See also</span></span>

- [<span data-ttu-id="b83b8-188">& İşleci</span><span class="sxs-lookup"><span data-stu-id="b83b8-188">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="b83b8-189">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="b83b8-189">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="b83b8-190">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="b83b8-190">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="b83b8-191">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="b83b8-191">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="b83b8-192">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="b83b8-192">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b83b8-193">Visual Basic aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="b83b8-193">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="b83b8-194">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="b83b8-194">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
