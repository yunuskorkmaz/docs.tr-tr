---
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
ms.openlocfilehash: bc31e4c66c64d891e3fffd809b7ae99b9c9a0520
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873453"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="46b06-102">+ İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46b06-102">+ Operator (Visual Basic)</span></span>

<span data-ttu-id="46b06-103">İki sayı ekler veya sayısal bir ifadenin pozitif değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="46b06-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="46b06-104">, İki dize ifadesini birleştirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46b06-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46b06-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46b06-105">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="46b06-106">veya</span><span class="sxs-lookup"><span data-stu-id="46b06-106">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="46b06-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="46b06-107">Parts</span></span>  
  
|<span data-ttu-id="46b06-108">Terim</span><span class="sxs-lookup"><span data-stu-id="46b06-108">Term</span></span>|<span data-ttu-id="46b06-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="46b06-109">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="46b06-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="46b06-110">Required.</span></span> <span data-ttu-id="46b06-111">Herhangi bir sayısal veya dize ifadesi.</span><span class="sxs-lookup"><span data-stu-id="46b06-111">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="46b06-112">`+`İşleç negatif bir değer hesaplanmadığı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="46b06-112">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="46b06-113">Herhangi bir sayısal veya dize ifadesi.</span><span class="sxs-lookup"><span data-stu-id="46b06-113">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="46b06-114">Sonuç</span><span class="sxs-lookup"><span data-stu-id="46b06-114">Result</span></span>  

 <span data-ttu-id="46b06-115">`expression1`Ve `expression2` her ikisi de ise, sonuç Aritmetik toplamdır.</span><span class="sxs-lookup"><span data-stu-id="46b06-115">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="46b06-116">Yoksa `expression2` , `+` işleci bir ifadenin değiştirilmemiş değeri için *birli* kimlik işleçtir.</span><span class="sxs-lookup"><span data-stu-id="46b06-116">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="46b06-117">Bu anlamda, işlem işaretini korur `expression1` , bu nedenle sonuç negatifse negatif olur `expression1` .</span><span class="sxs-lookup"><span data-stu-id="46b06-117">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="46b06-118">`expression1`Ve `expression2` her iki dizise sonuç, değerlerinin birleştirilmesiyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="46b06-118">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="46b06-119">`expression1`Ve `expression2` karışık türlerdir, uygulanan eylem türlerine, Içeriğine ve [katı deyimin seçeneğine](../statements/option-strict-statement.md)göre değişir.</span><span class="sxs-lookup"><span data-stu-id="46b06-119">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="46b06-120">Daha fazla bilgi için "Notlar" içindeki tablolara bakın.</span><span class="sxs-lookup"><span data-stu-id="46b06-120">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="46b06-121">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="46b06-121">Supported Types</span></span>  

 <span data-ttu-id="46b06-122">İşaretsiz ve kayan nokta türleri ve ve dahil olmak üzere tüm sayısal türler `Decimal` `String` .</span><span class="sxs-lookup"><span data-stu-id="46b06-122">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46b06-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46b06-123">Remarks</span></span>  

 <span data-ttu-id="46b06-124">Genel olarak, `+` mümkün olduğunda aritmetik ekleme gerçekleştirir ve yalnızca her iki ifade de dizeler olduğunda art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="46b06-124">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="46b06-125">Ne ifade yoksa `Object` Visual Basic aşağıdaki eylemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="46b06-125">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="46b06-126">İfadelerin veri türleri</span><span class="sxs-lookup"><span data-stu-id="46b06-126">Data types of expressions</span></span>|<span data-ttu-id="46b06-127">Derleyiciye göre eylem</span><span class="sxs-lookup"><span data-stu-id="46b06-127">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="46b06-128">Her iki ifade de sayısal veri türleridir ( `SByte` , `Byte` ,, `Short` `UShort` , `Integer` , `UInteger` , `Long` , `ULong` , `Decimal` , `Single` veya `Double` )</span><span class="sxs-lookup"><span data-stu-id="46b06-128">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="46b06-129">Ekle.</span><span class="sxs-lookup"><span data-stu-id="46b06-129">Add.</span></span> <span data-ttu-id="46b06-130">Sonuç veri türü ve veri türleri için uygun bir sayısal türdür `expression1` `expression2` .</span><span class="sxs-lookup"><span data-stu-id="46b06-130">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="46b06-131">[Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.</span><span class="sxs-lookup"><span data-stu-id="46b06-131">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="46b06-132">Her iki ifade de tür `String`</span><span class="sxs-lookup"><span data-stu-id="46b06-132">Both expressions are of type `String`</span></span>|<span data-ttu-id="46b06-133">Karakter.</span><span class="sxs-lookup"><span data-stu-id="46b06-133">Concatenate.</span></span>|  
|<span data-ttu-id="46b06-134">Bir ifade sayısal bir veri türü ve diğeri bir dizedir</span><span class="sxs-lookup"><span data-stu-id="46b06-134">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="46b06-135">`Option Strict`İse `On` , bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46b06-135">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="46b06-136">İse, öğesini `Option Strict` `Off` örtülü olarak öğesine dönüştürün `String` `Double` ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46b06-136">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="46b06-137">`String`Öğesine dönüştürülemiyorsa `Double` , bir <xref:System.InvalidCastException> özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="46b06-137">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="46b06-138">Bir ifade sayısal bir veri türüdür ve diğeri [Nothing](../nothing.md) değildir</span><span class="sxs-lookup"><span data-stu-id="46b06-138">One expression is a numeric data type, and the other is [Nothing](../nothing.md)</span></span>|<span data-ttu-id="46b06-139">`Nothing`Değerini, sıfıra kadar değerli şekilde ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46b06-139">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="46b06-140">Bir ifade bir dizedir ve diğeri `Nothing`</span><span class="sxs-lookup"><span data-stu-id="46b06-140">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="46b06-141">"" İle birlikte Birleştir `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="46b06-141">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="46b06-142">Bir ifade bir `Object` ifadesiyse, Visual Basic aşağıdaki eylemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="46b06-142">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="46b06-143">İfadelerin veri türleri</span><span class="sxs-lookup"><span data-stu-id="46b06-143">Data types of expressions</span></span>|<span data-ttu-id="46b06-144">Derleyiciye göre eylem</span><span class="sxs-lookup"><span data-stu-id="46b06-144">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="46b06-145">`Object` ifade sayısal bir değer ve diğeri ise sayısal bir veri türü tutar</span><span class="sxs-lookup"><span data-stu-id="46b06-145">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="46b06-146">`Option Strict`İse `On` , bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46b06-146">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="46b06-147">`Option Strict`İse `Off` , ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46b06-147">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="46b06-148">`Object` ifade bir sayısal değer ve diğeri tür `String`</span><span class="sxs-lookup"><span data-stu-id="46b06-148">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="46b06-149">`Option Strict`İse `On` , bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46b06-149">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="46b06-150">İse, öğesini `Option Strict` `Off` örtülü olarak öğesine dönüştürün `String` `Double` ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46b06-150">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="46b06-151">`String`Öğesine dönüştürülemiyorsa `Double` , bir <xref:System.InvalidCastException> özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="46b06-151">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="46b06-152">`Object` ifade bir dize tutar ve diğeri sayısal bir veri türü</span><span class="sxs-lookup"><span data-stu-id="46b06-152">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="46b06-153">`Option Strict`İse `On` , bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46b06-153">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="46b06-154">`Option Strict`İse `Off` , dizeyi örtük olarak `Object` öğesine dönüştürün `Double` ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46b06-154">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="46b06-155">Dize `Object` öğesine dönüştürülemiyorsa `Double` , bir <xref:System.InvalidCastException> özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="46b06-155">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="46b06-156">`Object` ifade bir dizeyi ve diğeri türü tutar `String`</span><span class="sxs-lookup"><span data-stu-id="46b06-156">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="46b06-157">`Option Strict`İse `On` , bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46b06-157">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="46b06-158">`Option Strict`İse `Off` , örtülü olarak Dönüştür `Object` `String` ve birleştir.</span><span class="sxs-lookup"><span data-stu-id="46b06-158">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="46b06-159">Her iki ifade de `Object` ifadeleridir, Visual Basic aşağıdaki eylemleri alır ( `Option Strict Off` yalnızca).</span><span class="sxs-lookup"><span data-stu-id="46b06-159">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="46b06-160">İfadelerin veri türleri</span><span class="sxs-lookup"><span data-stu-id="46b06-160">Data types of expressions</span></span>|<span data-ttu-id="46b06-161">Derleyiciye göre eylem</span><span class="sxs-lookup"><span data-stu-id="46b06-161">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="46b06-162">Her iki `Object` ifade de sayısal değerleri tutar</span><span class="sxs-lookup"><span data-stu-id="46b06-162">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="46b06-163">Ekle.</span><span class="sxs-lookup"><span data-stu-id="46b06-163">Add.</span></span>|  
|<span data-ttu-id="46b06-164">Her iki `Object` ifade de tür `String`</span><span class="sxs-lookup"><span data-stu-id="46b06-164">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="46b06-165">Karakter.</span><span class="sxs-lookup"><span data-stu-id="46b06-165">Concatenate.</span></span>|  
|<span data-ttu-id="46b06-166">Bir `Object` ifade sayısal bir değer ve diğeri bir dize tutar</span><span class="sxs-lookup"><span data-stu-id="46b06-166">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="46b06-167">Dizeyi örtük olarak `Object` öğesine dönüştürün `Double` ve ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46b06-167">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="46b06-168">Dize `Object` sayısal bir değere dönüştürülemiyorsa, bir <xref:System.InvalidCastException> özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="46b06-168">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="46b06-169">Her iki `Object` ifade de [Nothing](../nothing.md) olarak değerlendirilirse <xref:System.DBNull> , `+` işleci bunu `String` "" değeri ile bir olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="46b06-169">If either `Object` expression evaluates to [Nothing](../nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46b06-170">`+`İşlecini kullandığınızda, ekleme veya dize birleştirme işleminin yapılıp yapılmayacağını belirleyemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46b06-170">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="46b06-171">`&`Belirsizliği ortadan kaldırmak ve kendi kendine belgeleme kodu sağlamak için birleştirme işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="46b06-171">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="46b06-172">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="46b06-172">Overloading</span></span>  

 <span data-ttu-id="46b06-173">`+`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="46b06-173">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="46b06-174">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="46b06-174">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="46b06-175">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="46b06-175">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="46b06-176">Örnek</span><span class="sxs-lookup"><span data-stu-id="46b06-176">Example</span></span>  

 <span data-ttu-id="46b06-177">Aşağıdaki örnek, `+` sayı eklemek için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="46b06-177">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="46b06-178">İşlenenler her ikisi de sayısal ise, Visual Basic aritmetik sonucu hesaplar.</span><span class="sxs-lookup"><span data-stu-id="46b06-178">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="46b06-179">Aritmetik sonuç, iki işlenenin toplamını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="46b06-179">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="46b06-180">Ayrıca, `+` dizeleri birleştirmek için işlecini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46b06-180">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="46b06-181">İşlenenler her iki dizise, Visual Basic bunları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="46b06-181">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="46b06-182">Birleştirme sonucu, iki işleneninin içeriğinden oluşan tek bir dizeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="46b06-182">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="46b06-183">İşlenenler karışık türlerinise, sonuç, [Option Strict deyimin](../statements/option-strict-statement.md)ayarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="46b06-183">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="46b06-184">Aşağıdaki örnek, olduğu zaman sonucunu gösterir `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="46b06-184">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="46b06-185">Aşağıdaki örnek, olduğu zaman sonucunu gösterir `Option Strict` `Off` .</span><span class="sxs-lookup"><span data-stu-id="46b06-185">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="46b06-186">Belirsizliği ortadan kaldırmak için, `&` birleştirmek yerine işlecini kullanmanız gerekir `+` .</span><span class="sxs-lookup"><span data-stu-id="46b06-186">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b06-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46b06-187">See also</span></span>

- [<span data-ttu-id="46b06-188">& Işleci</span><span class="sxs-lookup"><span data-stu-id="46b06-188">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="46b06-189">Birleştirme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="46b06-189">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="46b06-190">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="46b06-190">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="46b06-191">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="46b06-191">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="46b06-192">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="46b06-192">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="46b06-193">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="46b06-193">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="46b06-194">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="46b06-194">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
