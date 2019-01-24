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
ms.openlocfilehash: b20dbf20c580d08553ae22f6a62ee33a7354db74
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624924"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="40453-102">Aşırı Yüklemeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40453-102">Overloads (Visual Basic)</span></span>
<span data-ttu-id="40453-103">Bir özelliğin ya da yordamın bir veya daha fazla var olan özellikler veya aynı ada sahip yordamları gizlediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="40453-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40453-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40453-104">Remarks</span></span>  
 <span data-ttu-id="40453-105">*Aşırı yükleme* aynı kapsamda belirli bir özellik veya yordam adı için birden fazla tanım sağlayan uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="40453-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="40453-106">Bir özellik veya yordamı farklı imzayla redeclaring bazen adlı *imzaya göre gizleme*.</span><span class="sxs-lookup"><span data-stu-id="40453-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="40453-107">Kurallar</span><span class="sxs-lookup"><span data-stu-id="40453-107">Rules</span></span>  
  
-   <span data-ttu-id="40453-108">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="40453-108">**Declaration Context.**</span></span> <span data-ttu-id="40453-109">Kullanabileceğiniz `Overloads` yalnızca bir özellik veya yordamı bildirim deyiminde.</span><span class="sxs-lookup"><span data-stu-id="40453-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="40453-110">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="40453-110">**Combined Modifiers.**</span></span> <span data-ttu-id="40453-111">Belirtemezsiniz `Overloads` ile birlikte [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) aynı yordam bildirimi.</span><span class="sxs-lookup"><span data-stu-id="40453-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>  
  
-   <span data-ttu-id="40453-112">**Farklar gereklidir.**</span><span class="sxs-lookup"><span data-stu-id="40453-112">**Required Differences.**</span></span> <span data-ttu-id="40453-113">*İmza* Bu bildirimde her bir özellik veya aşırı yordamı imzasının farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40453-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="40453-114">İmza özelliği ya da yordamın adı ile birlikte aşağıdaki oluşur:</span><span class="sxs-lookup"><span data-stu-id="40453-114">The signature comprises the property or procedure name together with the following:</span></span>  
  
    -   <span data-ttu-id="40453-115">parametre sayısı</span><span class="sxs-lookup"><span data-stu-id="40453-115">the number of parameters</span></span>  
  
    -   <span data-ttu-id="40453-116">Parametreler sırası</span><span class="sxs-lookup"><span data-stu-id="40453-116">the order of the parameters</span></span>  
  
    -   <span data-ttu-id="40453-117">parametrelerinin veri türleri</span><span class="sxs-lookup"><span data-stu-id="40453-117">the data types of the parameters</span></span>  
  
    -   <span data-ttu-id="40453-118">Tür parametreleri (için genel bir yordam) sayısı</span><span class="sxs-lookup"><span data-stu-id="40453-118">the number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="40453-119">dönüş türü (yalnızca bir dönüştürme işleci yordam)</span><span class="sxs-lookup"><span data-stu-id="40453-119">the return type (only for a conversion operator procedure)</span></span>  
  
     <span data-ttu-id="40453-120">Tüm aşırı yüklemeler aynı ada sahip olmalıdır, ancak her diğer tüm kişilerden gelen bir veya daha önceki gizliliğinize farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40453-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="40453-121">Bu özellik veya yordam kodu çağırdığında, kullanılacak hangi sürümünü ayırt etmek derleyicinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="40453-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>  
  
-   <span data-ttu-id="40453-122">**İzin verilmeyen farklar.**</span><span class="sxs-lookup"><span data-stu-id="40453-122">**Disallowed Differences.**</span></span> <span data-ttu-id="40453-123">Bir veya daha fazlasını değiştirme, imzasının parçası olmadıklarından bir özelliği ya da yordamın, aşırı yükleme için geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="40453-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>  
  
    -   <span data-ttu-id="40453-124">(bir yordam için) bir değer olup olmadığını döndürür</span><span class="sxs-lookup"><span data-stu-id="40453-124">whether or not it returns a value (for a procedure)</span></span>  
  
    -   <span data-ttu-id="40453-125">(bir dönüşüm işleci dışında) dönüş değerinin veri türü</span><span class="sxs-lookup"><span data-stu-id="40453-125">the data type of the return value (except for a conversion operator)</span></span>  
  
    -   <span data-ttu-id="40453-126">Tür parametreleri ve parametre adları</span><span class="sxs-lookup"><span data-stu-id="40453-126">the names of the parameters or type parameters</span></span>  
  
    -   <span data-ttu-id="40453-127">(için genel bir yordam) tür parametrelerindeki kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="40453-127">the constraints on the type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="40453-128">parametre değiştiricisi anahtar sözcükleri (gibi `ByRef` veya `Optional`)</span><span class="sxs-lookup"><span data-stu-id="40453-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>  
  
    -   <span data-ttu-id="40453-129">özellik veya yordamı değiştiricisi anahtar sözcükleri (gibi `Public` veya `Shared`)</span><span class="sxs-lookup"><span data-stu-id="40453-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>  
  
-   <span data-ttu-id="40453-130">**İsteğe bağlı bir değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="40453-130">**Optional Modifier.**</span></span> <span data-ttu-id="40453-131">Kullanmak zorunda değil `Overloads` aynı sınıf içinde birden fazla aşırı yüklenmiş özellikler ya da yordamlar tanımlarken değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="40453-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="40453-132">Ancak, kullanırsanız `Overloads` bildirimleri her birinde, bunların tümünde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40453-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>  
  
-   <span data-ttu-id="40453-133">**Gölgeleme ve aşırı yükleme.**</span><span class="sxs-lookup"><span data-stu-id="40453-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="40453-134">`Overloads` Ayrıca varolan bir üye gölge ya da taban sınıfında aşırı yüklenmiş üyelerin kümesini kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40453-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="40453-135">Kullanırken `Overloads` bu şekilde, özellik veya yöntem ile aynı ada ve aynı parametre listesi temel sınıf üye olarak bildirmek ve sağladığınız değil `Shadows` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="40453-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>  
  
 <span data-ttu-id="40453-136">Kullanırsanız `Overrides`, derleyicinin dolaylı olarak ekler `Overloads` kitaplığınızı API'leri ile çalışmak üzere C# daha kolay.</span><span class="sxs-lookup"><span data-stu-id="40453-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="40453-137">`Overloads` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="40453-137">The `Overloads` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="40453-138">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="40453-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="40453-139">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="40453-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="40453-140">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="40453-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="40453-141">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="40453-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="40453-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40453-142">See also</span></span>
- [<span data-ttu-id="40453-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="40453-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="40453-144">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="40453-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="40453-145">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="40453-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="40453-146">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="40453-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="40453-147">Nasıl yapılır: Bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="40453-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
