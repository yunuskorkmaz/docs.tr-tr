---
title: Namespace veya türü içeri aktarmalar içinde belirtilen &#39; &lt;qualifiedelementname&gt; &#39; mevcut değil&#39;t ortak üye içermiyor ya da bulunamıyor
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8be0df5cbe4b8d4a640c9b6c2e126b3828254fd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595111"
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="e4ffb-102">Namespace veya türü içeri aktarmalar içinde belirtilen &#39; &lt;qualifiedelementname&gt; &#39; mevcut değil&#39;t ortak üye içermiyor ya da bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="e4ffb-102">Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="e4ffb-103">Namespace veya türü belirtilen içeri aktarmalar içinde\<qualifiedelementname >' ortak üye içermiyor veya bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="e4ffb-104">Ad alanı veya tür tanımlanır ve en az bir ortak üye içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="e4ffb-105">Diğer ad başka diğer adlar içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="e4ffb-106">Bir `Imports` deyimi belirtir bulunamıyor veya herhangi bir tanımlamıyor içeren bir öğeyi `Public` üyeleri.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="e4ffb-107">A *öğeyi içeren* bir ad alanı, sınıf, yapı, modülü, arabirimi veya numaralandırması olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="e4ffb-108">Üye değişkenleri, yordamlar ve içeren diğer öğeler gibi içeren öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="e4ffb-109">İçeri aktarma amacı bunları uygun gerek kalmadan kodunuzu erişim ad alanı veya tür üyeleri için izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="e4ffb-110">Projenizi de ad alanı veya türü bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="e4ffb-111">Daha fazla bilgi için bkz: "İçeren öğelerini içe aktarma" [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="e4ffb-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="e4ffb-112">Derleyici belirtilen içeren öğe bulamazsanız, bunu kullanan başvuruları çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="e4ffb-113">Öğeyi bulur ancak öğe herhangi kullanıma sunmuyor `Public` üyeleri sonra hiçbir başvurusu olabilir başarılı.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="e4ffb-114">Her iki durumda da içeri aktarma öğesi anlamsız hale gelir.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="e4ffb-115">İçeren bir öğe içeri aktarma ve içeri aktarma diğer ad atayın, ardından bu içeri aktarma diğer ad başka bir öğe içeri aktarmak için kullanamazsınız olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="e4ffb-116">Aşağıdaki kod derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-116">The following code generates a compiler error.</span></span>  
  
 <span data-ttu-id="e4ffb-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span><span class="sxs-lookup"><span data-stu-id="e4ffb-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span></span>  
  
 <span data-ttu-id="e4ffb-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span><span class="sxs-lookup"><span data-stu-id="e4ffb-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span></span>  
  
 <span data-ttu-id="e4ffb-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span><span class="sxs-lookup"><span data-stu-id="e4ffb-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span></span>  
  
 <span data-ttu-id="e4ffb-120">**Hata Kimliği:** BC40056</span><span class="sxs-lookup"><span data-stu-id="e4ffb-120">**Error ID:** BC40056</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e4ffb-121">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e4ffb-121">To correct this error</span></span>  
  
1.  <span data-ttu-id="e4ffb-122">Kapsayan öğe projenizden erişilebilir olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-122">Verify that the containing element is accessible from your project.</span></span>  
  
2.  <span data-ttu-id="e4ffb-123">İçeren öğesinin belirtimini herhangi alma diğer başka bir içeri aktarma adından içermez doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-123">Verify that the specification of the containing element does not include any import alias from another import.</span></span>  
  
3.  <span data-ttu-id="e4ffb-124">İçeren öğesi en az bir gösterir doğrulayın `Public` üyesi.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-124">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ffb-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4ffb-125">See Also</span></span>  
 [<span data-ttu-id="e4ffb-126">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="e4ffb-126">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="e4ffb-127">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="e4ffb-127">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="e4ffb-128">Public</span><span class="sxs-lookup"><span data-stu-id="e4ffb-128">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="e4ffb-129">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="e4ffb-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="e4ffb-130">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="e4ffb-130">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
