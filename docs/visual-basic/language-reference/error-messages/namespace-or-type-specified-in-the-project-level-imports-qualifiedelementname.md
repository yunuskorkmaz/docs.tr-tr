---
description: "Hakkında daha fazla bilgi edinin: BC40057: proje düzeyi Imports ' ' içinde belirtilen ad alanı veya tür <qualifiedelementname> ortak üye içermiyor veya bulunamıyor"
title: Proje düzeyi Imports '<qualifiedelementname>' içinde belirtilen ad alanı veya tür ortak üye içermiyor veya bulunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 66ae40ca6a2feff78f80bdbc8886387e801f7db2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795696"
---
# <a name="bc40057-namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="c590c-103">BC40057: proje düzeyi Imports ' ' içinde belirtilen ad alanı veya tür \<qualifiedelementname> ortak üye içermiyor veya bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="c590c-103">BC40057: Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="c590c-104">Proje düzeyi Imports ' ' içinde belirtilen ad alanı veya tür \<qualifiedelementname> ortak üye içermiyor veya bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="c590c-104">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="c590c-105">Ad alanının veya türün tanımlandığından ve en az bir ortak üye içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c590c-105">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="c590c-106">Diğer ad adının başka diğer adlar içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c590c-106">Make sure the alias name doesn't contain other aliases.</span></span>

 <span data-ttu-id="c590c-107">Projenin içeri aktarma özelliği, bulunamayan veya hiçbir üye tanımlamayan bir kapsayan öğe belirtiyor `Public` .</span><span class="sxs-lookup"><span data-stu-id="c590c-107">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

 <span data-ttu-id="c590c-108">*Kapsayan bir öğe* bir Namespace, Class, Structure, Module, Interface veya Enumeration olabilir.</span><span class="sxs-lookup"><span data-stu-id="c590c-108">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="c590c-109">Kapsayan öğe, değişkenler, yordamlar veya içerilen diğer öğeler gibi Üyeler içerir.</span><span class="sxs-lookup"><span data-stu-id="c590c-109">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

 <span data-ttu-id="c590c-110">İçeri aktarma amacı, kodunuzun ad alanına veya tür üyelerine, bunları nitelemek zorunda kalmadan erişmesine izin versağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="c590c-110">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="c590c-111">Projenizin ad alanına veya türe bir başvuru eklemesi de gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c590c-111">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="c590c-112">Daha fazla bilgi için, bkz. "Içerilen öğeleri Içeri aktarma", [belirtilen öğelerin başvuruları](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="c590c-112">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

 <span data-ttu-id="c590c-113">Derleyici belirtilen içeren öğeyi bulamazsa, onu kullanan başvuruları çözemez.</span><span class="sxs-lookup"><span data-stu-id="c590c-113">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="c590c-114">Öğe bulunursa ancak öğe hiçbir üye sunmadığında `Public` , hiçbir başvuru başarılı olmaz.</span><span class="sxs-lookup"><span data-stu-id="c590c-114">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="c590c-115">Her iki durumda da, öğesini içeri aktarmak anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="c590c-115">In either case it is meaningless to import the element.</span></span>

 <span data-ttu-id="c590c-116">İçeri aktarılacak öğeleri belirtmek için **Proje tasarımcısını** kullanın.</span><span class="sxs-lookup"><span data-stu-id="c590c-116">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="c590c-117">**Başvurular** sayfasının **içeri aktarılan ad alanları** bölümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="c590c-117">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="c590c-118">**Proje tasarımcısına** , **Çözüm Gezgini** içindeki **projem** simgesine çift tıklayarak ulaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c590c-118">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>

 <span data-ttu-id="c590c-119">**Hata kimliği:** BC40057</span><span class="sxs-lookup"><span data-stu-id="c590c-119">**Error ID:** BC40057</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c590c-120">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c590c-120">To correct this error</span></span>

1. <span data-ttu-id="c590c-121">**Proje tasarımcısını** açın ve **başvuru** sayfasına geçin.</span><span class="sxs-lookup"><span data-stu-id="c590c-121">Open the **Project Designer** and switch to the **Reference** page.</span></span>

2. <span data-ttu-id="c590c-122">**Içeri aktarılan ad alanları** bölümünde, içeren öğenin projenizden erişilebilir olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="c590c-122">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>

3. <span data-ttu-id="c590c-123">Kapsayan öğenin en az bir üye gösterdiğinden emin olun `Public` .</span><span class="sxs-lookup"><span data-stu-id="c590c-123">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="c590c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c590c-124">See also</span></span>

- [<span data-ttu-id="c590c-125">Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c590c-125">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [<span data-ttu-id="c590c-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="c590c-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="c590c-127">Genel</span><span class="sxs-lookup"><span data-stu-id="c590c-127">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="c590c-128">Visual Basic'de Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="c590c-128">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="c590c-129">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="c590c-129">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
