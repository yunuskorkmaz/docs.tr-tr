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
ms.openlocfilehash: fa97a374d4570e014222bf44844271b3394453da
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830077"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="46772-102">Enum Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46772-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="46772-103">Bir sabit listesi bildirir ve üyelerinin değerlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46772-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46772-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46772-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="46772-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="46772-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="46772-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46772-106">Optional.</span></span> <span data-ttu-id="46772-107">Bu sabit listesi için geçerli olan özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="46772-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="46772-108">İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraçlar içinde ("`<`"ve"`>`").</span><span class="sxs-lookup"><span data-stu-id="46772-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="46772-109"><xref:System.FlagsAttribute> Özniteliği örneği numaralandırma değerini birden fazla numaralandırma üyelerini içerebilir ve her üyesi bir bit alanı numaralandırma değeri temsil ettiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="46772-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="46772-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46772-110">Optional.</span></span> <span data-ttu-id="46772-111">Bu sabit listesi kod erişip belirtir.</span><span class="sxs-lookup"><span data-stu-id="46772-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="46772-112">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="46772-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="46772-113">Public</span><span class="sxs-lookup"><span data-stu-id="46772-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="46772-114">Protected</span><span class="sxs-lookup"><span data-stu-id="46772-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="46772-115">Friend</span><span class="sxs-lookup"><span data-stu-id="46772-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="46772-116">Private</span><span class="sxs-lookup"><span data-stu-id="46772-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="46772-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="46772-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="46772-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="46772-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     <span data-ttu-id="46772-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46772-119">Optional.</span></span> <span data-ttu-id="46772-120">Bu numaralandırma redeclares ve bir programlama aynı adlı bir öğeyi veya taban sınıfında aşırı yüklenmiş bir öğe kümesini gizler belirtir.</span><span class="sxs-lookup"><span data-stu-id="46772-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="46772-121">Belirtebileceğiniz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) yalnızca numaralandırma, tüm üyeleri üzerinde değil.</span><span class="sxs-lookup"><span data-stu-id="46772-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="46772-122">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="46772-122">Required.</span></span> <span data-ttu-id="46772-123">Sabit listesinin adı.</span><span class="sxs-lookup"><span data-stu-id="46772-123">Name of the enumeration.</span></span> <span data-ttu-id="46772-124">Geçerli adlar hakkında daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="46772-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="46772-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46772-125">Optional.</span></span> <span data-ttu-id="46772-126">Sabit listesi ve tüm üyeleri veri türü.</span><span class="sxs-lookup"><span data-stu-id="46772-126">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="46772-127">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="46772-127">Required.</span></span> <span data-ttu-id="46772-128">Bu deyiminde bildirilen üye sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="46772-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="46772-129">Birden çok üye bağımsız kaynak kod satırlarında görünür.</span><span class="sxs-lookup"><span data-stu-id="46772-129">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="46772-130">Her `member` aşağıdaki söz dizimini ve bölümleri vardır: `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="46772-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="46772-131">Bölümü</span><span class="sxs-lookup"><span data-stu-id="46772-131">Part</span></span>|<span data-ttu-id="46772-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46772-132">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="46772-133">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="46772-133">Required.</span></span> <span data-ttu-id="46772-134">Bu üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="46772-134">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="46772-135">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46772-135">Optional.</span></span> <span data-ttu-id="46772-136">Derleme zamanında değerlendirilir ve bu üye için atanan ifade.</span><span class="sxs-lookup"><span data-stu-id="46772-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="46772-137">`End``Enum`</span><span class="sxs-lookup"><span data-stu-id="46772-137">`End` `Enum`</span></span>  
  
     <span data-ttu-id="46772-138">Sonlandırır `Enum` blok.</span><span class="sxs-lookup"><span data-stu-id="46772-138">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46772-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46772-139">Remarks</span></span>  
 <span data-ttu-id="46772-140">Mantıksal olarak birbiriyle ilişkili değişmeyen değerlerini bir dizi varsa, bunları bir numaralandırmada birlikte tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46772-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="46772-141">Bu sabit listesi ve bunların değerlerini kolay üyelerini için anlamlı adlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="46772-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="46772-142">Daha sonra kodunuzda pek çok yerde numaralandırma üyelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46772-142">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="46772-143">Numaralandırmalar kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="46772-143">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="46772-144">Sırasını değiştirme ya da sayı yanlış yazmanız kaynaklanan hataları azaltır.</span><span class="sxs-lookup"><span data-stu-id="46772-144">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="46772-145">Değerleri gelecekte değiştirilmesini daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="46772-145">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="46772-146">Hataları görülecektir olasılığını olduğu anlamına gelir, daha kolay kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="46772-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="46772-147">İleriye dönük uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="46772-147">Ensures forward compatibility.</span></span> <span data-ttu-id="46772-148">Numaralandırmalar kullanırsanız, kodunuzu gelecekte birinin üyesi adlara karşılık gelen değerleri değişirse başarısız etkilenme olasılığı da düşer.</span><span class="sxs-lookup"><span data-stu-id="46772-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="46772-149">Bir numaralandırma bir ad, temel alınan bir veri türü ve bir üye kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="46772-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="46772-150">Her üye bir sabiti temsil eder.</span><span class="sxs-lookup"><span data-stu-id="46772-150">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="46772-151">Sınıfı, yapı, modül veya dışında herhangi bir yordam arabirimi düzeyinde bildirilen bir sabit listesidir bir *üye numaralandırması*.</span><span class="sxs-lookup"><span data-stu-id="46772-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="46772-152">Sınıfı, yapısı, modül veya onu bildiren arabirimin bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="46772-152">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="46772-153">Üye numaralandırmalar öğesinden herhangi bir yerde kendi sınıf, yapı, modül veya arabirimi içinde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="46772-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="46772-154">Kod bir sınıf dışında yapısını veya modülünü Bu sınıf, yapı veya modül adını bir üye sabit listesinin adıyla nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46772-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="46772-155">Tam olarak nitelenmiş adlar ekleyerek kullanmaya gerek kaçınabilirsiniz bir [içeri aktarmalar](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) bildirimi kaynak dosyası.</span><span class="sxs-lookup"><span data-stu-id="46772-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="46772-156">Ad alanı düzeyinde sınıf, yapı, modül veya arabirimi, dışında bildirilen bir numaralandırma göründüğü ad alanının bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="46772-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="46772-157">*Bildirim içeriğinin* numaralandırması bir kaynak dosyası, ad alanı, sınıf, yapı, modül veya arabirimi olması gerekir ve bir yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="46772-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="46772-158">Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="46772-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="46772-159">Öznitelikleri numaralandırması bir bütün olarak, ancak üyelerini tek tek uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46772-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="46772-160">Bir özniteliği derleme meta bilgileri katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="46772-160">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="46772-161">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="46772-161">Data Type</span></span>  
 <span data-ttu-id="46772-162">`Enum` Deyimi, veri türü bir numaralandırmanın bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46772-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="46772-163">Her üye, sabit listesinin veri türünü alır.</span><span class="sxs-lookup"><span data-stu-id="46772-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="46772-164">Belirtebileceğiniz `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, veya `UShort`.</span><span class="sxs-lookup"><span data-stu-id="46772-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="46772-165">Siz belirtmezseniz `datatype` sabit listesi için her üye veri türünü alır. kendi `initializer`.</span><span class="sxs-lookup"><span data-stu-id="46772-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="46772-166">Her ikisini de belirtirseniz `datatype` ve `initializer`, veri türü `initializer` dönüştürülebilmelidir `datatype`.</span><span class="sxs-lookup"><span data-stu-id="46772-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="46772-167">Kullanılmazsa `datatype` ya da `initializer` varsa, veri türü için varsayılan değerleri `Integer`.</span><span class="sxs-lookup"><span data-stu-id="46772-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="46772-168">Üyeleri başlatma</span><span class="sxs-lookup"><span data-stu-id="46772-168">Initializing Members</span></span>  
 <span data-ttu-id="46772-169">`Enum` Deyimi Seçili üyelerin içeriğini başlatmak `memberlist`.</span><span class="sxs-lookup"><span data-stu-id="46772-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="46772-170">Kullandığınız `initializer` üyesine atanmış bir ifade sağlamanız için.</span><span class="sxs-lookup"><span data-stu-id="46772-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="46772-171">Siz belirtmezseniz `initializer` bir üye için Visual Basic ya da sıfırdan başlatır (ilk ise `member` içinde `memberlist`), ya da tek hemen önceki ait olandan daha büyük bir değere `member`.</span><span class="sxs-lookup"><span data-stu-id="46772-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="46772-172">Her sağlanan ifade `initializer` değişmez değerleri, önceden tanımlanmış diğer sabitleri ve zaten, önceki bu sabit listesi üyesi de dahil olmak üzere tanımlanan numaralandırma üyeleri herhangi bir birleşimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="46772-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="46772-173">Bu öğeleri birleştirin, aritmetik ve mantıksal işleçlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46772-173">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="46772-174">Değişkenler veya işlevlerinde kullanılamaz `initializer`.</span><span class="sxs-lookup"><span data-stu-id="46772-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="46772-175">Bununla birlikte, dönüşüm anahtar sözcükleri gibi kullanabileceğiniz `CByte` ve `CShort`.</span><span class="sxs-lookup"><span data-stu-id="46772-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="46772-176">Ayrıca `AscW` bir sabit ile çağırırsanız `String` veya `Char` bağımsız değişkeni, derleme zamanında değerlendirilebilen olduğundan.</span><span class="sxs-lookup"><span data-stu-id="46772-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="46772-177">Numaralandırmalar, kayan nokta değerlerine sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="46772-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="46772-178">Üye bir kayan noktalı değere atanırsa ve `Option Strict` , bir derleyici hatası oluşursa ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="46772-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="46772-179">Varsa `Option Strict` kapalıysa, değer otomatik olarak dönüştürülür `Enum` türü.</span><span class="sxs-lookup"><span data-stu-id="46772-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="46772-180">Temel alınan veri türü için izin verilen aralık bir üyenin değerini aşarsa veya herhangi bir üyesi temel alınan veri türü tarafından izin verilen en yüksek değere başlatmak, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="46772-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="46772-181">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="46772-181">Modifiers</span></span>  
 <span data-ttu-id="46772-182">Sınıfı, yapı, modül ve arabirim üyesi numaralandırmalar varsayılan genel erişim için.</span><span class="sxs-lookup"><span data-stu-id="46772-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="46772-183">Erişim değiştiricileri ile kullanıcıların erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46772-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="46772-184">Namespace üye numaralandırmalar varsayılan'öğesine friend erişimi için.</span><span class="sxs-lookup"><span data-stu-id="46772-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="46772-185">Genel, ancak özel veya korumalı, erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46772-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="46772-186">Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="46772-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="46772-187">Tüm numaralandırma üyelerini genel erişimi vardır ve bunlar üzerinde herhangi bir erişim değiştiricileri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="46772-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="46772-188">Numaralandırma, daha kısıtlı bir erişim düzeyi varsa, ancak belirtilen numaralandırma erişim düzeyi önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="46772-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="46772-189">Varsayılan olarak, tüm numaralandırmalar türleridir ve onların alanları sabittir.</span><span class="sxs-lookup"><span data-stu-id="46772-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="46772-190">Bu nedenle `Shared`, `Static`, ve `ReadOnly` numaralandırma veya üyelerinin bildirirken, anahtar sözcükler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="46772-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="46772-191">Birden çok değer atama</span><span class="sxs-lookup"><span data-stu-id="46772-191">Assigning Multiple Values</span></span>  
 <span data-ttu-id="46772-192">Numaralandırmalar genellikle birbirini dışlayan değerleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="46772-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="46772-193">Ekleyerek <xref:System.FlagsAttribute> özniteliğini `Enum` bildirimi, bunun yerine atayabilirsiniz birden çok değer numaralandırma örneği.</span><span class="sxs-lookup"><span data-stu-id="46772-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="46772-194"><xref:System.FlagsAttribute> Özniteliği sabit listesi flags diğer bir deyişle, bir dizi bir bit alanı olarak değerlendirilmesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="46772-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="46772-195">Bunlar adlandırılır *bit düzeyinde* numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="46772-195">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="46772-196">Kullanarak bir numaralandırma bildirdiğinizde <xref:System.FlagsAttribute> özniteliği öneririz, 2, 1, 2, 4, 8, 16 ve benzeri tabanların değerlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="46772-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="46772-197">Ayrıca, "None" değeri 0 olan bir üyenin adını olmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="46772-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="46772-198">Ek yönergeler için bkz: <xref:System.FlagsAttribute> ve <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="46772-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46772-199">Örnek</span><span class="sxs-lookup"><span data-stu-id="46772-199">Example</span></span>  
 <span data-ttu-id="46772-200">Aşağıdaki örnek nasıl kullanılacağını gösterir `Enum` deyimi.</span><span class="sxs-lookup"><span data-stu-id="46772-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="46772-201">Üye olarak adlandırılır Not `EggSizeEnum.Medium`, olarak değil `Medium`.</span><span class="sxs-lookup"><span data-stu-id="46772-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="46772-202">Örnek</span><span class="sxs-lookup"><span data-stu-id="46772-202">Example</span></span>  
 <span data-ttu-id="46772-203">Aşağıdaki örnekte yöntemi dışında `Egg` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="46772-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="46772-204">Bu nedenle, `EggSizeEnum` olarak tam olarak `Egg.EggSizeEnum`.</span><span class="sxs-lookup"><span data-stu-id="46772-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]  
  
