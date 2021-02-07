---
description: 'Daha fazla bilgi edinin: aşırı yüklemeler (Visual Basic)'
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
ms.openlocfilehash: 7f0b440b537500595e465d8aabc7724671f3ae95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730518"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="a0aea-103">Aşırı Yüklemeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0aea-103">Overloads (Visual Basic)</span></span>

<span data-ttu-id="a0aea-104">Bir özellik veya yordamın, aynı ada sahip bir veya daha fazla var olan özelliği ya da yordamları yeniden bildirdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0aea-104">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0aea-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0aea-105">Remarks</span></span>

<span data-ttu-id="a0aea-106">*Aşırı yükleme* , aynı kapsamda verilen bir özellik veya yordam adı için birden fazla tanım sağlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a0aea-106">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="a0aea-107">Farklı imzaya sahip bir özellik veya yordamın yeniden bildirilmesi bazen *imzaya göre gizleme* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a0aea-107">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>

## <a name="rules"></a><span data-ttu-id="a0aea-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="a0aea-108">Rules</span></span>

- <span data-ttu-id="a0aea-109">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="a0aea-109">**Declaration Context.**</span></span> <span data-ttu-id="a0aea-110">`Overloads`Yalnızca bir özellik veya yordam bildirimi ifadesinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0aea-110">You can use `Overloads` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="a0aea-111">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="a0aea-111">**Combined Modifiers.**</span></span> <span data-ttu-id="a0aea-112">`Overloads`Aynı yordam bildiriminde [gölgilerle](shadows.md) birlikte belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0aea-112">You cannot specify `Overloads` together with [Shadows](shadows.md) in the same procedure declaration.</span></span>

- <span data-ttu-id="a0aea-113">**Gerekli farklar.**</span><span class="sxs-lookup"><span data-stu-id="a0aea-113">**Required Differences.**</span></span> <span data-ttu-id="a0aea-114">Bu Bildirimdeki *imza* , aşırı yüklediği her özellik veya yordamın imzasıyla farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0aea-114">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="a0aea-115">İmza, özellik veya yordam adını aşağıdakiler ile birlikte içerir:</span><span class="sxs-lookup"><span data-stu-id="a0aea-115">The signature comprises the property or procedure name together with the following:</span></span>

  - <span data-ttu-id="a0aea-116">parametre sayısı</span><span class="sxs-lookup"><span data-stu-id="a0aea-116">the number of parameters</span></span>

  - <span data-ttu-id="a0aea-117">Parametrelerin sırası</span><span class="sxs-lookup"><span data-stu-id="a0aea-117">the order of the parameters</span></span>

  - <span data-ttu-id="a0aea-118">parametrelerin veri türleri</span><span class="sxs-lookup"><span data-stu-id="a0aea-118">the data types of the parameters</span></span>

  - <span data-ttu-id="a0aea-119">tür parametrelerinin sayısı (genel yordam için)</span><span class="sxs-lookup"><span data-stu-id="a0aea-119">the number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="a0aea-120">dönüş türü (yalnızca bir dönüştürme işleci yordamı için)</span><span class="sxs-lookup"><span data-stu-id="a0aea-120">the return type (only for a conversion operator procedure)</span></span>

  <span data-ttu-id="a0aea-121">Tüm aşırı yüklemeler aynı ada sahip olmalıdır, ancak her biri bir veya daha fazla önceki yönden daha fazla diğerlerinden farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0aea-121">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="a0aea-122">Bu, derleyicinin kodu özellik veya yordamı çağırdığında hangi sürümün kullanılacağını ayırt etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a0aea-122">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>

- <span data-ttu-id="a0aea-123">**İzin verilmeyen farklar.**</span><span class="sxs-lookup"><span data-stu-id="a0aea-123">**Disallowed Differences.**</span></span> <span data-ttu-id="a0aea-124">Aşağıdakilerden bir veya daha fazla değişiklik yapmak, imzanın bir parçası olmadıklarından bir özellik veya yordamı aşırı yüklemek için geçerli değildir:</span><span class="sxs-lookup"><span data-stu-id="a0aea-124">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>

  - <span data-ttu-id="a0aea-125">bir değer döndürüp döndürmeksizin (bir yordam için)</span><span class="sxs-lookup"><span data-stu-id="a0aea-125">whether or not it returns a value (for a procedure)</span></span>

  - <span data-ttu-id="a0aea-126">dönüş değerinin veri türü (dönüştürme işleci dışında)</span><span class="sxs-lookup"><span data-stu-id="a0aea-126">the data type of the return value (except for a conversion operator)</span></span>

  - <span data-ttu-id="a0aea-127">parametrelerin veya tür parametrelerinin adları</span><span class="sxs-lookup"><span data-stu-id="a0aea-127">the names of the parameters or type parameters</span></span>

  - <span data-ttu-id="a0aea-128">Tür Parametrelerindeki Kısıtlamalar (genel yordam için)</span><span class="sxs-lookup"><span data-stu-id="a0aea-128">the constraints on the type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="a0aea-129">parametre değiştirici anahtar sözcükleri ( `ByRef` veya gibi `Optional` )</span><span class="sxs-lookup"><span data-stu-id="a0aea-129">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>

  - <span data-ttu-id="a0aea-130">Özellik veya yordam değiştirici anahtar sözcükleri ( `Public` veya gibi `Shared` )</span><span class="sxs-lookup"><span data-stu-id="a0aea-130">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>

- <span data-ttu-id="a0aea-131">**İsteğe bağlı değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="a0aea-131">**Optional Modifier.**</span></span> <span data-ttu-id="a0aea-132">`Overloads`Aynı sınıfta birden fazla aşırı yüklenmiş özellik veya yordam tanımlarken değiştirici kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a0aea-132">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="a0aea-133">Ancak, `Overloads` bildirimlerden birinde kullanıyorsanız, bunların tümünde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0aea-133">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>

- <span data-ttu-id="a0aea-134">**Gölgeleme ve aşırı yükleme.**</span><span class="sxs-lookup"><span data-stu-id="a0aea-134">**Shadowing and Overloading.**</span></span> <span data-ttu-id="a0aea-135">`Overloads` , bir temel sınıfta varolan bir üyeyi veya aşırı yüklenmiş üyelerin gölgesini almak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a0aea-135">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="a0aea-136">`Overloads`Bu şekilde kullandığınızda, temel sınıf üyesiyle aynı ada ve aynı parametre listesine sahip özelliği veya yöntemi bildirirsiniz ve `Shadows` anahtar sözcüğünü sağlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="a0aea-136">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>

<span data-ttu-id="a0aea-137">Kullanırsanız `Overrides` , derleyici `Overloads` kitaplık API 'Lerinizin C# ile daha kolay çalışmasını sağlamak için örtülü olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="a0aea-137">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="a0aea-138">`Overloads`Değiştirici şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="a0aea-138">The `Overloads` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="a0aea-139">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0aea-139">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="a0aea-140">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0aea-140">Operator Statement</span></span>](../statements/operator-statement.md)

- [<span data-ttu-id="a0aea-141">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0aea-141">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="a0aea-142">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0aea-142">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="a0aea-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0aea-143">See also</span></span>

- [<span data-ttu-id="a0aea-144">Shadows</span><span class="sxs-lookup"><span data-stu-id="a0aea-144">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="a0aea-145">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="a0aea-145">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="a0aea-146">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="a0aea-146">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="a0aea-147">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="a0aea-147">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="a0aea-148">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="a0aea-148">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
