---
title: "İşleç aşırı yüklemeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1d17aa00ce551d951b0e178304632572abf592b6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="operator-overloads"></a><span data-ttu-id="2b604-102">İşleç aşırı yüklemeleri</span><span class="sxs-lookup"><span data-stu-id="2b604-102">Operator Overloads</span></span>
<span data-ttu-id="2b604-103">İşleç aşırı yüklemeleri yerleşik dil temelleri oldukları gibi görünmesi framework türü izin verir.</span><span class="sxs-lookup"><span data-stu-id="2b604-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>  
  
 <span data-ttu-id="2b604-104">İzin verilen ve bazı durumlarda yararlı olsa da, işlecin dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b604-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="2b604-105">Hangi İşleç aşırı yüklemesi, framework tasarımcıları işleçleri basit yöntemleri olmalıdır işlemleri için kullanılacak başladığında gibi kötüye birçok durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="2b604-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="2b604-106">Aşağıdaki yönergeler ne zaman ve nasıl İşleç aşırı yüklemesi kullanma karar vermenize yardımcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b604-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>  
  
 <span data-ttu-id="2b604-107">**KAÇININ x** gibi (yerleşik) ilkel türlerinde geliyor olmalıdır türlerinde dışında işleci aşırı tanımlama.</span><span class="sxs-lookup"><span data-stu-id="2b604-107">**X AVOID** defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>  
  
 <span data-ttu-id="2b604-108">**✓ DÜŞÜNÜN** gibi basit tür geliyor olmalıdır bir türdeki işlecin tanımlama.</span><span class="sxs-lookup"><span data-stu-id="2b604-108">**✓ CONSIDER** defining operator overloads in a type that should feel like a primitive type.</span></span>  
  
 <span data-ttu-id="2b604-109">Örneğin, <xref:System.String?displayProperty=nameWithType> sahip `operator==` ve `operator!=` tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="2b604-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>  
  
 <span data-ttu-id="2b604-110">**✓ YAPMAK** numaralarını temsil eden yapılar için işleç aşırı yüklemeleri tanımlayın (gibi <xref:System.Decimal?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="2b604-110">**✓ DO** define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="2b604-111">**X yok** işlecin tanımlarken şirin olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b604-111">**X DO NOT** be cute when defining operator overloads.</span></span>  
  
 <span data-ttu-id="2b604-112">İşleç aşırı yüklemesi işlemin sonucunu ne olacağını hemen göze olduğu durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b604-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="2b604-113">Örneğin, bir çıkarma yapabilmek için mantıklıdır <xref:System.DateTime> başka bir `DateTime` ve bir <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="2b604-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="2b604-114">Ancak, mantıksal birleşim işlecini bileşim iki veritabanı sorgularını kullanın ya da bir akışa yazmak üzere kaydırma işleci kullanmak için uygun değil.</span><span class="sxs-lookup"><span data-stu-id="2b604-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>  
  
 <span data-ttu-id="2b604-115">**X yok** işleci aşırı yüklemeler işlenen en az biri aşırı tanımlama türü olmadıkça sağlayın.</span><span class="sxs-lookup"><span data-stu-id="2b604-115">**X DO NOT** provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>  
  
 <span data-ttu-id="2b604-116">**✓ YAPMAK** bir simetrik şekilde işleçleri aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="2b604-116">**✓ DO** overload operators in a symmetric fashion.</span></span>  
  
 <span data-ttu-id="2b604-117">Örneğin, aşırı yükleme `operator==`, ayrıca aşırı `operator!=`.</span><span class="sxs-lookup"><span data-stu-id="2b604-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="2b604-118">Benzer şekilde, aşırı yükleme varsa `operator<`, ayrıca aşırı `operator>`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="2b604-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>  
  
 <span data-ttu-id="2b604-119">**✓ DÜŞÜNÜN** yöntemleri karşılık gelen kolay adlarla her aşırı yüklenmiş işleç sağlama.</span><span class="sxs-lookup"><span data-stu-id="2b604-119">**✓ CONSIDER** providing methods with friendly names that correspond to each overloaded operator.</span></span>  
  
 <span data-ttu-id="2b604-120">İşleç aşırı yüklemesi birçok dil desteklemez.</span><span class="sxs-lookup"><span data-stu-id="2b604-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="2b604-121">Bu nedenle, işleçleri aşırı yükleme türleri ikincil bir yöntem uygun bir etki alanına özgü adıyla eşdeğer işlevsellik sağlayan olmaması önerilir.</span><span class="sxs-lookup"><span data-stu-id="2b604-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>  
  
 <span data-ttu-id="2b604-122">Aşağıdaki tabloda işleçler ve karşılık gelen kolay yöntem adlarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="2b604-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>  
  
|<span data-ttu-id="2b604-123">C# işleç simgesi</span><span class="sxs-lookup"><span data-stu-id="2b604-123">C# Operator Symbol</span></span>|<span data-ttu-id="2b604-124">Meta veri adı</span><span class="sxs-lookup"><span data-stu-id="2b604-124">Metadata Name</span></span>|<span data-ttu-id="2b604-125">Kolay ad</span><span class="sxs-lookup"><span data-stu-id="2b604-125">Friendly Name</span></span>|  
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
  
### <a name="overloading-operator-"></a><span data-ttu-id="2b604-126">İşleç aşırı yüklemesi ==</span><span class="sxs-lookup"><span data-stu-id="2b604-126">Overloading Operator ==</span></span>  
 <span data-ttu-id="2b604-127">Aşırı yükleme `operator ==` oldukça karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="2b604-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="2b604-128">İşleci semantiği gibi birkaç diğer üyeleriyle uyumlu olması gereken <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2b604-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="conversion-operators"></a><span data-ttu-id="2b604-129">Dönüşüm İşleçleri</span><span class="sxs-lookup"><span data-stu-id="2b604-129">Conversion Operators</span></span>  
 <span data-ttu-id="2b604-130">Dönüştürme işleçleri bir türden diğerine dönüştürme izin birli işleçler şunlardır.</span><span class="sxs-lookup"><span data-stu-id="2b604-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="2b604-131">İşleçler statik üyeler işlenen ya da dönüş türü olarak tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b604-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="2b604-132">Dönüştürme işleçleri iki tür vardır: örtük ve açık.</span><span class="sxs-lookup"><span data-stu-id="2b604-132">There are two types of conversion operators: implicit and explicit.</span></span>  
  
 <span data-ttu-id="2b604-133">**X yok** tür dönüştürme son kullanıcılar tarafından açıkça görülmüyorsa bir dönüşüm işleci sağlayın.</span><span class="sxs-lookup"><span data-stu-id="2b604-133">**X DO NOT** provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>  
  
 <span data-ttu-id="2b604-134">**X yok** dönüşüm işleçleri dışında bir tür etki alanını tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2b604-134">**X DO NOT** define conversion operators outside of a type’s domain.</span></span>  
  
 <span data-ttu-id="2b604-135">Örneğin, <xref:System.Int32>, <xref:System.Double>, ve <xref:System.Decimal> tüm sayısal ancak türleridir <xref:System.DateTime> değil.</span><span class="sxs-lookup"><span data-stu-id="2b604-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="2b604-136">Bu nedenle, olmamalıdır dönüştürmek için hiçbir dönüştürme işleci bir `Double(long)` için bir `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="2b604-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="2b604-137">Bir oluşturucu, böyle bir durumda tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="2b604-137">A constructor is preferred in such a case.</span></span>  
  
 <span data-ttu-id="2b604-138">**X yok** dönüştürme olası kayıplı ise bir örtük dönüşüm işleci sağlayın.</span><span class="sxs-lookup"><span data-stu-id="2b604-138">**X DO NOT** provide an implicit conversion operator if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="2b604-139">Örneğin, olmamalıdır örtük bir dönüştürme `Double` için `Int32` çünkü `Double` daha geniş bir sahip `Int32`.</span><span class="sxs-lookup"><span data-stu-id="2b604-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="2b604-140">Dönüştürme olası kayıplı olsa bile bir açık dönüşüm işleci sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="2b604-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="2b604-141">**X yok** örtük atamaları özel durumlar atar.</span><span class="sxs-lookup"><span data-stu-id="2b604-141">**X DO NOT** throw exceptions from implicit casts.</span></span>  
  
 <span data-ttu-id="2b604-142">Neler olduğunu, bunların dönüştürme yer aldığı kullanan olmayabileceğinden anlamak son kullanıcılar için çok zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b604-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>  
  
 <span data-ttu-id="2b604-143">**✓ YAPMAK** throw <xref:System.InvalidCastException?displayProperty=nameWithType> atama işleci için bir çağrı sonuçları kayıplı dönüştürmede ve sözleşmenin işlecinin kayıplı dönüşümleri izin vermez.</span><span class="sxs-lookup"><span data-stu-id="2b604-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>  
  
 <span data-ttu-id="2b604-144">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="2b604-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2b604-145">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="2b604-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b604-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b604-146">See Also</span></span>  
 [<span data-ttu-id="2b604-147">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2b604-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="2b604-148">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2b604-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
