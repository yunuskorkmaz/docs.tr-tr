---
title: Genişletme ve Daraltma Dönüşümleri
ms.date: 07/20/2015
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
ms.openlocfilehash: c0e10f5593ce5c81002233516444e415571541f3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058540"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a><span data-ttu-id="bb346-102">Genişletme ve Daraltma Dönüşümleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb346-102">Widening and Narrowing Conversions (Visual Basic)</span></span>

<span data-ttu-id="bb346-103">Tür dönüştürmesinin sonucu, dönüştürme sonucunun hedef veri türünün aralığı içinde olup olmadığı konusunda önemli bir noktadır.</span><span class="sxs-lookup"><span data-stu-id="bb346-103">An important consideration with a type conversion is whether the result of the conversion is within the range of the destination data type.</span></span>  
  
 <span data-ttu-id="bb346-104">*Genişleyen dönüştürme* bir değeri, özgün verilerin olası bir değeri için izin verebilecek bir veri türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="bb346-104">A *widening conversion* changes a value to a data type that can allow for any possible value of the original data.</span></span>  <span data-ttu-id="bb346-105">Genişleyen dönüştürmeler kaynak değeri korur, ancak temsilini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="bb346-105">Widening conversions preserve the source value but can change its representation.</span></span> <span data-ttu-id="bb346-106">Bu, bir integral türünden `Decimal` veya ' den ' ye dönüştürürseniz oluşur `Char` `String` .</span><span class="sxs-lookup"><span data-stu-id="bb346-106">This occurs if you convert from an integral type to `Decimal`, or from `Char` to `String`.</span></span>  
  
 <span data-ttu-id="bb346-107">*Daraltma dönüştürmesi* bir değeri, olası değerlerden bazılarını tutabilecek bir veri türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="bb346-107">A *narrowing conversion* changes a value to a data type that might not be able to hold some of the possible values.</span></span> <span data-ttu-id="bb346-108">Örneğin, bir tamsayı türüne dönüştürüldüğünde kesirli değer yuvarlanır ve dönüştürülecek sayısal bir tür `Boolean` ya da değerine düşürülür `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="bb346-108">For example, a fractional value is rounded when it is converted to an integral type, and a numeric type being converted to `Boolean` is reduced to either `True` or `False`.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="bb346-109">Dönüştürmeleri Genişletme</span><span class="sxs-lookup"><span data-stu-id="bb346-109">Widening Conversions</span></span>  

 <span data-ttu-id="bb346-110">Aşağıdaki tabloda, standart genişletme dönüştürmeleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bb346-110">The following table shows the standard widening conversions.</span></span>  
  
|<span data-ttu-id="bb346-111">Veri türü</span><span class="sxs-lookup"><span data-stu-id="bb346-111">Data type</span></span>|<span data-ttu-id="bb346-112">Widens-veri türleri <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="bb346-112">Widens to data types <sup>1</sup></span></span>|  
|---|---|  
|[<span data-ttu-id="bb346-113">SByte</span><span class="sxs-lookup"><span data-stu-id="bb346-113">SByte</span></span>](../../../language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="bb346-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="bb346-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="bb346-115">Bayt</span><span class="sxs-lookup"><span data-stu-id="bb346-115">Byte</span></span>](../../../language-reference/data-types/byte-data-type.md)|<span data-ttu-id="bb346-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="bb346-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="bb346-117">Kısadır</span><span class="sxs-lookup"><span data-stu-id="bb346-117">Short</span></span>](../../../language-reference/data-types/short-data-type.md)|<span data-ttu-id="bb346-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="bb346-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="bb346-119">UShort</span><span class="sxs-lookup"><span data-stu-id="bb346-119">UShort</span></span>](../../../language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="bb346-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="bb346-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="bb346-121">Tamsayı</span><span class="sxs-lookup"><span data-stu-id="bb346-121">Integer</span></span>](../../../language-reference/data-types/integer-data-type.md)|<span data-ttu-id="bb346-122">`Integer`, `Long` , `Decimal` , `Single` , `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bb346-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="bb346-123">UInteger</span><span class="sxs-lookup"><span data-stu-id="bb346-123">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="bb346-124">`UInteger`, `Long` , `ULong` , `Decimal` , `Single` , `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bb346-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="bb346-125">Kalacağını</span><span class="sxs-lookup"><span data-stu-id="bb346-125">Long</span></span>](../../../language-reference/data-types/long-data-type.md)|<span data-ttu-id="bb346-126">`Long`, `Decimal` , `Single` , `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bb346-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="bb346-127">'Tur</span><span class="sxs-lookup"><span data-stu-id="bb346-127">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="bb346-128">`ULong`, `Decimal` , `Single` , `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bb346-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="bb346-129">Kategori</span><span class="sxs-lookup"><span data-stu-id="bb346-129">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="bb346-130">`Decimal`, `Single` , `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="bb346-130">`Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="bb346-131">Tek</span><span class="sxs-lookup"><span data-stu-id="bb346-131">Single</span></span>](../../../language-reference/data-types/single-data-type.md)|<span data-ttu-id="bb346-132">`Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="bb346-132">`Single`, `Double`</span></span>|  
|[<span data-ttu-id="bb346-133">Çift</span><span class="sxs-lookup"><span data-stu-id="bb346-133">Double</span></span>](../../../language-reference/data-types/double-data-type.md)|`Double`|  
|<span data-ttu-id="bb346-134">Herhangi bir numaralandırılmış tür ([enum](../../../language-reference/statements/enum-statement.md))</span><span class="sxs-lookup"><span data-stu-id="bb346-134">Any enumerated type ([Enum](../../../language-reference/statements/enum-statement.md))</span></span>|<span data-ttu-id="bb346-135">Temel alınan integral türü ve temel alınan tür widens olan herhangi bir tür.</span><span class="sxs-lookup"><span data-stu-id="bb346-135">Its underlying integral type and any type to which the underlying type widens.</span></span>|  
|[<span data-ttu-id="bb346-136">Char</span><span class="sxs-lookup"><span data-stu-id="bb346-136">Char</span></span>](../../../language-reference/data-types/char-data-type.md)|<span data-ttu-id="bb346-137">`Char`, `String`</span><span class="sxs-lookup"><span data-stu-id="bb346-137">`Char`, `String`</span></span>|  
|<span data-ttu-id="bb346-138">`Char` dizide</span><span class="sxs-lookup"><span data-stu-id="bb346-138">`Char` array</span></span>|<span data-ttu-id="bb346-139">`Char` dizide `String`</span><span class="sxs-lookup"><span data-stu-id="bb346-139">`Char` array, `String`</span></span>|  
|<span data-ttu-id="bb346-140">Herhangi bir tür</span><span class="sxs-lookup"><span data-stu-id="bb346-140">Any type</span></span>|[<span data-ttu-id="bb346-141">Nesne</span><span class="sxs-lookup"><span data-stu-id="bb346-141">Object</span></span>](../../../language-reference/data-types/object-data-type.md)|  
|<span data-ttu-id="bb346-142">Türetilmiş herhangi bir tür</span><span class="sxs-lookup"><span data-stu-id="bb346-142">Any derived type</span></span>|<span data-ttu-id="bb346-143"><sup>3</sup>' ün türetildiği temel tür.</span><span class="sxs-lookup"><span data-stu-id="bb346-143">Any base type from which it is derived <sup>3</sup>.</span></span>|  
|<span data-ttu-id="bb346-144">Herhangi bir tür</span><span class="sxs-lookup"><span data-stu-id="bb346-144">Any type</span></span>|<span data-ttu-id="bb346-145">Uyguladığı herhangi bir arabirim.</span><span class="sxs-lookup"><span data-stu-id="bb346-145">Any interface it implements.</span></span>|  
|[<span data-ttu-id="bb346-146">Yapma</span><span class="sxs-lookup"><span data-stu-id="bb346-146">Nothing</span></span>](../../../language-reference/nothing.md)|<span data-ttu-id="bb346-147">Herhangi bir veri türü veya nesne türü.</span><span class="sxs-lookup"><span data-stu-id="bb346-147">Any data type or object type.</span></span>|  
  
 <span data-ttu-id="bb346-148"><sup>1</sup> tanım, her veri türü ise widens.</span><span class="sxs-lookup"><span data-stu-id="bb346-148"><sup>1</sup> By definition, every data type widens to itself.</span></span>  
  
 <span data-ttu-id="bb346-149"><sup>2</sup> ,,, `Integer` `UInteger` veya ile arasındaki dönüşümler `Long` `ULong` `Decimal` `Single` `Double` duyarlık kaybına neden olabilir, ancak hiçbir şekilde büyüklük kaybı olmaz.</span><span class="sxs-lookup"><span data-stu-id="bb346-149"><sup>2</sup> Conversions from `Integer`, `UInteger`, `Long`, `ULong`, or `Decimal` to `Single` or `Double` might result in loss of precision, but never in loss of magnitude.</span></span> <span data-ttu-id="bb346-150">Bu anlamda bilgi kaybı yoktur.</span><span class="sxs-lookup"><span data-stu-id="bb346-150">In this sense they do not incur information loss.</span></span>  
  
 <span data-ttu-id="bb346-151"><sup>3</sup> bu, türetilmiş bir türden bir dönüştürmenin temel türlerinden birine dönüştürülmesinin genişleyen olduğunu ortaya çıkarmayabilir.</span><span class="sxs-lookup"><span data-stu-id="bb346-151"><sup>3</sup> It might seem surprising that a conversion from a derived type to one of its base types is widening.</span></span> <span data-ttu-id="bb346-152">Gerekçe, türetilmiş türün temel türün tüm üyelerini içermesinden dolayı temel türün bir örneği olarak nitelendirir.</span><span class="sxs-lookup"><span data-stu-id="bb346-152">The justification is that the derived type contains all the members of the base type, so it qualifies as an instance of the base type.</span></span> <span data-ttu-id="bb346-153">Ters yönde, temel tür türetilmiş tür tarafından tanımlanan yeni üyeleri içermez.</span><span class="sxs-lookup"><span data-stu-id="bb346-153">In the opposite direction, the base type does not contain any new members defined by the derived type.</span></span>  
  
 <span data-ttu-id="bb346-154">Genişletme dönüştürmeleri her zaman çalışma zamanında başarılı olur ve veri kaybına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="bb346-154">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="bb346-155">Bağımsız olarak, [katı deyimin](../../../language-reference/statements/option-strict-statement.md) tür denetleme anahtarını veya olarak ayarlamadığını örtülü olarak yapabilirsiniz `On` `Off` .</span><span class="sxs-lookup"><span data-stu-id="bb346-155">You can always perform them implicitly, whether the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) sets the type checking switch to `On` or to `Off`.</span></span>  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="bb346-156">Daraltma dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="bb346-156">Narrowing Conversions</span></span>  

 <span data-ttu-id="bb346-157">Standart daraltma dönüştürmeleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="bb346-157">The standard narrowing conversions include the following:</span></span>  
  
