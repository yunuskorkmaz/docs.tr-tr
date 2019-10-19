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
ms.openlocfilehash: be1780b00b4d58964e1de5ec199cb80dc0f9dba5
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583403"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="00e56-102">Enum Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00e56-102">Enum Statement (Visual Basic)</span></span>

<span data-ttu-id="00e56-103">Bir sabit listesi bildirir ve üyelerinin değerlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="00e56-103">Declares an enumeration and defines the values of its members.</span></span>

## <a name="syntax"></a><span data-ttu-id="00e56-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00e56-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a><span data-ttu-id="00e56-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="00e56-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="00e56-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="00e56-106">Optional.</span></span> <span data-ttu-id="00e56-107">Bu sabit listesi için uygulanan özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="00e56-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="00e56-108">[Öznitelik listesini](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç içine almalısınız ("`<`" ve "`>`").</span><span class="sxs-lookup"><span data-stu-id="00e56-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

  <span data-ttu-id="00e56-109">@No__t_0 özniteliği, sabit listesinin bir örneğinin değerinin birden çok numaralandırma üyesi içerebileceğini ve her üyenin numaralandırma değerindeki bir bit alanını temsil ettiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="00e56-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>

- `accessmodifier`

  <span data-ttu-id="00e56-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="00e56-110">Optional.</span></span> <span data-ttu-id="00e56-111">Bu numaralandırmaya erişebilecek kodu belirtir.</span><span class="sxs-lookup"><span data-stu-id="00e56-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="00e56-112">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="00e56-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="00e56-113">Public</span><span class="sxs-lookup"><span data-stu-id="00e56-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="00e56-114">Protected</span><span class="sxs-lookup"><span data-stu-id="00e56-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="00e56-115">Friend</span><span class="sxs-lookup"><span data-stu-id="00e56-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="00e56-116">Private</span><span class="sxs-lookup"><span data-stu-id="00e56-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="00e56-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="00e56-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="00e56-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="00e56-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

- `Shadows`

  <span data-ttu-id="00e56-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="00e56-119">Optional.</span></span> <span data-ttu-id="00e56-120">Bu sabit listesinin, bir temel sınıfta aynı adlı programlama öğesi veya aşırı yüklenmiş öğeler kümesini yeniden bildirdiğini ve gizlediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="00e56-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="00e56-121">Her üye üzerinde değil, yalnızca Numaralandırmadaki [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md) belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e56-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>

- `enumerationname`

  <span data-ttu-id="00e56-122">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="00e56-122">Required.</span></span> <span data-ttu-id="00e56-123">Sabit listesinin adı.</span><span class="sxs-lookup"><span data-stu-id="00e56-123">Name of the enumeration.</span></span> <span data-ttu-id="00e56-124">Geçerli adlar hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="00e56-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `datatype`

  <span data-ttu-id="00e56-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="00e56-125">Optional.</span></span> <span data-ttu-id="00e56-126">Numaralandırmanın ve tüm üyelerinin veri türü.</span><span class="sxs-lookup"><span data-stu-id="00e56-126">Data type of the enumeration and all its members.</span></span>

