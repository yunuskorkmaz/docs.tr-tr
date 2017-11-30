---
title: "Aşırı Yüklemeler (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a23a6b91681cbd814ac96464e1c340be99a0ecf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="fde50-102">Aşırı Yüklemeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fde50-102">Overloads (Visual Basic)</span></span>
<span data-ttu-id="fde50-103">Bir özellik veya yordam bir veya daha fazla var olan özellikleri ya da aynı ada sahip yordamlar redeclares belirtir.</span><span class="sxs-lookup"><span data-stu-id="fde50-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fde50-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fde50-104">Remarks</span></span>  
 <span data-ttu-id="fde50-105">*Aşırı yükleme* aynı kapsamda belirli bir özellik veya yordam adı için birden fazla tanım sağladığını uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="fde50-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="fde50-106">Bir özellik veya farklı bir imzaya sahip yordamı redeclaring bazen çağrılır *imzaya göre gizleme*.</span><span class="sxs-lookup"><span data-stu-id="fde50-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="fde50-107">Kurallar</span><span class="sxs-lookup"><span data-stu-id="fde50-107">Rules</span></span>  
  
-   <span data-ttu-id="fde50-108">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="fde50-108">**Declaration Context.**</span></span> <span data-ttu-id="fde50-109">Kullanabileceğiniz `Overloads` yalnızca bir özellik veya yordam bildirimi deyimi içinde.</span><span class="sxs-lookup"><span data-stu-id="fde50-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="fde50-110">**Birleşik değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="fde50-110">**Combined Modifiers.**</span></span> <span data-ttu-id="fde50-111">Belirtemeyeceğiniz `Overloads` ile birlikte [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md) aynı yordamı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="fde50-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>  
  
-   <span data-ttu-id="fde50-112">**Farkları gereklidir.**</span><span class="sxs-lookup"><span data-stu-id="fde50-112">**Required Differences.**</span></span> <span data-ttu-id="fde50-113">*İmza* bu bildirimi her bir özellik veya onu overloads yordamı imzadan farklı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fde50-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="fde50-114">İmza birlikte aşağıdaki özellik veya yordam adı oluşur:</span><span class="sxs-lookup"><span data-stu-id="fde50-114">The signature comprises the property or procedure name together with the following:</span></span>  
  
    -   <span data-ttu-id="fde50-115">parametre sayısı</span><span class="sxs-lookup"><span data-stu-id="fde50-115">the number of parameters</span></span>  
  
    -   <span data-ttu-id="fde50-116">Parametreler sırası</span><span class="sxs-lookup"><span data-stu-id="fde50-116">the order of the parameters</span></span>  
  
    -   <span data-ttu-id="fde50-117">parametre veri türleri</span><span class="sxs-lookup"><span data-stu-id="fde50-117">the data types of the parameters</span></span>  
  
    -   <span data-ttu-id="fde50-118">Tür parametreleri (için genel bir yordam) sayısı</span><span class="sxs-lookup"><span data-stu-id="fde50-118">the number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="fde50-119">dönüş türü (yalnızca bir dönüşüm işleci yordam için)</span><span class="sxs-lookup"><span data-stu-id="fde50-119">the return type (only for a conversion operator procedure)</span></span>  
  
     <span data-ttu-id="fde50-120">Tüm aşırı aynı ada sahip olmalıdır, ancak her tüm başkalarından gelen bir veya daha önceki gizliliğinize farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fde50-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="fde50-121">Bu kod özellik veya yordam çağırdığında kullanmak için hangi sürümün ayırt etmek derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="fde50-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>  
  
-   <span data-ttu-id="fde50-122">**İzin verilmeyen farklılıkları.**</span><span class="sxs-lookup"><span data-stu-id="fde50-122">**Disallowed Differences.**</span></span> <span data-ttu-id="fde50-123">Aşağıdakilerden birini veya birkaçını değiştirme, imza parçası olmadıklarından bir özellik veya yordam aşırı yüklemesi için geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="fde50-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>  
  
    -   <span data-ttu-id="fde50-124">desteklemediğini (için bir yordam) bir değer döndürür</span><span class="sxs-lookup"><span data-stu-id="fde50-124">whether or not it returns a value (for a procedure)</span></span>  
  
    -   <span data-ttu-id="fde50-125">Dönüş değeri (dışında bir dönüşüm işleci) veri türü</span><span class="sxs-lookup"><span data-stu-id="fde50-125">the data type of the return value (except for a conversion operator)</span></span>  
  
    -   <span data-ttu-id="fde50-126">Tür parametreleri parametre adları</span><span class="sxs-lookup"><span data-stu-id="fde50-126">the names of the parameters or type parameters</span></span>  
  
    -   <span data-ttu-id="fde50-127">(için genel bir yordam) tür parametrelerindeki kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="fde50-127">the constraints on the type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="fde50-128">parametresi değiştiricisi anahtar sözcükler (gibi `ByRef` veya `Optional`)</span><span class="sxs-lookup"><span data-stu-id="fde50-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>  
  
    -   <span data-ttu-id="fde50-129">özellik veya yordam değiştiricisi anahtar sözcükler (gibi `Public` veya `Shared`)</span><span class="sxs-lookup"><span data-stu-id="fde50-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>  
  
-   <span data-ttu-id="fde50-130">**İsteğe bağlı değiştiricisi.**</span><span class="sxs-lookup"><span data-stu-id="fde50-130">**Optional Modifier.**</span></span> <span data-ttu-id="fde50-131">Kullanmak zorunda değil `Overloads` aynı sınıfta birden fazla aşırı yüklenmiş özellikler ya da yordamlar tanımlarken değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="fde50-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="fde50-132">Ancak, kullanırsanız `Overloads` bildirimleri her birinde, bunların tümünde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fde50-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>  
  
-   <span data-ttu-id="fde50-133">**Gölgeleme ve aşırı yüklemesi.**</span><span class="sxs-lookup"><span data-stu-id="fde50-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="fde50-134">`Overloads`Ayrıca gölge var olan bir üye ya da bir taban sınıf içinde aşırı yüklenmiş üyeler kümesi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fde50-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="fde50-135">Kullandığınızda `Overloads` bu şekilde, özellik veya yöntem aynı adı ve temel sınıf üyesi ile aynı parametre listesine bildirme ve sağladığınız değil `Shadows` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="fde50-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>  
  
 <span data-ttu-id="fde50-136">Kullanırsanız `Overrides`, derleyici örtük olarak ekler `Overloads` kitaplığınızın API'leri iş böylece C# ile daha kolay.</span><span class="sxs-lookup"><span data-stu-id="fde50-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="fde50-137">`Overloads` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="fde50-137">The `Overloads` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="fde50-138">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="fde50-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="fde50-139">Operator deyimi</span><span class="sxs-lookup"><span data-stu-id="fde50-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="fde50-140">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="fde50-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="fde50-141">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="fde50-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="fde50-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fde50-142">See Also</span></span>  
 [<span data-ttu-id="fde50-143">Gölgeleri</span><span class="sxs-lookup"><span data-stu-id="fde50-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="fde50-144">Yordam aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="fde50-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="fde50-145">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="fde50-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="fde50-146">İşleç yordamları</span><span class="sxs-lookup"><span data-stu-id="fde50-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="fde50-147">Nasıl yapılır: bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="fde50-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
