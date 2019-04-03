---
title: Proje düzeyi Imports '<qualifiedelementname>' içinde belirtilen ad alanı veya tür ortak üye içermiyor veya bulunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 554300f87dbfca351ebcd2d544051968e84880ab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816834"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="d6145-102">Belirtilen proje düzeyi Imports Namespace veya tür\<qualifiedelementname >', genel üye içermiyor veya bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="d6145-102">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>
<span data-ttu-id="d6145-103">Belirtilen proje düzeyi Imports Namespace veya tür\<qualifiedelementname >', genel üye içermiyor veya bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="d6145-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="d6145-104">Ad alanı veya tür tanımlanır ve en az bir ortak üye içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d6145-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="d6145-105">Diğer ad başka diğer adlar içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d6145-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="d6145-106">Bir projenin bir içeri aktarma özelliği bulunamıyor ya da tüm tanımlamıyor içeren bir öğeyi belirtir `Public` üyeleri.</span><span class="sxs-lookup"><span data-stu-id="d6145-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="d6145-107">A *öğeyi içeren* bir ad alanı, sınıf, yapı, modülü, arabirimi veya sabit listesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6145-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="d6145-108">Kapsayıcı öğe üyeleri, değişkenleri, yordamları veya içeren diğer öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d6145-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="d6145-109">İçeri aktarma amacı, bunları uygun zorunda kalmadan kodunuzu ad alanı veya tür üyelerine erişmek için izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="d6145-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="d6145-110">Projenizi de ad alanı veya tür için bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d6145-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="d6145-111">Daha fazla bilgi için "İçeren öğeleri içeri aktarma" bölümüne bakın. [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="d6145-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="d6145-112">Derleyiciye belirtilen kapsayıcı öğe bulamazsa, kullanılmakta başvuru çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="d6145-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="d6145-113">Öğeyi bulur ancak öğe herhangi kullanıma sunmuyor `Public` üyeleri, ardından hiçbir başvurusu olabilir başarılı.</span><span class="sxs-lookup"><span data-stu-id="d6145-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="d6145-114">Her iki durumda da, içeri aktarma öğesi anlamsız.</span><span class="sxs-lookup"><span data-stu-id="d6145-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="d6145-115">Kullandığınız **Proje Tasarımcısı** almak için öğeleri belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="d6145-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="d6145-116">Kullanım **içeri aktarılan ad alanlarını** bölümünü **başvuruları** sayfası.</span><span class="sxs-lookup"><span data-stu-id="d6145-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="d6145-117">Ulaşmak için **Proje Tasarımcısı** çift tıklayarak **Projem** simgesini **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="d6145-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="d6145-118">**Hata Kimliği:** BC40057</span><span class="sxs-lookup"><span data-stu-id="d6145-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d6145-119">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d6145-119">To correct this error</span></span>  
  
1.  <span data-ttu-id="d6145-120">Açık **Proje Tasarımcısı** geçin **başvuru** sayfası.</span><span class="sxs-lookup"><span data-stu-id="d6145-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2.  <span data-ttu-id="d6145-121">İçinde **içeri aktarılan ad alanlarını** bölümünde, kapsayıcı öğe projenizden erişilebilir olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="d6145-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3.  <span data-ttu-id="d6145-122">Kapsayıcı öğe en az bir sunan doğrulayın `Public` üyesi.</span><span class="sxs-lookup"><span data-stu-id="d6145-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6145-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6145-123">See also</span></span>

- [<span data-ttu-id="d6145-124">Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6145-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [<span data-ttu-id="d6145-125">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="d6145-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="d6145-126">Public</span><span class="sxs-lookup"><span data-stu-id="d6145-126">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="d6145-127">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="d6145-127">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="d6145-128">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="d6145-128">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