- `memberlist`

  <span data-ttu-id="00e56-127">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="00e56-127">Required.</span></span> <span data-ttu-id="00e56-128">Bu bildirimde bildirildiği üye sabitlerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="00e56-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="00e56-129">Tek tek kaynak kodu satırlarında birden çok üye görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="00e56-129">Multiple members appear on individual source code lines.</span></span>

  <span data-ttu-id="00e56-130">Her `member` aşağıdaki söz dizimi ve bölümlere sahiptir: `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="00e56-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>

  |<span data-ttu-id="00e56-131">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="00e56-131">Part</span></span>|<span data-ttu-id="00e56-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00e56-132">Description</span></span>|
  |---|---|
  |`membername`|<span data-ttu-id="00e56-133">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="00e56-133">Required.</span></span> <span data-ttu-id="00e56-134">Bu üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="00e56-134">Name of this member.</span></span>|
  |`initializer`|<span data-ttu-id="00e56-135">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="00e56-135">Optional.</span></span> <span data-ttu-id="00e56-136">Derleme zamanında değerlendirilen ve bu üyeye atanan ifade.</span><span class="sxs-lookup"><span data-stu-id="00e56-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|

- <span data-ttu-id="00e56-137">`End``Enum`</span><span class="sxs-lookup"><span data-stu-id="00e56-137">`End` `Enum`</span></span>

  <span data-ttu-id="00e56-138">@No__t_0 bloğunu sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="00e56-138">Terminates the `Enum` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="00e56-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00e56-139">Remarks</span></span>

<span data-ttu-id="00e56-140">Mantıksal olarak birbirleriyle ilgili değişmeyen bir değerler kümesi varsa, bunları bir numaralandırmada birlikte tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e56-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="00e56-141">Bu, sabit listesi ve üyeleri için değerlerinden daha kolay anımsanacak anlamlı adlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="00e56-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="00e56-142">Daha sonra, sabit listesi üyelerini kodunuzda birçok yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e56-142">You can then use the enumeration members in many places in your code.</span></span>

<span data-ttu-id="00e56-143">Numaralandırmalar kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="00e56-143">The benefits of using enumerations include the following:</span></span>

- <span data-ttu-id="00e56-144">Dışarı veya hatalı yazma numaralarının neden olduğu hataları azaltır.</span><span class="sxs-lookup"><span data-stu-id="00e56-144">Reduces errors caused by transposing or mistyping numbers.</span></span>

- <span data-ttu-id="00e56-145">Gelecekte değerlerin değiştirilmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="00e56-145">Makes it easy to change values in the future.</span></span>

- <span data-ttu-id="00e56-146">Kodun daha kolay okunmasını sağlar, bu da hataların tanıtılmasından daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="00e56-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>

- <span data-ttu-id="00e56-147">İleriye dönük uyumluluğu sağlar.</span><span class="sxs-lookup"><span data-stu-id="00e56-147">Ensures forward compatibility.</span></span> <span data-ttu-id="00e56-148">Numaralandırmalar kullanıyorsanız, gelecekte birisinin üye adlarına karşılık gelen değerleri değiştirmesinin ardından kodunuzun başarısız olma olasılığı düşüktür.</span><span class="sxs-lookup"><span data-stu-id="00e56-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>

<span data-ttu-id="00e56-149">Bir numaralandırma bir ada, temel alınan veri türüne ve bir üye kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="00e56-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="00e56-150">Her üye bir sabiti temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00e56-150">Each member represents a constant.</span></span>

<span data-ttu-id="00e56-151">Sınıf, yapı, modül veya arabirim düzeyinde tanımlanan ve herhangi bir yordamın dışında bir numaralandırma, bir *üye numaralandırmadır*.</span><span class="sxs-lookup"><span data-stu-id="00e56-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="00e56-152">Bunu bildiren sınıf, yapı, modül veya arabirimin bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="00e56-152">It is a member of the class, structure, module, or interface that declares it.</span></span>

<span data-ttu-id="00e56-153">Üye numaralandırmalara, sınıfları, yapısı, modülü veya arabirimi içinde herhangi bir yerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="00e56-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="00e56-154">Bir sınıf, yapı veya modülün dışındaki kodun, bir üye sabit listesinin adını bu sınıf, yapı veya modülün adı ile nitelemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="00e56-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="00e56-155">Kaynak dosyaya bir [Içeri aktarmalar](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) açıklaması ekleyerek tam nitelikli adlar kullanma gereksinimini ortadan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e56-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>

<span data-ttu-id="00e56-156">Herhangi bir sınıf, yapı, modül veya arabirim dışında, ad alanı düzeyinde belirtilen bir sabit listesi, göründüğü ad alanının bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="00e56-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>

<span data-ttu-id="00e56-157">Bir numaralandırma için *Bildirim bağlamı* bir kaynak dosya, ad alanı, sınıf, yapı, modül veya arabirim olmalıdır ve bir yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="00e56-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="00e56-158">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="00e56-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="00e56-159">Öznitelikleri bir numaralandırmaya bir bütün olarak uygulayabilir, ancak üyelerine tek tek atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e56-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="00e56-160">Bir öznitelik, bilgileri derlemenin meta verilerine katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="00e56-160">An attribute contributes information to the assembly's metadata.</span></span>

## <a name="data-type"></a><span data-ttu-id="00e56-161">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="00e56-161">Data Type</span></span>

<span data-ttu-id="00e56-162">@No__t_0 deyimin bir numaralandırmanın veri türünü bildirebilme.</span><span class="sxs-lookup"><span data-stu-id="00e56-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="00e56-163">Her üye, numaralandırmanın veri türünü alır.</span><span class="sxs-lookup"><span data-stu-id="00e56-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="00e56-164">@No__t_0, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong` veya `UShort` belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e56-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>

