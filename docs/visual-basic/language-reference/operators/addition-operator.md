---
description: 'Daha fazla bilgi edinin: + Işleci (Visual Basic)'
title: + Operatör
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
ms.openlocfilehash: 9a6517847945cb2edcbd97adac6a013498dde174
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700695"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="c089f-103">+ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c089f-103">+ Operator (Visual Basic)</span></span>

<span data-ttu-id="c089f-104">İki sayı ekler veya sayısal bir ifadenin pozitif değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c089f-104">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="c089f-105">, İki dize ifadesini birleştirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c089f-105">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c089f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c089f-106">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="c089f-107">veya</span><span class="sxs-lookup"><span data-stu-id="c089f-107">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="c089f-108">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c089f-108">Parts</span></span>  
  
|<span data-ttu-id="c089f-109">Süre</span><span class="sxs-lookup"><span data-stu-id="c089f-109">Term</span></span>|<span data-ttu-id="c089f-110">Tanım</span><span class="sxs-lookup"><span data-stu-id="c089f-110">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="c089f-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c089f-111">Required.</span></span> <span data-ttu-id="c089f-112">Herhangi bir sayısal veya dize ifadesi.</span><span class="sxs-lookup"><span data-stu-id="c089f-112">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="c089f-113">`+`İşleç negatif bir değer hesaplanmadığı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c089f-113">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="c089f-114">Herhangi bir sayısal veya dize ifadesi.</span><span class="sxs-lookup"><span data-stu-id="c089f-114">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="c089f-115">Sonuç</span><span class="sxs-lookup"><span data-stu-id="c089f-115">Result</span></span>  

 <span data-ttu-id="c089f-116">`expression1`Ve `expression2` her ikisi de ise, sonuç Aritmetik toplamdır.</span><span class="sxs-lookup"><span data-stu-id="c089f-116">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="c089f-117">Yoksa `expression2` , `+` işleci bir ifadenin değiştirilmemiş değeri için *birli* kimlik işleçtir.</span><span class="sxs-lookup"><span data-stu-id="c089f-117">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="c089f-118">Bu anlamda, işlem işaretini korur `expression1` , bu nedenle sonuç negatifse negatif olur `expression1` .</span><span class="sxs-lookup"><span data-stu-id="c089f-118">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="c089f-119">`expression1`Ve `expression2` her iki dizise sonuç, değerlerinin birleştirilmesiyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="c089f-119">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="c089f-120">`expression1`Ve `expression2` karışık türlerdir, uygulanan eylem türlerine, Içeriğine ve [katı deyimin seçeneğine](../statements/option-strict-statement.md)göre değişir.</span><span class="sxs-lookup"><span data-stu-id="c089f-120">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="c089f-121">Daha fazla bilgi için "Notlar" içindeki tablolara bakın.</span><span class="sxs-lookup"><span data-stu-id="c089f-121">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="c089f-122">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="c089f-122">Supported Types</span></span>  

 <span data-ttu-id="c089f-123">İşaretsiz ve kayan nokta türleri ve ve dahil olmak üzere tüm sayısal türler `Decimal` `String` .</span><span class="sxs-lookup"><span data-stu-id="c089f-123">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c089f-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c089f-124">Remarks</span></span>  

 <span data-ttu-id="c089f-125">Genel olarak, `+` mümkün olduğunda aritmetik ekleme gerçekleştirir ve yalnızca her iki ifade de dizeler olduğunda art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="c089f-125">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="c089f-126">Ne ifade yoksa `Object` Visual Basic aşağıdaki eylemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c089f-126">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="c089f-127">İfadelerin veri türleri</span><span class="sxs-lookup"><span data-stu-id="c089f-127">Data types of expressions</span></span>|<span data-ttu-id="c089f-128">Derleyiciye göre eylem</span><span class="sxs-lookup"><span data-stu-id="c089f-128">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="c089f-129">Her iki ifade de sayısal veri türleridir ( `SByte` , `Byte` ,, `Short` `UShort` , `Integer` , `UInteger` , `Long` , `ULong` , `Decimal` , `Single` veya `Double` )</span><span class="sxs-lookup"><span data-stu-id="c089f-129">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="c089f-130">Ekle.</span><span class="sxs-lookup"><span data-stu-id="c089f-130">Add.</span></span> <span data-ttu-id="c089f-131">Sonuç veri türü ve veri türleri için uygun bir sayısal türdür `expression1` `expression2` .</span><span class="sxs-lookup"><span data-stu-id="c089f-131">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="c089f-132">[Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.</span><span class="sxs-lookup"><span data-stu-id="c089f-132">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="c089f-133">Her iki ifade de tür `String`</span><span class="sxs-lookup"><span data-stu-id="c089f-133">Both expressions are of type `String`</span></span>|<span data-ttu-id="c089f-134">Karakter.</span><span class="sxs-lookup"><span data-stu-id="c089f-134">Concatenate.</span></span>|  
