---
title: Aşırı Yüklemeler (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: b68c13d192845fc4bedf1b34a40165ccc1a5ff75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601920"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="db7bf-102">Aşırı Yüklemeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db7bf-102">Overloads (Visual Basic)</span></span>
<span data-ttu-id="db7bf-103">Bir özellik veya yordam bir veya daha fazla var olan özellikleri ya da aynı ada sahip yordamlar redeclares belirtir.</span><span class="sxs-lookup"><span data-stu-id="db7bf-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db7bf-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db7bf-104">Remarks</span></span>  
 <span data-ttu-id="db7bf-105">*Aşırı yükleme* aynı kapsamda belirli bir özellik veya yordam adı için birden fazla tanım sağladığını uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="db7bf-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="db7bf-106">Bir özellik veya farklı bir imzaya sahip yordamı redeclaring bazen çağrılır *imzaya göre gizleme*.</span><span class="sxs-lookup"><span data-stu-id="db7bf-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="db7bf-107">Kurallar</span><span class="sxs-lookup"><span data-stu-id="db7bf-107">Rules</span></span>  
  
-   <span data-ttu-id="db7bf-108">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="db7bf-108">**Declaration Context.**</span></span> <span data-ttu-id="db7bf-109">Kullanabileceğiniz `Overloads` yalnızca bir özellik veya yordam bildirimi deyimi içinde.</span><span class="sxs-lookup"><span data-stu-id="db7bf-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="db7bf-110">**Birleşik değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="db7bf-110">**Combined Modifiers.**</span></span> <span data-ttu-id="db7bf-111">Belirtemeyeceğiniz `Overloads` ile birlikte [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md) aynı yordamı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="db7bf-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>  
  
-   <span data-ttu-id="db7bf-112">**Farkları gereklidir.**</span><span class="sxs-lookup"><span data-stu-id="db7bf-112">**Required Differences.**</span></span> <span data-ttu-id="db7bf-113">*İmza* bu bildirimi her bir özellik veya onu overloads yordamı imzadan farklı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="db7bf-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="db7bf-114">İmza birlikte aşağıdaki özellik veya yordam adı oluşur:</span><span class="sxs-lookup"><span data-stu-id="db7bf-114">The signature comprises the property or procedure name together with the following:</span></span>  
  
    -   <span data-ttu-id="db7bf-115">parametre sayısı</span><span class="sxs-lookup"><span data-stu-id="db7bf-115">the number of parameters</span></span>  
  
    -   <span data-ttu-id="db7bf-116">Parametreler sırası</span><span class="sxs-lookup"><span data-stu-id="db7bf-116">the order of the parameters</span></span>  
  
    -   <span data-ttu-id="db7bf-117">parametre veri türleri</span><span class="sxs-lookup"><span data-stu-id="db7bf-117">the data types of the parameters</span></span>  
  
    -   <span data-ttu-id="db7bf-118">Tür parametreleri (için genel bir yordam) sayısı</span><span class="sxs-lookup"><span data-stu-id="db7bf-118">the number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="db7bf-119">dönüş türü (yalnızca bir dönüşüm işleci yordam için)</span><span class="sxs-lookup"><span data-stu-id="db7bf-119">the return type (only for a conversion operator procedure)</span></span>  
  
     <span data-ttu-id="db7bf-120">Tüm aşırı aynı ada sahip olmalıdır, ancak her tüm başkalarından gelen bir veya daha önceki gizliliğinize farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db7bf-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="db7bf-121">Bu kod özellik veya yordam çağırdığında kullanmak için hangi sürümün ayırt etmek derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="db7bf-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>  
  
-   <span data-ttu-id="db7bf-122">**İzin verilmeyen farklılıkları.**</span><span class="sxs-lookup"><span data-stu-id="db7bf-122">**Disallowed Differences.**</span></span> <span data-ttu-id="db7bf-123">Aşağıdakilerden birini veya birkaçını değiştirme, imza parçası olmadıklarından bir özellik veya yordam aşırı yüklemesi için geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="db7bf-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>  
  
    -   <span data-ttu-id="db7bf-124">desteklemediğini (için bir yordam) bir değer döndürür</span><span class="sxs-lookup"><span data-stu-id="db7bf-124">whether or not it returns a value (for a procedure)</span></span>  
  
    -   <span data-ttu-id="db7bf-125">Dönüş değeri (dışında bir dönüşüm işleci) veri türü</span><span class="sxs-lookup"><span data-stu-id="db7bf-125">the data type of the return value (except for a conversion operator)</span></span>  
  
    -   <span data-ttu-id="db7bf-126">Tür parametreleri parametre adları</span><span class="sxs-lookup"><span data-stu-id="db7bf-126">the names of the parameters or type parameters</span></span>  
  
    -   <span data-ttu-id="db7bf-127">(için genel bir yordam) tür parametrelerindeki kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="db7bf-127">the constraints on the type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="db7bf-128">parametresi değiştiricisi anahtar sözcükler (gibi `ByRef` veya `Optional`)</span><span class="sxs-lookup"><span data-stu-id="db7bf-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>  
  
    -   <span data-ttu-id="db7bf-129">özellik veya yordam değiştiricisi anahtar sözcükler (gibi `Public` veya `Shared`)</span><span class="sxs-lookup"><span data-stu-id="db7bf-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>  
  
-   <span data-ttu-id="db7bf-130">**İsteğe bağlı değiştiricisi.**</span><span class="sxs-lookup"><span data-stu-id="db7bf-130">**Optional Modifier.**</span></span> <span data-ttu-id="db7bf-131">Kullanmak zorunda değil `Overloads` aynı sınıfta birden fazla aşırı yüklenmiş özellikler ya da yordamlar tanımlarken değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="db7bf-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="db7bf-132">Ancak, kullanırsanız `Overloads` bildirimleri her birinde, bunların tümünde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="db7bf-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>  
  
-   <span data-ttu-id="db7bf-133">**Gölgeleme ve aşırı yüklemesi.**</span><span class="sxs-lookup"><span data-stu-id="db7bf-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="db7bf-134">`Overloads` Ayrıca gölge var olan bir üye ya da bir taban sınıf içinde aşırı yüklenmiş üyeler kümesi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db7bf-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="db7bf-135">Kullandığınızda `Overloads` bu şekilde, özellik veya yöntem aynı adı ve temel sınıf üyesi ile aynı parametre listesine bildirme ve sağladığınız değil `Shadows` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="db7bf-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>  
  
 <span data-ttu-id="db7bf-136">Kullanırsanız `Overrides`, derleyici örtük olarak ekler `Overloads` kitaplığınızın API'leri iş böylece C# ile daha kolay.</span><span class="sxs-lookup"><span data-stu-id="db7bf-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="db7bf-137">`Overloads` Değiştiricisi bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="db7bf-137">The `Overloads` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="db7bf-138">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="db7bf-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="db7bf-139">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="db7bf-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="db7bf-140">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="db7bf-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="db7bf-141">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="db7bf-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="db7bf-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db7bf-142">See Also</span></span>  
 [<span data-ttu-id="db7bf-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="db7bf-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="db7bf-144">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="db7bf-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="db7bf-145">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="db7bf-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="db7bf-146">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="db7bf-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="db7bf-147">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="db7bf-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