<span data-ttu-id="00e56-165">Sabit listesi için `datatype` belirtmezseniz, her üye `initializer` veri türünü alır.</span><span class="sxs-lookup"><span data-stu-id="00e56-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="00e56-166">Hem `datatype` hem de `initializer` belirtirseniz `initializer` veri türü `datatype` dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00e56-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="00e56-167">Ne `datatype` ne de `initializer` yoksa, veri türü varsayılan olarak `Integer`.</span><span class="sxs-lookup"><span data-stu-id="00e56-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>

## <a name="initializing-members"></a><span data-ttu-id="00e56-168">Üyeler başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="00e56-168">Initializing Members</span></span>

<span data-ttu-id="00e56-169">@No__t_0 deyimleri `memberlist` seçilen üyelerin içeriğini başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="00e56-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="00e56-170">Üyeye atanacak bir ifade sağlamak için `initializer` kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="00e56-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>

<span data-ttu-id="00e56-171">Bir üye için `initializer` belirtmezseniz, Visual Basic sıfır (`memberlist` ' de ilk `member`) veya hemen önceki `member` bir değere göre daha büyük bir değere başlatır.</span><span class="sxs-lookup"><span data-stu-id="00e56-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>

<span data-ttu-id="00e56-172">Her bir `initializer` sağlanan ifade, herhangi bir sabit değer, önceden tanımlanmış diğer sabitler ve bu numaralandırmanın önceki bir üyesi dahil, zaten tanımlanmış olan sabit listesi üyeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="00e56-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="00e56-173">Bu tür öğeleri birleştirmek için aritmetik ve mantıksal işleçler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e56-173">You can use arithmetic and logical operators to combine such elements.</span></span>

<span data-ttu-id="00e56-174">@No__t_0 değişkenleri veya işlevleri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="00e56-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="00e56-175">Ancak, `CByte` ve `CShort` gibi dönüştürme anahtar sözcüklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e56-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="00e56-176">@No__t_0, derleme zamanında değerlendirilebilen bir sabit `String` veya `Char` bağımsız değişkeniyle çağırırsanız de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e56-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

<span data-ttu-id="00e56-177">Numaralandırmalar kayan nokta değerlerine sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="00e56-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="00e56-178">Bir üyeye kayan nokta değeri atanırsa ve `Option Strict` on olarak ayarlandıysa, bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="00e56-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="00e56-179">@No__t_0 kapalıysa, değer otomatik olarak `Enum` türüne dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="00e56-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>

<span data-ttu-id="00e56-180">Bir üyenin değeri, temel alınan veri türü için izin verilen aralığı aşarsa veya herhangi bir üyeyi temel alınan veri türü tarafından izin verilen en yüksek değere başlattığınızda, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="00e56-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>

## <a name="modifiers"></a><span data-ttu-id="00e56-181">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="00e56-181">Modifiers</span></span>

<span data-ttu-id="00e56-182">Sınıf, yapı, modül ve arabirim üyesi numaralandırmalar, genel erişim için varsayılan.</span><span class="sxs-lookup"><span data-stu-id="00e56-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="00e56-183">Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e56-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="00e56-184">Ad alanı üyesi numaralandırmalar arkadaş erişimi için varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="00e56-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="00e56-185">Erişim düzeylerini herkese açık olarak ayarlayabilir, ancak özel veya korumalı olamaz.</span><span class="sxs-lookup"><span data-stu-id="00e56-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="00e56-186">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="00e56-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="00e56-187">Tüm numaralandırma üyelerinin ortak erişimi vardır ve bunlar üzerinde herhangi bir erişim değiştiricilerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="00e56-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="00e56-188">Ancak, numaralandırmanın kendisi daha kısıtlı erişim düzeyine sahipse, belirtilen numaralandırma erişim düzeyi önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="00e56-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>

<span data-ttu-id="00e56-189">Varsayılan olarak, tüm numaralandırmalar türlerdir ve alanları sabittir.</span><span class="sxs-lookup"><span data-stu-id="00e56-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="00e56-190">Bu nedenle, bir numaralandırma veya üyeleri bildirirken `Shared`, `Static` ve `ReadOnly` anahtar sözcükleri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="00e56-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>

## <a name="assigning-multiple-values"></a><span data-ttu-id="00e56-191">Birden çok değer atama</span><span class="sxs-lookup"><span data-stu-id="00e56-191">Assigning Multiple Values</span></span>

<span data-ttu-id="00e56-192">Numaralandırmalar genellikle birbirini dışlayan değerleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00e56-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="00e56-193">@No__t_1 bildirimine <xref:System.FlagsAttribute> özniteliğini ekleyerek, bunun yerine sabit listesinin bir örneğine birden çok değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e56-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="00e56-194">@No__t_0 özniteliği, numaralandırmanın bir bit alanı, yani bir bayrak kümesi olarak değerlendirilip değerlendirilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="00e56-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="00e56-195">Bunlara *bit düzeyinde* numaralandırmalar denir.</span><span class="sxs-lookup"><span data-stu-id="00e56-195">These are called *bitwise* enumerations.</span></span>

<span data-ttu-id="00e56-196">@No__t_0 özniteliğini kullanarak bir numaralandırma bildirdiğinizde, değerler için 2, bu, 1, 2, 4, 8, 16, vb. üslerini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="00e56-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="00e56-197">Ayrıca "none" değerinin değeri 0 olan üyenin adı olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="00e56-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="00e56-198">Ek yönergeler için bkz. <xref:System.FlagsAttribute> ve <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="00e56-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>

## <a name="example"></a><span data-ttu-id="00e56-199">Örnek</span><span class="sxs-lookup"><span data-stu-id="00e56-199">Example</span></span>

<span data-ttu-id="00e56-200">Aşağıdaki örnek, `Enum` deyimin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="00e56-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="00e56-201">Üyenin `Medium` değil `EggSizeEnum.Medium` olarak adlandırıldığına göz önünde bulunurlar.</span><span class="sxs-lookup"><span data-stu-id="00e56-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a><span data-ttu-id="00e56-202">Örnek</span><span class="sxs-lookup"><span data-stu-id="00e56-202">Example</span></span>

<span data-ttu-id="00e56-203">Aşağıdaki örnekteki yöntem `Egg` sınıfının dışındadır.</span><span class="sxs-lookup"><span data-stu-id="00e56-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="00e56-204">Bu nedenle, `EggSizeEnum` `Egg.EggSizeEnum` tam olarak nitelenir.</span><span class="sxs-lookup"><span data-stu-id="00e56-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a><span data-ttu-id="00e56-205">Örnek</span><span class="sxs-lookup"><span data-stu-id="00e56-205">Example</span></span>

<span data-ttu-id="00e56-206">Aşağıdaki örnek, ilgili bir adlandırılmış sabit değer kümesini tanımlamak için `Enum` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="00e56-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="00e56-207">Bu durumda, değerler, bir veritabanı için veri girişi formları tasarlamayı seçebileceğiniz renklerdir.</span><span class="sxs-lookup"><span data-stu-id="00e56-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a><span data-ttu-id="00e56-208">Örnek</span><span class="sxs-lookup"><span data-stu-id="00e56-208">Example</span></span>

<span data-ttu-id="00e56-209">Aşağıdaki örnek, hem pozitif hem de negatif sayı içeren değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="00e56-209">The following example shows values that include both positive and negative numbers.</span></span>

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a><span data-ttu-id="00e56-210">Örnek</span><span class="sxs-lookup"><span data-stu-id="00e56-210">Example</span></span>

<span data-ttu-id="00e56-211">Aşağıdaki örnekte, bir numaralandırma `datatype` belirtmek için bir `As` yan tümcesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00e56-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a><span data-ttu-id="00e56-212">Örnek</span><span class="sxs-lookup"><span data-stu-id="00e56-212">Example</span></span>

<span data-ttu-id="00e56-213">Aşağıdaki örnek bit düzeyinde numaralandırmanın nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="00e56-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="00e56-214">Bit düzeyinde numaralandırma örneğine birden çok değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="00e56-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="00e56-215">@No__t_0 bildirimi, numaralandırmanın bir dizi bayrak olarak değerlendirileceğini gösteren <xref:System.FlagsAttribute> özniteliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="00e56-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a><span data-ttu-id="00e56-216">Örnek</span><span class="sxs-lookup"><span data-stu-id="00e56-216">Example</span></span>

<span data-ttu-id="00e56-217">Aşağıdaki örnek bir numaralandırma boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="00e56-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="00e56-218">Numaralandırmadaki üye adları dizisini almak için <xref:System.Enum.GetNames%2A> yöntemini kullanır ve üye değerleri dizisini almak için <xref:System.Enum.GetValues%2A>.</span><span class="sxs-lookup"><span data-stu-id="00e56-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="00e56-219">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00e56-219">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="00e56-220">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="00e56-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="00e56-221">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="00e56-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="00e56-222">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="00e56-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="00e56-223">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="00e56-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="00e56-224">Sabitler ve Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="00e56-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