- <span data-ttu-id="bb346-158">Yukarıdaki tabloda genişleyen dönüştürmelerin ters yönleri (her tür widens kendisi hariç)</span><span class="sxs-lookup"><span data-stu-id="bb346-158">The reverse directions of the widening conversions in the preceding table (except that every type widens to itself)</span></span>  
  
- <span data-ttu-id="bb346-159">[Boolean](../../../language-reference/data-types/boolean-data-type.md) ve herhangi bir sayısal tür arasındaki iki yönde dönüştürme</span><span class="sxs-lookup"><span data-stu-id="bb346-159">Conversions in either direction between [Boolean](../../../language-reference/data-types/boolean-data-type.md) and any numeric type</span></span>  
  
- <span data-ttu-id="bb346-160">Herhangi bir sayısal türden herhangi bir numaralandırılmış türe ( `Enum` ) dönüştürme</span><span class="sxs-lookup"><span data-stu-id="bb346-160">Conversions from any numeric type to any enumerated type (`Enum`)</span></span>  
  
- <span data-ttu-id="bb346-161">[Dize](../../../language-reference/data-types/string-data-type.md) ile herhangi bir sayısal tür, `Boolean` ya da [Tarih](../../../language-reference/data-types/date-data-type.md) arasındaki yönde dönüşümler</span><span class="sxs-lookup"><span data-stu-id="bb346-161">Conversions in either direction between [String](../../../language-reference/data-types/string-data-type.md) and any numeric type, `Boolean`, or [Date](../../../language-reference/data-types/date-data-type.md)</span></span>  
  
