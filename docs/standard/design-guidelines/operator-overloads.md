---
title: İşleç Aşırı Yüklemeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 893b7d1f76dfb059a0ddca77dfd8654812e9ae12
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289739"
---
# <a name="operator-overloads"></a><span data-ttu-id="c4860-102">İşleç Aşırı Yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="c4860-102">Operator Overloads</span></span>
<span data-ttu-id="c4860-103">İşleç aşırı yüklemeleri, çerçeve türlerinin yerleşik dil temelleri gibi görünmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="c4860-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="c4860-104">Bazı durumlarda izin verilen ve yararlı olsa da, işleç aşırı yüklemeleri dikkatle kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4860-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="c4860-105">Çerçeve tasarımcılarının basit yöntemler olması gereken işlemler için İşleçleri kullanmaya başladığı durumlar gibi, operatör aşırı yüklemesinde çok sayıda durum vardır.</span><span class="sxs-lookup"><span data-stu-id="c4860-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="c4860-106">Aşağıdaki kılavuzlar, işleç aşırı yüklemesini ne zaman ve nasıl kullanacağınızı belirlemenize yardımcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4860-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="c4860-107">❌İlkel (yerleşik) türler gibi olması gereken türler dışında işleç aşırı yüklemeleri tanımlamaktan KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="c4860-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="c4860-108">✔️, bir temel tür gibi olması gereken bir türde operatör aşırı yüklerini tanımlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="c4860-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="c4860-109">Örneğin, <xref:System.String?displayProperty=nameWithType> `operator==` ve `operator!=` tanımlı.</span><span class="sxs-lookup"><span data-stu-id="c4860-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="c4860-110">✔️, sayıları temsil eden yapılarda işleç aşırı yüklerini tanımlama (örneğin <xref:System.Decimal?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="c4860-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="c4860-111">❌Operatör aşırı yüklerini tanımlarken şirin olun.</span><span class="sxs-lookup"><span data-stu-id="c4860-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="c4860-112">İşleç aşırı yüklemesi, işlemin sonucunun anında daha açık olduğu durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4860-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="c4860-113">Örneğin, bir diğerinden çıkartabilir <xref:System.DateTime> `DateTime` ve bir alabilir <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="c4860-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="c4860-114">Ancak, iki veritabanı sorgusu UNION veya bir akışa yazmak için SHIFT işlecini kullanmak üzere mantıksal UNION işlecini kullanmak uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="c4860-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="c4860-115">❌İşlenenlerin en az biri aşırı yüklemeyi tanımlayan türde değilse, işleç aşırı yüklemeleri sağlamadığınız.</span><span class="sxs-lookup"><span data-stu-id="c4860-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="c4860-116">aşırı yükleme işleçlerini bir simetrik biçimde ✔️.</span><span class="sxs-lookup"><span data-stu-id="c4860-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="c4860-117">Örneğin, öğesini tekrar yüklüyorsanız, `operator==` öğesini de aşırı yükleyebilirsiniz `operator!=` .</span><span class="sxs-lookup"><span data-stu-id="c4860-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="c4860-118">Benzer şekilde, öğesini aşırı yüklüyorsanız, `operator<` ve de ' i de aşırı yükleyebilirsiniz `operator>` .</span><span class="sxs-lookup"><span data-stu-id="c4860-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="c4860-119">✔️, her bir aşırı yüklenmiş işlece karşılık gelen kolay adlara sahip Yöntemler sağlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="c4860-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="c4860-120">Birçok dil, işleç aşırı yüklemesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c4860-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="c4860-121">Bu nedenle, aşırı yükleme işleçleri 'nin eşdeğer işlevselliği sağlayan uygun bir etki alanına özgü ada sahip ikincil bir yöntem içermesi önerilir.</span><span class="sxs-lookup"><span data-stu-id="c4860-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="c4860-122">Aşağıdaki tabloda, işleçler ve ilgili kolay yöntem adları listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c4860-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="c4860-123">C# işleç simgesi</span><span class="sxs-lookup"><span data-stu-id="c4860-123">C# Operator Symbol</span></span>|<span data-ttu-id="c4860-124">Meta veri adı</span><span class="sxs-lookup"><span data-stu-id="c4860-124">Metadata Name</span></span>|<span data-ttu-id="c4860-125">Kolay ad</span><span class="sxs-lookup"><span data-stu-id="c4860-125">Friendly Name</span></span>|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a><span data-ttu-id="c4860-126">Aşırı yükleme Işleci = =</span><span class="sxs-lookup"><span data-stu-id="c4860-126">Overloading Operator ==</span></span>
 <span data-ttu-id="c4860-127">Aşırı yükleme `operator ==` oldukça karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="c4860-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="c4860-128">İşlecinin semantiğinin, gibi diğer birçok üye ile uyumlu olması gerekir <xref:System.Object.Equals%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c4860-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="c4860-129">Dönüşüm İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c4860-129">Conversion Operators</span></span>
 <span data-ttu-id="c4860-130">Dönüştürme işleçleri, bir türden diğerine dönüştürmeye izin veren birli işleçlerdir.</span><span class="sxs-lookup"><span data-stu-id="c4860-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="c4860-131">İşleçler, işlenen ya da dönüş türü üzerinde statik üye olarak tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4860-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="c4860-132">İki tür dönüştürme işleci vardır: örtük ve açık.</span><span class="sxs-lookup"><span data-stu-id="c4860-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="c4860-133">❌Bu dönüştürme, son kullanıcılar tarafından açıkça beklenmiyorsa, bir dönüştürme işleci sağlamayan.</span><span class="sxs-lookup"><span data-stu-id="c4860-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="c4860-134">❌Dönüştürme işleçlerini bir türün etki alanı dışında tanımlamayın.</span><span class="sxs-lookup"><span data-stu-id="c4860-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="c4860-135">Örneğin,, <xref:System.Int32> <xref:System.Double> ve <xref:System.Decimal> tüm sayısal türlerdir, ancak bu <xref:System.DateTime> değildir.</span><span class="sxs-lookup"><span data-stu-id="c4860-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="c4860-136">Bu nedenle, bir öğesine dönüştürmek için bir dönüştürme işleci olmamalıdır `Double(long)` `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="c4860-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="c4860-137">Böyle bir durumda bir Oluşturucu tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="c4860-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="c4860-138">❌Dönüştürme potansiyel olarak kayıplı ise örtük bir dönüştürme işleci sağlamaın.</span><span class="sxs-lookup"><span data-stu-id="c4860-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="c4860-139">Örneğin, öğesinden öğesine örtük bir dönüşüm olmaması gerekir, `Double` çünkü öğesinden `Int32` `Double` daha geniş bir Aralık vardır `Int32` .</span><span class="sxs-lookup"><span data-stu-id="c4860-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="c4860-140">Dönüştürme potansiyel olarak kayıplı olsa bile açık bir dönüştürme işleci sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4860-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="c4860-141">❌Örtülü kaynaklardan özel durumlar atamayın.</span><span class="sxs-lookup"><span data-stu-id="c4860-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="c4860-142">Son kullanıcıların ne olduğunu anlaması çok zordur, çünkü bir dönüştürmenin gerçekleştiğinden haberdar olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c4860-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="c4860-143"><xref:System.InvalidCastException?displayProperty=nameWithType>bir cast işlecine yapılan bir çağrı kayıplı dönüştürmeye neden olursa ve işlecin sözleşmesi kayıplı Dönüştürmelere izin vermezse throw ✔️.</span><span class="sxs-lookup"><span data-stu-id="c4860-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="c4860-144">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="c4860-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c4860-145">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="c4860-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c4860-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4860-146">See also</span></span>

- [<span data-ttu-id="c4860-147">Üye tasarımı yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c4860-147">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="c4860-148">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c4860-148">Framework Design Guidelines</span></span>](index.md)