## <a name="example"></a><span data-ttu-id="46772-205">Örnek</span><span class="sxs-lookup"><span data-stu-id="46772-205">Example</span></span>  
 <span data-ttu-id="46772-206">Aşağıdaki örnekte `Enum` ilgili bir kümesini tanımlamak için deyimi adlı sabit değerler.</span><span class="sxs-lookup"><span data-stu-id="46772-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="46772-207">Bu durumda, bir veritabanı için veri girişi formları tasarlama tercih edebileceğiniz renkleri değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="46772-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="46772-208">Örnek</span><span class="sxs-lookup"><span data-stu-id="46772-208">Example</span></span>  
 <span data-ttu-id="46772-209">Aşağıdaki örnek, pozitif ve negatif sayıları içeren değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="46772-209">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="46772-210">Örnek</span><span class="sxs-lookup"><span data-stu-id="46772-210">Example</span></span>  
 <span data-ttu-id="46772-211">Aşağıdaki örnekte, bir `As` yan tümcesini belirtmek için kullanılır `datatype` bir numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="46772-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="46772-212">Örnek</span><span class="sxs-lookup"><span data-stu-id="46772-212">Example</span></span>  
 <span data-ttu-id="46772-213">Aşağıdaki örnek, bit düzeyinde bir numaralandırma kullanma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="46772-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="46772-214">Bit düzeyinde bir sabit listesi örneğini birden çok değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="46772-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="46772-215">`Enum` Bildirimi içeren <xref:System.FlagsAttribute> özniteliği sabit listesi flags bir dizi ele alınıp alınamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="46772-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="46772-216">Örnek</span><span class="sxs-lookup"><span data-stu-id="46772-216">Example</span></span>  
 <span data-ttu-id="46772-217">Aşağıdaki örnek, bir sabit listesi yinelenir.</span><span class="sxs-lookup"><span data-stu-id="46772-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="46772-218">Kullandığı <xref:System.Enum.GetNames%2A> sabit listesinden alınmış üye adlarının dizisini almak için yöntemi ve <xref:System.Enum.GetValues%2A> üye değerler dizisini almak için.</span><span class="sxs-lookup"><span data-stu-id="46772-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]  
  
## <a name="see-also"></a><span data-ttu-id="46772-219">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46772-219">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="46772-220">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="46772-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="46772-221">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="46772-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="46772-222">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="46772-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="46772-223">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="46772-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="46772-224">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="46772-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
