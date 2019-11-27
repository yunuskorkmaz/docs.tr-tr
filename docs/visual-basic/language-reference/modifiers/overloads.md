---
title: Aşırı Yüklemeler
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
ms.openlocfilehash: 44823b409cfa81dc889aabacf101fac90bf851e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351403"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="5bb29-102">Aşırı Yüklemeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bb29-102">Overloads (Visual Basic)</span></span>

<span data-ttu-id="5bb29-103">Bir özellik veya yordamın, aynı ada sahip bir veya daha fazla var olan özelliği ya da yordamları yeniden bildirdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bb29-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5bb29-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5bb29-104">Remarks</span></span>

<span data-ttu-id="5bb29-105">*Aşırı yükleme* , aynı kapsamda verilen bir özellik veya yordam adı için birden fazla tanım sağlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="5bb29-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="5bb29-106">Farklı imzaya sahip bir özellik veya yordamın yeniden bildirilmesi bazen *imzaya göre gizleme*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5bb29-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>

## <a name="rules"></a><span data-ttu-id="5bb29-107">Kurallar</span><span class="sxs-lookup"><span data-stu-id="5bb29-107">Rules</span></span>

- <span data-ttu-id="5bb29-108">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="5bb29-108">**Declaration Context.**</span></span> <span data-ttu-id="5bb29-109">Yalnızca bir özellik veya yordam bildirimi ifadesinde `Overloads` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bb29-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="5bb29-110">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="5bb29-110">**Combined Modifiers.**</span></span> <span data-ttu-id="5bb29-111">Aynı yordam bildiriminde [gölgilerle](../../../visual-basic/language-reference/modifiers/shadows.md) birlikte `Overloads` belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bb29-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>

- <span data-ttu-id="5bb29-112">**Gerekli farklar.**</span><span class="sxs-lookup"><span data-stu-id="5bb29-112">**Required Differences.**</span></span> <span data-ttu-id="5bb29-113">Bu Bildirimdeki *imza* , aşırı yüklediği her özellik veya yordamın imzasıyla farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5bb29-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="5bb29-114">İmza, özellik veya yordam adını aşağıdakiler ile birlikte içerir:</span><span class="sxs-lookup"><span data-stu-id="5bb29-114">The signature comprises the property or procedure name together with the following:</span></span>

  - <span data-ttu-id="5bb29-115">parametre sayısı</span><span class="sxs-lookup"><span data-stu-id="5bb29-115">the number of parameters</span></span>

  - <span data-ttu-id="5bb29-116">Parametrelerin sırası</span><span class="sxs-lookup"><span data-stu-id="5bb29-116">the order of the parameters</span></span>

  - <span data-ttu-id="5bb29-117">parametrelerin veri türleri</span><span class="sxs-lookup"><span data-stu-id="5bb29-117">the data types of the parameters</span></span>

  - <span data-ttu-id="5bb29-118">tür parametrelerinin sayısı (genel yordam için)</span><span class="sxs-lookup"><span data-stu-id="5bb29-118">the number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="5bb29-119">dönüş türü (yalnızca bir dönüştürme işleci yordamı için)</span><span class="sxs-lookup"><span data-stu-id="5bb29-119">the return type (only for a conversion operator procedure)</span></span>

  <span data-ttu-id="5bb29-120">Tüm aşırı yüklemeler aynı ada sahip olmalıdır, ancak her biri bir veya daha fazla önceki yönden daha fazla diğerlerinden farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5bb29-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="5bb29-121">Bu, derleyicinin kodu özellik veya yordamı çağırdığında hangi sürümün kullanılacağını ayırt etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5bb29-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>

- <span data-ttu-id="5bb29-122">**İzin verilmeyen farklar.**</span><span class="sxs-lookup"><span data-stu-id="5bb29-122">**Disallowed Differences.**</span></span> <span data-ttu-id="5bb29-123">Aşağıdakilerden bir veya daha fazla değişiklik yapmak, imzanın bir parçası olmadıklarından bir özellik veya yordamı aşırı yüklemek için geçerli değildir:</span><span class="sxs-lookup"><span data-stu-id="5bb29-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>

  - <span data-ttu-id="5bb29-124">bir değer döndürüp döndürmeksizin (bir yordam için)</span><span class="sxs-lookup"><span data-stu-id="5bb29-124">whether or not it returns a value (for a procedure)</span></span>

  - <span data-ttu-id="5bb29-125">Dönüş değerinin veri türü (dönüştürme işleci dışında)</span><span class="sxs-lookup"><span data-stu-id="5bb29-125">the data type of the return value (except for a conversion operator)</span></span>

  - <span data-ttu-id="5bb29-126">parametrelerin veya tür parametrelerinin adları</span><span class="sxs-lookup"><span data-stu-id="5bb29-126">the names of the parameters or type parameters</span></span>

  - <span data-ttu-id="5bb29-127">Tür Parametrelerindeki Kısıtlamalar (genel yordam için)</span><span class="sxs-lookup"><span data-stu-id="5bb29-127">the constraints on the type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="5bb29-128">parametre değiştirici anahtar sözcükleri (`ByRef` veya `Optional`gibi)</span><span class="sxs-lookup"><span data-stu-id="5bb29-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>

  - <span data-ttu-id="5bb29-129">Özellik veya yordam değiştirici anahtar sözcükleri (`Public` veya `Shared`gibi)</span><span class="sxs-lookup"><span data-stu-id="5bb29-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>

- <span data-ttu-id="5bb29-130">**İsteğe bağlı değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="5bb29-130">**Optional Modifier.**</span></span> <span data-ttu-id="5bb29-131">Aynı sınıfta birden fazla aşırı yüklenmiş özellik veya yordam tanımlarken `Overloads` değiştiricisini kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5bb29-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="5bb29-132">Ancak, bildirimlerden birinde `Overloads` kullanıyorsanız, bunların tümünde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5bb29-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>

- <span data-ttu-id="5bb29-133">**Gölgeleme ve aşırı yükleme.**</span><span class="sxs-lookup"><span data-stu-id="5bb29-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="5bb29-134">`Overloads`, bir temel sınıfta varolan bir üyeyi veya aşırı yüklenmiş Üyeler kümesini gölgelendirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5bb29-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="5bb29-135">`Overloads` bu şekilde kullandığınızda, temel sınıf üyesiyle aynı ada ve aynı parametre listesine sahip olan özelliği veya yöntemi bildirirsiniz ve `Shadows` anahtar sözcüğünü sağlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="5bb29-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>

<span data-ttu-id="5bb29-136">`Overrides`kullanırsanız, derleyici kitaplık API 'lerinizin C# daha kolay bir şekilde çalışması için `Overloads` dolaylı olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="5bb29-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="5bb29-137">`Overloads` değiştiricisi şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="5bb29-137">The `Overloads` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="5bb29-138">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="5bb29-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="5bb29-139">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="5bb29-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)

- [<span data-ttu-id="5bb29-140">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="5bb29-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="5bb29-141">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="5bb29-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="5bb29-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bb29-142">See also</span></span>

- [<span data-ttu-id="5bb29-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="5bb29-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="5bb29-144">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="5bb29-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="5bb29-145">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="5bb29-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="5bb29-146">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="5bb29-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="5bb29-147">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="5bb29-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