- <span data-ttu-id="bb346-162">Veri türünden veya nesne türünden türetilmiş bir türe dönüşümler</span><span class="sxs-lookup"><span data-stu-id="bb346-162">Conversions from a data type or object type to a type derived from it</span></span>  
  
 <span data-ttu-id="bb346-163">Daraltma dönüştürmeleri her zaman çalışma zamanında başarılı olmaz ve veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="bb346-163">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="bb346-164">Hedef veri türü dönüştürülürken değeri alamadıysanız bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="bb346-164">An error occurs if the destination data type cannot receive the value being converted.</span></span> <span data-ttu-id="bb346-165">Örneğin, sayısal bir dönüştürme taşmaya neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="bb346-165">For example, a numeric conversion can result in an overflow.</span></span> <span data-ttu-id="bb346-166">[Kesin ifade](../../../language-reference/statements/option-strict-statement.md) tür denetimi olarak ayarlarsa, derleyici daraltma dönüştürmelerini örtülü olarak gerçekleştirmenize izin vermez `Off` .</span><span class="sxs-lookup"><span data-stu-id="bb346-166">The compiler does not allow you to perform narrowing conversions implicitly unless the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) sets the type checking switch to `Off`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb346-167">Daraltma dönüştürme hatası, bir `For Each…Next` koleksiyondaki öğelerden döngü denetim değişkenine dönüşümler için bastırılır.</span><span class="sxs-lookup"><span data-stu-id="bb346-167">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="bb346-168">Daha fazla bilgi ve örnek için, her biri Için içindeki "dönüştürmeleri daraltma" bölümüne bakın [... Sonraki Ifade](../../../language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bb346-168">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>  
  
