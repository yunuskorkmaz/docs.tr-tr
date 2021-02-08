---
description: 'Daha fazla bilgi edinin: enum ekstresi (Visual Basic)'
title: Enum Deyimi
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
ms.openlocfilehash: dcaf28e949f8d34b8d72b07d8029ea10d6baeabf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769175"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="fd8e5-103">Enum Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd8e5-103">Enum Statement (Visual Basic)</span></span>

<span data-ttu-id="fd8e5-104">Bir sabit listesi bildirir ve üyelerinin değerlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-104">Declares an enumeration and defines the values of its members.</span></span>

## <a name="syntax"></a><span data-ttu-id="fd8e5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fd8e5-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a><span data-ttu-id="fd8e5-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="fd8e5-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="fd8e5-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-107">Optional.</span></span> <span data-ttu-id="fd8e5-108">Bu sabit listesi için uygulanan özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-108">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="fd8e5-109">[Öznitelik listesini](attribute-list.md) açılı ayraçlar (" `<` " ve " `>` ") içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-109">You must enclose the [attribute list](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

  <span data-ttu-id="fd8e5-110"><xref:System.FlagsAttribute>Özniteliği, sabit listesinin bir örneğinin değerinin birden çok numaralandırma üyesi içerebileceğini ve her üyenin numaralandırma değerindeki bir bit alanını temsil ettiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-110">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>

- `accessmodifier`

  <span data-ttu-id="fd8e5-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-111">Optional.</span></span> <span data-ttu-id="fd8e5-112">Bu numaralandırmaya erişebilecek kodu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-112">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="fd8e5-113">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="fd8e5-113">Can be one of the following:</span></span>

  - [<span data-ttu-id="fd8e5-114">Genel</span><span class="sxs-lookup"><span data-stu-id="fd8e5-114">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="fd8e5-115">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="fd8e5-115">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="fd8e5-116">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="fd8e5-116">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="fd8e5-117">Özel</span><span class="sxs-lookup"><span data-stu-id="fd8e5-117">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="fd8e5-118">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="fd8e5-118">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="fd8e5-119">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="fd8e5-119">Private Protected</span></span>](../modifiers/private-protected.md)

