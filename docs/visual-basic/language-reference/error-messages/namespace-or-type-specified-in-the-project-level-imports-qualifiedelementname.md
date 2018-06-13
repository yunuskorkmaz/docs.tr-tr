---
title: Namespace veya türü belirtilen proje düzeyi içeri aktarmalar içinde &#39; &lt;qualifiedelementname&gt; &#39; mevcut değil&#39;t ortak üye içermiyor ya da bulunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: d6d0c931262d892ec3e65888a76f25218b23d868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595819"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="0e51e-102">Namespace veya türü belirtilen proje düzeyi içeri aktarmalar içinde &#39; &lt;qualifiedelementname&gt; &#39; mevcut değil&#39;t ortak üye içermiyor ya da bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="0e51e-102">Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="0e51e-103">Namespace veya türü belirtilen proje düzeyi içeri aktarmalar içinde\<qualifiedelementname >' ortak üye içermiyor veya bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="0e51e-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="0e51e-104">Ad alanı veya tür tanımlanır ve en az bir ortak üye içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0e51e-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="0e51e-105">Diğer ad başka diğer adlar içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0e51e-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="0e51e-106">Projenin bir alma özellik bulunamıyor veya herhangi bir tanımlamıyor içeren bir öğeyi belirtir `Public` üyeleri.</span><span class="sxs-lookup"><span data-stu-id="0e51e-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="0e51e-107">A *öğeyi içeren* bir ad alanı, sınıf, yapı, modülü, arabirimi veya numaralandırması olabilir.</span><span class="sxs-lookup"><span data-stu-id="0e51e-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="0e51e-108">Üye değişkenleri, yordamlar ve içeren diğer öğeler gibi içeren öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="0e51e-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="0e51e-109">İçeri aktarma amacı bunları uygun gerek kalmadan kodunuzu erişim ad alanı veya tür üyeleri için izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="0e51e-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="0e51e-110">Projenizi de ad alanı veya türü bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0e51e-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="0e51e-111">Daha fazla bilgi için bkz: "İçeren öğelerini içe aktarma" [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="0e51e-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="0e51e-112">Derleyici belirtilen içeren öğe bulamazsanız, bunu kullanan başvuruları çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="0e51e-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="0e51e-113">Öğeyi bulur ancak öğe herhangi kullanıma sunmuyor `Public` üyeleri sonra hiçbir başvurusu olabilir başarılı.</span><span class="sxs-lookup"><span data-stu-id="0e51e-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="0e51e-114">Her iki durumda da içeri aktarma öğesi anlamsız hale gelir.</span><span class="sxs-lookup"><span data-stu-id="0e51e-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="0e51e-115">Kullandığınız **Proje Tasarımcısı** almak için öğeleri belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="0e51e-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="0e51e-116">Kullanım **içeri aktarılan ad alanları** bölümünü **başvuruları** sayfası.</span><span class="sxs-lookup"><span data-stu-id="0e51e-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="0e51e-117">İçin edinebilirsiniz **Proje Tasarımcısı** çift tıklatarak **My proje** simgesine **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="0e51e-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="0e51e-118">**Hata Kimliği:** BC40057</span><span class="sxs-lookup"><span data-stu-id="0e51e-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0e51e-119">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0e51e-119">To correct this error</span></span>  
  
1.  <span data-ttu-id="0e51e-120">Açık **Proje Tasarımcısı** ve geçiş **başvuru** sayfası.</span><span class="sxs-lookup"><span data-stu-id="0e51e-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2.  <span data-ttu-id="0e51e-121">İçinde **içeri aktarılan ad alanları** bölümünde, kapsayan öğe projenizden erişilebilir olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="0e51e-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3.  <span data-ttu-id="0e51e-122">İçeren öğesi en az bir gösterir doğrulayın `Public` üyesi.</span><span class="sxs-lookup"><span data-stu-id="0e51e-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e51e-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e51e-123">See Also</span></span>  
 [<span data-ttu-id="0e51e-124">Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e51e-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)  
 [<span data-ttu-id="0e51e-125">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="0e51e-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="0e51e-126">Public</span><span class="sxs-lookup"><span data-stu-id="0e51e-126">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="0e51e-127">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="0e51e-127">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="0e51e-128">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="0e51e-128">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
