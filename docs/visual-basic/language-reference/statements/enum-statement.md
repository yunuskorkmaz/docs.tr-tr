---
title: Enum Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 7cac4d5bde9ec617a1877a0605dc6dbab67ddf7f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="21787-102">Enum Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21787-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="21787-103">Numaralandırma bildirir ve üyeleri değerleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="21787-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21787-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21787-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="21787-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="21787-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="21787-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="21787-106">Optional.</span></span> <span data-ttu-id="21787-107">Bu numaralandırma uygulamak öznitelikler listesi.</span><span class="sxs-lookup"><span data-stu-id="21787-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="21787-108">İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç ("`<`"ve"`>`").</span><span class="sxs-lookup"><span data-stu-id="21787-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="21787-109"><xref:System.FlagsAttribute> Öznitelik, numaralandırma örneği değerini birden fazla numaralandırma üyeleri içerebilir ve her üye numaralandırma değeri bit alanında temsil ettiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="21787-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="21787-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="21787-110">Optional.</span></span> <span data-ttu-id="21787-111">Bu numaralandırma hangi kod erişip belirtir.</span><span class="sxs-lookup"><span data-stu-id="21787-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="21787-112">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="21787-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="21787-113">Public</span><span class="sxs-lookup"><span data-stu-id="21787-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="21787-114">Protected</span><span class="sxs-lookup"><span data-stu-id="21787-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="21787-115">Friend</span><span class="sxs-lookup"><span data-stu-id="21787-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="21787-116">Private</span><span class="sxs-lookup"><span data-stu-id="21787-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="21787-117">Korumalı Friend</span><span class="sxs-lookup"><span data-stu-id="21787-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="21787-118">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="21787-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     <span data-ttu-id="21787-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="21787-119">Optional.</span></span> <span data-ttu-id="21787-120">Bu numaralandırma redeclares ve bir aynı adlı programlama öğesi ya da bir taban sınıf içinde aşırı yüklenmiş öğelerin gizler belirtir.</span><span class="sxs-lookup"><span data-stu-id="21787-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="21787-121">Belirleyebileceğiniz [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md) yalnızca numaralandırma, tüm üyeleri üzerinde değil.</span><span class="sxs-lookup"><span data-stu-id="21787-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="21787-122">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="21787-122">Required.</span></span> <span data-ttu-id="21787-123">Numaralandırma adı.</span><span class="sxs-lookup"><span data-stu-id="21787-123">Name of the enumeration.</span></span> <span data-ttu-id="21787-124">Geçerli adları hakkında daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="21787-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="21787-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="21787-125">Optional.</span></span> <span data-ttu-id="21787-126">Numaralandırma ve tüm üyelerini veri türü.</span><span class="sxs-lookup"><span data-stu-id="21787-126">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="21787-127">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="21787-127">Required.</span></span> <span data-ttu-id="21787-128">Bu deyim içinde bildirilen üye sabitleri listesi.</span><span class="sxs-lookup"><span data-stu-id="21787-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="21787-129">Birden çok üye bağımsız kaynak kodu satırlarda görünür.</span><span class="sxs-lookup"><span data-stu-id="21787-129">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="21787-130">Her `member` aşağıdaki söz dizimini ve bölümleri vardır: `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="21787-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="21787-131">Bölümü</span><span class="sxs-lookup"><span data-stu-id="21787-131">Part</span></span>|<span data-ttu-id="21787-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21787-132">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="21787-133">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="21787-133">Required.</span></span> <span data-ttu-id="21787-134">Bu üye adı.</span><span class="sxs-lookup"><span data-stu-id="21787-134">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="21787-135">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="21787-135">Optional.</span></span> <span data-ttu-id="21787-136">Derleme zamanında değerlendirilir ve bu üye için atanan ifade.</span><span class="sxs-lookup"><span data-stu-id="21787-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="21787-137">`End``Enum`</span><span class="sxs-lookup"><span data-stu-id="21787-137">`End` `Enum`</span></span>  
  
     <span data-ttu-id="21787-138">Sonlandırır `Enum` bloğu.</span><span class="sxs-lookup"><span data-stu-id="21787-138">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21787-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21787-139">Remarks</span></span>  
 <span data-ttu-id="21787-140">Bir mantıksal olarak birbiriyle ilişkili değişmeyen değerleri kümesi varsa, bunları bir numaralandırma birlikte tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21787-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="21787-141">Bu numaralandırma ve değerlerine kolay üyelerini için anlamlı adlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="21787-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="21787-142">Numaralandırma üyeleri kodunuzda birçok yerde kullanın.</span><span class="sxs-lookup"><span data-stu-id="21787-142">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="21787-143">Numaralandırmalar kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="21787-143">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="21787-144">Sırasını değiştirme veya numaraları yanlış yazmanız kaynaklanan hataları azaltır.</span><span class="sxs-lookup"><span data-stu-id="21787-144">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="21787-145">Gelecekte değerlerini değiştirmek kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="21787-145">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="21787-146">Hataları görülecektir olasılığını anlamına gelen kod okumak daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="21787-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="21787-147">İleriye dönük uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="21787-147">Ensures forward compatibility.</span></span> <span data-ttu-id="21787-148">Numaralandırmalar kullanırsanız, kodunuzu gelecekte birinin üyesi adlarına karşılık gelen değerleri değişirse başarısız daha az olasıdır.</span><span class="sxs-lookup"><span data-stu-id="21787-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="21787-149">Numaralandırma bir ad, bir temel alınan veri türü ve bir üye kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="21787-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="21787-150">Her üye bir sabiti temsil eder.</span><span class="sxs-lookup"><span data-stu-id="21787-150">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="21787-151">Sınıfı, yapısı, modül veya dışında herhangi bir yordam arabirimi düzeyinde bildirilen bir numaralandırma bir *üye numaralandırma*.</span><span class="sxs-lookup"><span data-stu-id="21787-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="21787-152">Sınıfı, yapısı, modül veya onu tanımlandığı arabirimi bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="21787-152">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="21787-153">Üye numaralandırmalar gelen yerden kendi sınıfı, yapısı, modül veya arabirimi içinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="21787-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="21787-154">Kod bir sınıf dışında yapısı veya modülü bu sınıf, yapı veya modül adını bir üye numaralandırmanın adıyla nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="21787-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="21787-155">Tam olarak nitelenmiş adlar ekleyerek kullanmaya gerek önleyebilirsiniz bir [içeri aktarmalar](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) kaynak dosyasına deyimi.</span><span class="sxs-lookup"><span data-stu-id="21787-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="21787-156">Sınıfı, yapısı, modül veya arabirim dışında ad alanı düzeyinde bildirilen numaralandırma göründüğü ad alanının bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="21787-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="21787-157">*Bildirimi bağlam* numaralandırma bir kaynak dosya, ad alanı, sınıf, yapısı, modül veya arabirimi olmalı ve bir yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="21787-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="21787-158">Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="21787-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="21787-159">Öznitelikler için sabit bir bütün olarak ancak üyeleri için ayrı ayrı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21787-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="21787-160">Bir öznitelik derlemenin meta verilerini bilgileri katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="21787-160">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="21787-161">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="21787-161">Data Type</span></span>  
 <span data-ttu-id="21787-162">`Enum` Deyimi veri türü bir numaralandırmanın bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21787-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="21787-163">Her üye sabit veri türünü alır.</span><span class="sxs-lookup"><span data-stu-id="21787-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="21787-164">Belirleyebileceğiniz `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, veya `UShort`.</span><span class="sxs-lookup"><span data-stu-id="21787-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="21787-165">Belirtmezseniz, `datatype` numaralandırma için her üye veri türünü alır. kendi `initializer`.</span><span class="sxs-lookup"><span data-stu-id="21787-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="21787-166">Her ikisini de belirtirseniz, `datatype` ve `initializer`, veri türü `initializer` dönüştürülebilir olmalıdır `datatype`.</span><span class="sxs-lookup"><span data-stu-id="21787-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="21787-167">Ne `datatype` ya da `initializer` varsa, veri türü için varsayılan `Integer`.</span><span class="sxs-lookup"><span data-stu-id="21787-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="21787-168">Üyeleri başlatma</span><span class="sxs-lookup"><span data-stu-id="21787-168">Initializing Members</span></span>  
 <span data-ttu-id="21787-169">`Enum` Deyimi içinde seçilen üyeleri içeriğini başlatma `memberlist`.</span><span class="sxs-lookup"><span data-stu-id="21787-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="21787-170">Kullandığınız `initializer` üyesine atanacak bir ifade sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="21787-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="21787-171">Belirtmezseniz, `initializer` bir üye için Visual Basic, sıfır ya da başlatır (ilk ise `member` içinde `memberlist`), ya da tek hemen önceki, daha büyük bir değere `member`.</span><span class="sxs-lookup"><span data-stu-id="21787-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="21787-172">Her sağlanan ifade `initializer` değişmez değerleri, önceden tanımlanmış diğer sabitleri ve zaten, önceki bu numaralandırma üyesi de dahil olmak üzere tanımlanan numaralandırma üyeleri herhangi bir bileşimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="21787-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="21787-173">Bu öğeler birleştirmek için aritmetik ve mantıksal işleçleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21787-173">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="21787-174">Değişkenleri veya işlevleri kullanamazsınız `initializer`.</span><span class="sxs-lookup"><span data-stu-id="21787-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="21787-175">Ancak, dönüşüm anahtar sözcükleri gibi kullanabilir `CByte` ve `CShort`.</span><span class="sxs-lookup"><span data-stu-id="21787-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="21787-176">Aynı zamanda `AscW` bir sabit ile çağırırsanız `String` veya `Char` derleme zamanında değerlendirilebilir beri bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="21787-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="21787-177">Numaralandırmalar kayan nokta değerlerine sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="21787-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="21787-178">Üye bir kayan nokta değer atanırsa ve `Option Strict` , bir derleyici hatası oluşursa ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="21787-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="21787-179">Varsa `Option Strict` kapalıysa, değeri için otomatik olarak dönüştürülür `Enum` türü.</span><span class="sxs-lookup"><span data-stu-id="21787-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="21787-180">Temel alınan veri türü için izin verilen aralığın bir üyesinin değerini aşması durumunda veya herhangi bir üyesi temel alınan veri türü tarafından izin verilen en yüksek değere başlatmak, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="21787-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="21787-181">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="21787-181">Modifiers</span></span>  
 <span data-ttu-id="21787-182">Sınıfı, yapısı, modül ve arabirim üye numaralandırmalar varsayılan genel erişim için.</span><span class="sxs-lookup"><span data-stu-id="21787-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="21787-183">Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21787-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="21787-184">Namespace üye numaralandırmalar varsayılan friend erişim.</span><span class="sxs-lookup"><span data-stu-id="21787-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="21787-185">Ortak, ancak özel veya korumalı erişim düzeylerine göre ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21787-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="21787-186">Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="21787-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="21787-187">Tüm numaralandırma üyeleri ortak erişimi vardır ve bunlar üzerinde hiçbir erişim değiştiricileri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="21787-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="21787-188">Numaralandırma daha kısıtlı erişim düzeyi varsa, ancak belirtilen numaralandırma erişim düzeyi önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="21787-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="21787-189">Varsayılan olarak, tüm numaralandırma türleri ve onların alanları sabitleri.</span><span class="sxs-lookup"><span data-stu-id="21787-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="21787-190">Bu nedenle `Shared`, `Static`, ve `ReadOnly` numaralandırma veya üyeleri bildirirken anahtar sözcükler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="21787-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="21787-191">Birden çok değerler atama</span><span class="sxs-lookup"><span data-stu-id="21787-191">Assigning Multiple Values</span></span>  
 <span data-ttu-id="21787-192">Numaralandırmalar genellikle birbirini dışlayan değerleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="21787-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="21787-193">Ekleyerek <xref:System.FlagsAttribute> özniteliğini `Enum` bildirimi, bunun yerine atayabilirsiniz birden çok değer numaralandırması örneğine.</span><span class="sxs-lookup"><span data-stu-id="21787-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="21787-194"><xref:System.FlagsAttribute> Özniteliği, numaralandırma bayrakları diğer bir deyişle, bir dizi bir bit alanı olarak değerlendirilmesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="21787-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="21787-195">Bunlar adlandırılır *Bitsel* numaralandırmalar.</span><span class="sxs-lookup"><span data-stu-id="21787-195">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="21787-196">Ne zaman bildirdiğiniz numaralandırma kullanarak <xref:System.FlagsAttribute> özniteliği öneririz, 2, 1, 2, 4, 8, 16 ve vb. tabanların değerlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="21787-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="21787-197">Ayrıca, "None" değeri 0 olan bir üyenin adını olmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="21787-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="21787-198">Ek yönergeler için bkz: <xref:System.FlagsAttribute> ve <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="21787-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21787-199">Örnek</span><span class="sxs-lookup"><span data-stu-id="21787-199">Example</span></span>  
 <span data-ttu-id="21787-200">Aşağıdaki örnekte nasıl kullanılacağını gösterir `Enum` deyimi.</span><span class="sxs-lookup"><span data-stu-id="21787-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="21787-201">Üye olarak adlandırılır Not `EggSizeEnum.Medium`, değil de `Medium`.</span><span class="sxs-lookup"><span data-stu-id="21787-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="21787-202">Örnek</span><span class="sxs-lookup"><span data-stu-id="21787-202">Example</span></span>  
 <span data-ttu-id="21787-203">Aşağıdaki örnekte yöntemi dışında `Egg` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="21787-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="21787-204">Bu nedenle, `EggSizeEnum` olarak tam olarak nitelenmiş `Egg.EggSizeEnum`.</span><span class="sxs-lookup"><span data-stu-id="21787-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="21787-205">Örnek</span><span class="sxs-lookup"><span data-stu-id="21787-205">Example</span></span>  
 <span data-ttu-id="21787-206">Aşağıdaki örnek kullanır `Enum` ilgili kümesini tanımlamak için deyimi adlı sabit değerleri.</span><span class="sxs-lookup"><span data-stu-id="21787-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="21787-207">Bu durumda, bir veritabanı için veri girişi formları tasarlama tercih edebileceğiniz renkleri değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="21787-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="21787-208">Örnek</span><span class="sxs-lookup"><span data-stu-id="21787-208">Example</span></span>  
 <span data-ttu-id="21787-209">Aşağıdaki örnek, pozitif ve negatif sayıları içeren değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="21787-209">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="21787-210">Örnek</span><span class="sxs-lookup"><span data-stu-id="21787-210">Example</span></span>  
 <span data-ttu-id="21787-211">Aşağıdaki örnekte, bir `As` yan tümcesini belirtmek için kullanılan `datatype` bir numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="21787-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="21787-212">Örnek</span><span class="sxs-lookup"><span data-stu-id="21787-212">Example</span></span>  
 <span data-ttu-id="21787-213">Aşağıdaki örnekte bir bit düzeyinde numaralandırma kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="21787-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="21787-214">Bit düzeyinde numaralandırması örneğine birden çok değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="21787-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="21787-215">`Enum` Bildirimi içerir <xref:System.FlagsAttribute> numaralandırma bayrakları kümesi olarak işlenebilir gösteren özniteliği.</span><span class="sxs-lookup"><span data-stu-id="21787-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a><span data-ttu-id="21787-216">Örnek</span><span class="sxs-lookup"><span data-stu-id="21787-216">Example</span></span>  
 <span data-ttu-id="21787-217">Aşağıdaki örnek, bir numaralandırma yineler.</span><span class="sxs-lookup"><span data-stu-id="21787-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="21787-218">Kullanır <xref:System.Enum.GetNames%2A> numaralandırma içinden üye adlarının dizisini almak için yöntemini ve <xref:System.Enum.GetValues%2A> üye değerleri dizisi alınamadı.</span><span class="sxs-lookup"><span data-stu-id="21787-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="21787-219">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21787-219">See Also</span></span>  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [<span data-ttu-id="21787-220">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="21787-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="21787-221">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="21787-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="21787-222">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="21787-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="21787-223">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="21787-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="21787-224">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="21787-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