- `Shadows`

  <span data-ttu-id="fd8e5-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-120">Optional.</span></span> <span data-ttu-id="fd8e5-121">Bu sabit listesinin, bir temel sınıfta aynı adlı programlama öğesi veya aşırı yüklenmiş öğeler kümesini yeniden bildirdiğini ve gizlediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-121">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="fd8e5-122">Her üye üzerinde değil, yalnızca Numaralandırmadaki [gölgeleri](../modifiers/shadows.md) belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-122">You can specify [Shadows](../modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>

- `enumerationname`

  <span data-ttu-id="fd8e5-123">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-123">Required.</span></span> <span data-ttu-id="fd8e5-124">Sabit listesinin adı.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-124">Name of the enumeration.</span></span> <span data-ttu-id="fd8e5-125">Geçerli adlar hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="fd8e5-125">For information on valid names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `datatype`

  <span data-ttu-id="fd8e5-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-126">Optional.</span></span> <span data-ttu-id="fd8e5-127">Numaralandırmanın ve tüm üyelerinin veri türü.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-127">Data type of the enumeration and all its members.</span></span>

- `memberlist`

  <span data-ttu-id="fd8e5-128">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-128">Required.</span></span> <span data-ttu-id="fd8e5-129">Bu bildirimde bildirildiği üye sabitlerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-129">List of member constants being declared in this statement.</span></span> <span data-ttu-id="fd8e5-130">Tek tek kaynak kodu satırlarında birden çok üye görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-130">Multiple members appear on individual source code lines.</span></span>

  <span data-ttu-id="fd8e5-131">Her birinin `member` aşağıdaki söz dizimi ve parçaları vardır: `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="fd8e5-131">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>

  |<span data-ttu-id="fd8e5-132">Bölüm</span><span class="sxs-lookup"><span data-stu-id="fd8e5-132">Part</span></span>|<span data-ttu-id="fd8e5-133">Description</span><span class="sxs-lookup"><span data-stu-id="fd8e5-133">Description</span></span>|
  |---|---|
  |`membername`|<span data-ttu-id="fd8e5-134">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-134">Required.</span></span> <span data-ttu-id="fd8e5-135">Bu üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-135">Name of this member.</span></span>|
  |`initializer`|<span data-ttu-id="fd8e5-136">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-136">Optional.</span></span> <span data-ttu-id="fd8e5-137">Derleme zamanında değerlendirilen ve bu üyeye atanan ifade.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-137">Expression that is evaluated at compile time and assigned to this member.</span></span>|

- <span data-ttu-id="fd8e5-138">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="fd8e5-138">`End` `Enum`</span></span>

  <span data-ttu-id="fd8e5-139">Bloğu sonlandırır `Enum` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-139">Terminates the `Enum` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd8e5-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd8e5-140">Remarks</span></span>

<span data-ttu-id="fd8e5-141">Mantıksal olarak birbirleriyle ilgili değişmeyen bir değerler kümesi varsa, bunları bir numaralandırmada birlikte tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-141">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="fd8e5-142">Bu, sabit listesi ve üyeleri için değerlerinden daha kolay anımsanacak anlamlı adlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-142">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="fd8e5-143">Daha sonra, sabit listesi üyelerini kodunuzda birçok yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-143">You can then use the enumeration members in many places in your code.</span></span>

<span data-ttu-id="fd8e5-144">Numaralandırmalar kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fd8e5-144">The benefits of using enumerations include the following:</span></span>

- <span data-ttu-id="fd8e5-145">Dışarı veya hatalı yazma numaralarının neden olduğu hataları azaltır.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-145">Reduces errors caused by transposing or mistyping numbers.</span></span>

- <span data-ttu-id="fd8e5-146">Gelecekte değerlerin değiştirilmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-146">Makes it easy to change values in the future.</span></span>

- <span data-ttu-id="fd8e5-147">Kodun daha kolay okunmasını sağlar, bu da hataların tanıtılmasından daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-147">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>

- <span data-ttu-id="fd8e5-148">İleriye dönük uyumluluğu sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-148">Ensures forward compatibility.</span></span> <span data-ttu-id="fd8e5-149">Numaralandırmalar kullanıyorsanız, gelecekte birisinin üye adlarına karşılık gelen değerleri değiştirmesinin ardından kodunuzun başarısız olma olasılığı düşüktür.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-149">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>

<span data-ttu-id="fd8e5-150">Bir numaralandırma bir ada, temel alınan veri türüne ve bir üye kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-150">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="fd8e5-151">Her üye bir sabiti temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-151">Each member represents a constant.</span></span>

<span data-ttu-id="fd8e5-152">Sınıf, yapı, modül veya arabirim düzeyinde tanımlanan ve herhangi bir yordamın dışında bir numaralandırma, bir *üye numaralandırmadır*.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-152">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="fd8e5-153">Bunu bildiren sınıf, yapı, modül veya arabirimin bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-153">It is a member of the class, structure, module, or interface that declares it.</span></span>

<span data-ttu-id="fd8e5-154">Üye numaralandırmalara, sınıfları, yapısı, modülü veya arabirimi içinde herhangi bir yerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-154">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="fd8e5-155">Bir sınıf, yapı veya modülün dışındaki kodun, bir üye sabit listesinin adını bu sınıf, yapı veya modülün adı ile nitelemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-155">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="fd8e5-156">Kaynak dosyaya bir [Içeri aktarmalar](imports-statement-net-namespace-and-type.md) açıklaması ekleyerek tam nitelikli adlar kullanma gereksinimini ortadan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-156">You can avoid the need to use fully qualified names by adding an [Imports](imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>

<span data-ttu-id="fd8e5-157">Herhangi bir sınıf, yapı, modül veya arabirim dışında, ad alanı düzeyinde belirtilen bir sabit listesi, göründüğü ad alanının bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-157">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>

<span data-ttu-id="fd8e5-158">Bir numaralandırma için *Bildirim bağlamı* bir kaynak dosya, ad alanı, sınıf, yapı, modül veya arabirim olmalıdır ve bir yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-158">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="fd8e5-159">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="fd8e5-159">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="fd8e5-160">Öznitelikleri bir numaralandırmaya bir bütün olarak uygulayabilir, ancak üyelerine tek tek atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-160">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="fd8e5-161">Bir öznitelik, bilgileri derlemenin meta verilerine katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-161">An attribute contributes information to the assembly's metadata.</span></span>

## <a name="data-type"></a><span data-ttu-id="fd8e5-162">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="fd8e5-162">Data Type</span></span>

<span data-ttu-id="fd8e5-163">`Enum`İfade, bir numaralandırmanın veri türünü bildirebilirler.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-163">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="fd8e5-164">Her üye, numaralandırmanın veri türünü alır.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-164">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="fd8e5-165">,,,,, `Byte` `Integer` ,, Veya belirtebilirsiniz `Long` `SByte` `Short` `UInteger` `ULong` `UShort` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-165">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>

<span data-ttu-id="fd8e5-166">`datatype`Sabit listesi için belirtmezseniz, her üye öğesinin veri türünü alır `initializer` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-166">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="fd8e5-167">Hem hem de belirtirseniz `datatype` `initializer` , veri türü `initializer` öğesine dönüştürülebilir olmalıdır `datatype` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-167">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="fd8e5-168">Ne yoksa `datatype` ne de `initializer` yoksa, veri türü varsayılan olarak olur `Integer` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-168">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>

## <a name="initializing-members"></a><span data-ttu-id="fd8e5-169">Üyeler başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="fd8e5-169">Initializing Members</span></span>

<span data-ttu-id="fd8e5-170">`Enum`İfade, içindeki seçili üyelerin içeriğini başlatabilir `memberlist` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-170">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="fd8e5-171">`initializer`Üyeye atanacak bir ifade sağlamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-171">You use `initializer` to supply an expression to be assigned to the member.</span></span>

<span data-ttu-id="fd8e5-172">`initializer`Bir üye için belirtmeyin, Visual Basic bunu sıfıra (ilk `member` içinde ise `memberlist` ) veya bir değerden daha büyük bir değere, hemen öncesinde gelen bir değere başlatır `member` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-172">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>

<span data-ttu-id="fd8e5-173">Her birinde sağlanan ifade `initializer` , herhangi bir sabit değer, önceden tanımlanmış diğer sabitler ve bu numaralandırmanın önceki bir üyesi dahil, zaten tanımlanmış olan sabit listesi üyeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-173">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="fd8e5-174">Bu tür öğeleri birleştirmek için aritmetik ve mantıksal işleçler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-174">You can use arithmetic and logical operators to combine such elements.</span></span>

<span data-ttu-id="fd8e5-175">İçindeki değişkenleri veya işlevleri kullanamazsınız `initializer` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-175">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="fd8e5-176">Ancak, ve gibi dönüştürme anahtar sözcüklerini kullanabilirsiniz `CByte` `CShort` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-176">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="fd8e5-177">`AscW` `String` `Char` Derleme zamanında değerlendirilebileceğinizden, bu değeri bir sabit veya bağımsız değişkenle birlikte çağırırsanız de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-177">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

<span data-ttu-id="fd8e5-178">Numaralandırmalar kayan nokta değerlerine sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-178">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="fd8e5-179">Bir üyeye kayan nokta değeri atanmışsa ve `Option Strict` Açık olarak ayarlanırsa, bir derleyici hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-179">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="fd8e5-180">`Option Strict`Kapalıysa, değer otomatik olarak `Enum` türüne dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-180">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>

<span data-ttu-id="fd8e5-181">Bir üyenin değeri, temel alınan veri türü için izin verilen aralığı aşarsa veya herhangi bir üyeyi temel alınan veri türü tarafından izin verilen en yüksek değere başlattığınızda, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-181">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>

## <a name="modifiers"></a><span data-ttu-id="fd8e5-182">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="fd8e5-182">Modifiers</span></span>

<span data-ttu-id="fd8e5-183">Sınıf, yapı, modül ve arabirim üyesi numaralandırmalar, genel erişim için varsayılan.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-183">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="fd8e5-184">Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-184">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="fd8e5-185">Ad alanı üyesi numaralandırmalar arkadaş erişimi için varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-185">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="fd8e5-186">Erişim düzeylerini herkese açık olarak ayarlayabilir, ancak özel veya korumalı olamaz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-186">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="fd8e5-187">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="fd8e5-187">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="fd8e5-188">Tüm numaralandırma üyelerinin ortak erişimi vardır ve bunlar üzerinde herhangi bir erişim değiştiricilerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-188">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="fd8e5-189">Ancak, numaralandırmanın kendisi daha kısıtlı erişim düzeyine sahipse, belirtilen numaralandırma erişim düzeyi önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-189">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>

<span data-ttu-id="fd8e5-190">Varsayılan olarak, tüm numaralandırmalar türlerdir ve alanları sabittir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-190">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="fd8e5-191">Bu nedenle `Shared` ,, `Static` ve `ReadOnly` anahtar sözcükleri bir numaralandırma veya üyeleri bildirirken kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-191">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>

## <a name="assigning-multiple-values"></a><span data-ttu-id="fd8e5-192">Birden çok değer atama</span><span class="sxs-lookup"><span data-stu-id="fd8e5-192">Assigning Multiple Values</span></span>

<span data-ttu-id="fd8e5-193">Numaralandırmalar genellikle birbirini dışlayan değerleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-193">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="fd8e5-194"><xref:System.FlagsAttribute>Özniteliği `Enum` bildirime ekleyerek, bunun yerine sabit listesinin bir örneğine birden çok değer atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-194">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="fd8e5-195"><xref:System.FlagsAttribute>Özniteliği, numaralandırmanın bir bit alanı, yani bir bayrak kümesi olarak değerlendirilip değerlendirilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-195">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="fd8e5-196">Bunlara *bit düzeyinde* numaralandırmalar denir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-196">These are called *bitwise* enumerations.</span></span>

<span data-ttu-id="fd8e5-197">Özniteliği kullanarak bir numaralandırma bildirdiğinizde <xref:System.FlagsAttribute> , değerler için 2, bu, 1, 2, 4, 8, 16, vb. üslerini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-197">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="fd8e5-198">Ayrıca "none" değerinin değeri 0 olan üyenin adı olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-198">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="fd8e5-199">Ek yönergeler için bkz <xref:System.FlagsAttribute> . ve <xref:System.Enum> .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-199">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>

## <a name="example"></a><span data-ttu-id="fd8e5-200">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd8e5-200">Example</span></span>

<span data-ttu-id="fd8e5-201">Aşağıdaki örnek, ifadesinin nasıl kullanılacağını göstermektedir `Enum` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-201">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="fd8e5-202">Üyenin olarak adlandırıldığına ve farklı şekilde olduğunu unutmayın `EggSizeEnum.Medium` `Medium` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-202">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a><span data-ttu-id="fd8e5-203">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd8e5-203">Example</span></span>

<span data-ttu-id="fd8e5-204">Aşağıdaki örnekteki yöntemi `Egg` sınıfının dışındadır.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-204">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="fd8e5-205">Bu nedenle, `EggSizeEnum` tam olarak nitelenir `Egg.EggSizeEnum` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-205">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a><span data-ttu-id="fd8e5-206">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd8e5-206">Example</span></span>

<span data-ttu-id="fd8e5-207">Aşağıdaki örnek, `Enum` ilgili bir adlandırılmış sabit değer kümesini tanımlamak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-207">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="fd8e5-208">Bu durumda, değerler, bir veritabanı için veri girişi formları tasarlamayı seçebileceğiniz renklerdir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-208">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a><span data-ttu-id="fd8e5-209">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd8e5-209">Example</span></span>

<span data-ttu-id="fd8e5-210">Aşağıdaki örnek, hem pozitif hem de negatif sayı içeren değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-210">The following example shows values that include both positive and negative numbers.</span></span>

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a><span data-ttu-id="fd8e5-211">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd8e5-211">Example</span></span>

<span data-ttu-id="fd8e5-212">Aşağıdaki örnekte, bir `As` sabit listesini belirtmek için bir yan tümce kullanılır `datatype` .</span><span class="sxs-lookup"><span data-stu-id="fd8e5-212">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a><span data-ttu-id="fd8e5-213">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd8e5-213">Example</span></span>

<span data-ttu-id="fd8e5-214">Aşağıdaki örnek bit düzeyinde numaralandırmanın nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-214">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="fd8e5-215">Bit düzeyinde numaralandırma örneğine birden çok değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-215">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="fd8e5-216">`Enum`Bildirimi, <xref:System.FlagsAttribute> numaralandırmanın bir dizi bayrak olarak değerlendirileceğini gösteren özniteliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-216">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a><span data-ttu-id="fd8e5-217">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd8e5-217">Example</span></span>

<span data-ttu-id="fd8e5-218">Aşağıdaki örnek bir numaralandırma boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-218">The following example iterates through an enumeration.</span></span> <span data-ttu-id="fd8e5-219"><xref:System.Enum.GetNames%2A>Numaralandırmadaki üye adları dizisini almak ve <xref:System.Enum.GetValues%2A> bir dizi üye değeri almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-219">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="fd8e5-220">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd8e5-220">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="fd8e5-221">Const Deyimi</span><span class="sxs-lookup"><span data-stu-id="fd8e5-221">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="fd8e5-222">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="fd8e5-222">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="fd8e5-223">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="fd8e5-223">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="fd8e5-224">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fd8e5-224">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="fd8e5-225">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="fd8e5-225">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