|<span data-ttu-id="c089f-135">Bir ifade sayısal bir veri türü ve diğeri bir dizedir</span><span class="sxs-lookup"><span data-stu-id="c089f-135">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="c089f-136">`Option Strict`İse `On` , bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c089f-136">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="c089f-137">İse, öğesini `Option Strict` `Off` örtülü olarak öğesine dönüştürün `String` `Double` ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c089f-137">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="c089f-138">`String`Öğesine dönüştürülemiyorsa `Double` , bir <xref:System.InvalidCastException> özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c089f-138">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="c089f-139">Bir ifade sayısal bir veri türüdür ve diğeri [Nothing](../nothing.md) değildir</span><span class="sxs-lookup"><span data-stu-id="c089f-139">One expression is a numeric data type, and the other is [Nothing](../nothing.md)</span></span>|<span data-ttu-id="c089f-140">`Nothing`Değerini, sıfıra kadar değerli şekilde ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c089f-140">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="c089f-141">Bir ifade bir dizedir ve diğeri `Nothing`</span><span class="sxs-lookup"><span data-stu-id="c089f-141">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="c089f-142">"" İle birlikte Birleştir `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="c089f-142">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="c089f-143">Bir ifade bir `Object` ifadesiyse, Visual Basic aşağıdaki eylemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c089f-143">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="c089f-144">İfadelerin veri türleri</span><span class="sxs-lookup"><span data-stu-id="c089f-144">Data types of expressions</span></span>|<span data-ttu-id="c089f-145">Derleyiciye göre eylem</span><span class="sxs-lookup"><span data-stu-id="c089f-145">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="c089f-146">`Object` ifade sayısal bir değer ve diğeri ise sayısal bir veri türü tutar</span><span class="sxs-lookup"><span data-stu-id="c089f-146">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="c089f-147">`Option Strict`İse `On` , bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c089f-147">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="c089f-148">`Option Strict`İse `Off` , ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c089f-148">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="c089f-149">`Object` ifade bir sayısal değer ve diğeri tür `String`</span><span class="sxs-lookup"><span data-stu-id="c089f-149">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="c089f-150">`Option Strict`İse `On` , bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c089f-150">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="c089f-151">İse, öğesini `Option Strict` `Off` örtülü olarak öğesine dönüştürün `String` `Double` ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c089f-151">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="c089f-152">`String`Öğesine dönüştürülemiyorsa `Double` , bir <xref:System.InvalidCastException> özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c089f-152">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="c089f-153">`Object` ifade bir dize tutar ve diğeri sayısal bir veri türü</span><span class="sxs-lookup"><span data-stu-id="c089f-153">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="c089f-154">`Option Strict`İse `On` , bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c089f-154">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="c089f-155">`Option Strict`İse `Off` , dizeyi örtük olarak `Object` öğesine dönüştürün `Double` ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c089f-155">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="c089f-156">Dize `Object` öğesine dönüştürülemiyorsa `Double` , bir <xref:System.InvalidCastException> özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c089f-156">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="c089f-157">`Object` ifade bir dizeyi ve diğeri türü tutar `String`</span><span class="sxs-lookup"><span data-stu-id="c089f-157">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="c089f-158">`Option Strict`İse `On` , bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c089f-158">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="c089f-159">`Option Strict`İse `Off` , örtülü olarak Dönüştür `Object` `String` ve birleştir.</span><span class="sxs-lookup"><span data-stu-id="c089f-159">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="c089f-160">Her iki ifade de `Object` ifadeleridir, Visual Basic aşağıdaki eylemleri alır ( `Option Strict Off` yalnızca).</span><span class="sxs-lookup"><span data-stu-id="c089f-160">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="c089f-161">İfadelerin veri türleri</span><span class="sxs-lookup"><span data-stu-id="c089f-161">Data types of expressions</span></span>|<span data-ttu-id="c089f-162">Derleyiciye göre eylem</span><span class="sxs-lookup"><span data-stu-id="c089f-162">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="c089f-163">Her iki `Object` ifade de sayısal değerleri tutar</span><span class="sxs-lookup"><span data-stu-id="c089f-163">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="c089f-164">Ekle.</span><span class="sxs-lookup"><span data-stu-id="c089f-164">Add.</span></span>|  
|<span data-ttu-id="c089f-165">Her iki `Object` ifade de tür `String`</span><span class="sxs-lookup"><span data-stu-id="c089f-165">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="c089f-166">Karakter.</span><span class="sxs-lookup"><span data-stu-id="c089f-166">Concatenate.</span></span>|  
|<span data-ttu-id="c089f-167">Bir `Object` ifade sayısal bir değer ve diğeri bir dize tutar</span><span class="sxs-lookup"><span data-stu-id="c089f-167">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="c089f-168">Dizeyi örtük olarak `Object` öğesine dönüştürün `Double` ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c089f-168">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="c089f-169">Dize `Object` sayısal bir değere dönüştürülemiyorsa, bir <xref:System.InvalidCastException> özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c089f-169">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="c089f-170">Her iki `Object` ifade de [Nothing](../nothing.md) olarak değerlendirilirse <xref:System.DBNull> , `+` işleci bunu `String` "" değeri ile bir olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c089f-170">If either `Object` expression evaluates to [Nothing](../nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c089f-171">`+`İşlecini kullandığınızda, ekleme veya dize birleştirme işleminin yapılıp yapılmayacağını belirleyemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c089f-171">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="c089f-172">`&`Belirsizliği ortadan kaldırmak ve kendi kendine belgeleme kodu sağlamak için birleştirme işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c089f-172">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c089f-173">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="c089f-173">Overloading</span></span>  

 <span data-ttu-id="c089f-174">`+`İşleç *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c089f-174">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c089f-175">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c089f-175">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c089f-176">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c089f-176">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c089f-177">Örnek</span><span class="sxs-lookup"><span data-stu-id="c089f-177">Example</span></span>  

 <span data-ttu-id="c089f-178">Aşağıdaki örnek, `+` sayı eklemek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c089f-178">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="c089f-179">İşlenenler her ikisi de sayısal ise, Visual Basic aritmetik sonucu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c089f-179">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="c089f-180">Aritmetik sonuç, iki işlenenin toplamını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c089f-180">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="c089f-181">Ayrıca, `+` dizeleri birleştirmek için işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c089f-181">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="c089f-182">İşlenenler her iki dizise, Visual Basic bunları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="c089f-182">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="c089f-183">Birleştirme sonucu, iki işleneninin içeriğinden oluşan tek bir dizeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c089f-183">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="c089f-184">İşlenenler karışık türlerinise, sonuç, [Option Strict deyimin](../statements/option-strict-statement.md)ayarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c089f-184">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="c089f-185">Aşağıdaki örnek, olduğu zaman sonucunu gösterir `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="c089f-185">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="c089f-186">Aşağıdaki örnek, olduğu zaman sonucunu gösterir `Option Strict` `Off` .</span><span class="sxs-lookup"><span data-stu-id="c089f-186">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="c089f-187">Belirsizliği ortadan kaldırmak için, `&` birleştirmek yerine işlecini kullanmanız gerekir `+` .</span><span class="sxs-lookup"><span data-stu-id="c089f-187">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c089f-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c089f-188">See also</span></span>

- [<span data-ttu-id="c089f-189">& Işleci</span><span class="sxs-lookup"><span data-stu-id="c089f-189">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="c089f-190">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c089f-190">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="c089f-191">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="c089f-191">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="c089f-192">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="c089f-192">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="c089f-193">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="c089f-193">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="c089f-194">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="c089f-194">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="c089f-195">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="c089f-195">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