### <a name="when-to-use-narrowing-conversions"></a><span data-ttu-id="bb346-169">Daraltma dönüştürmelerinde ne zaman kullanılır?</span><span class="sxs-lookup"><span data-stu-id="bb346-169">When to Use Narrowing Conversions</span></span>  

 <span data-ttu-id="bb346-170">Kaynak değerin hata veya veri kaybı olmadan hedef veri türüne dönüştürülebileceğini bildiğiniz zaman bir daraltma dönüştürmesi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="bb346-170">You use a narrowing conversion when you know the source value can be converted to the destination data type without error or data loss.</span></span> <span data-ttu-id="bb346-171">Örneğin, `String` "true" veya "false" içeren bir bilginiz varsa, `CBool` bunu öğesine dönüştürmek için anahtar sözcüğünü kullanabilirsiniz `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="bb346-171">For example, if you have a `String` that you know contains either "True" or "False," you can use the `CBool` keyword to convert it to `Boolean`.</span></span>  
  
## <a name="exceptions-during-conversion"></a><span data-ttu-id="bb346-172">Dönüştürme sırasında özel durumlar</span><span class="sxs-lookup"><span data-stu-id="bb346-172">Exceptions During Conversion</span></span>  

 <span data-ttu-id="bb346-173">Genişletme dönüştürmeleri her zaman başarılı olduğundan, özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="bb346-173">Because widening conversions always succeed, they do not throw exceptions.</span></span> <span data-ttu-id="bb346-174">Daraltma dönüştürmeleri, başarısız olduğunda, genellikle aşağıdaki özel durumları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bb346-174">Narrowing conversions, when they fail, most commonly throw the following exceptions:</span></span>  
  
- <span data-ttu-id="bb346-175"><xref:System.InvalidCastException> — iki tür arasında dönüştürme tanımlanmazsa</span><span class="sxs-lookup"><span data-stu-id="bb346-175"><xref:System.InvalidCastException> — if no conversion is defined between the two types</span></span>  
  
- <span data-ttu-id="bb346-176"><xref:System.OverflowException> — (yalnızca integral türleri) dönüştürülen değer hedef türü için çok büyükse</span><span class="sxs-lookup"><span data-stu-id="bb346-176"><xref:System.OverflowException> — (integral types only) if the converted value is too large for the target type</span></span>  
  
 <span data-ttu-id="bb346-177">Bir sınıf veya yapı, bu sınıfa veya yapıya dönüştürme işleci olarak kullanılmak üzere bir [CType işlevi](../../../language-reference/functions/ctype-function.md) tanımlıyorsa, `CType` uygun bir özel durum oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="bb346-177">If a class or structure defines a [CType Function](../../../language-reference/functions/ctype-function.md) to serve as a conversion operator to or from that class or structure, that `CType` can throw any exception it deems appropriate.</span></span> <span data-ttu-id="bb346-178">Ayrıca, `CType` Visual Basic işlevleri veya .NET Framework yöntemleri çağırabilir ve bu da çeşitli özel durumlar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="bb346-178">In addition, that `CType` might call Visual Basic functions or .NET Framework methods, which in turn could throw a variety of exceptions.</span></span>  
  
## <a name="changes-during-reference-type-conversions"></a><span data-ttu-id="bb346-179">Başvuru türü dönüştürmeleri sırasında yapılan değişiklikler</span><span class="sxs-lookup"><span data-stu-id="bb346-179">Changes During Reference Type Conversions</span></span>  

 <span data-ttu-id="bb346-180">*Başvuru türünden* bir dönüştürme yalnızca işaretçiyi değere kopyalar.</span><span class="sxs-lookup"><span data-stu-id="bb346-180">A conversion from a *reference type* copies only the pointer to the value.</span></span> <span data-ttu-id="bb346-181">Değerin kendisi hiçbir şekilde kopyalanmaz veya değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="bb346-181">The value itself is neither copied nor changed in any way.</span></span> <span data-ttu-id="bb346-182">Değişebilir tek şey, işaretçiyi tutan değişkenin veri türüdür.</span><span class="sxs-lookup"><span data-stu-id="bb346-182">The only thing that can change is the data type of the variable holding the pointer.</span></span> <span data-ttu-id="bb346-183">Aşağıdaki örnekte, veri türü türetilmiş sınıftan taban sınıfına dönüştürülür, ancak her iki değişkenin de işaret eden nesnesi değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="bb346-183">In the following example, the data type is converted from the derived class to its base class, but the object that both variables now point to is unchanged.</span></span>  
  
```vb  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb346-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb346-184">See also</span></span>

- [<span data-ttu-id="bb346-185">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="bb346-185">Data Types</span></span>](index.md)
- [<span data-ttu-id="bb346-186">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="bb346-186">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="bb346-187">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="bb346-187">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="bb346-188">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="bb346-188">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="bb346-189">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="bb346-189">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="bb346-190">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="bb346-190">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="bb346-191">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="bb346-191">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="bb346-192">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="bb346-192">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
