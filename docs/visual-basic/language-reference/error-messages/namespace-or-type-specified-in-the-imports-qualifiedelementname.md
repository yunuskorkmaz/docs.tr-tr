---
title: Imports '<qualifiedelementname>' içinde belirtilen ad alanı veya tür ortak üye içermiyor veya bulunamıyor
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: d19a769b33b3b63b7f431b73841f49632e41f9e6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288281"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="1e8e1-102">Imports belirtilen Namespace veya tür\<qualifiedelementname >', genel üye içermiyor veya bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="1e8e1-102">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>
<span data-ttu-id="1e8e1-103">Imports belirtilen Namespace veya tür\<qualifiedelementname >', genel üye içermiyor veya bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="1e8e1-104">Ad alanı veya tür tanımlanır ve en az bir ortak üye içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="1e8e1-105">Diğer ad başka diğer adlar içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="1e8e1-106">Bir `Imports` deyimi belirtir bulunamıyor ya da tüm tanımlamıyor içeren bir öğe `Public` üyeleri.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="1e8e1-107">A *öğeyi içeren* bir ad alanı, sınıf, yapı, modülü, arabirimi veya sabit listesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="1e8e1-108">Kapsayıcı öğe üyeleri, değişkenleri, yordamları veya içeren diğer öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="1e8e1-109">İçeri aktarma amacı, bunları uygun zorunda kalmadan kodunuzu ad alanı veya tür üyelerine erişmek için izin vermektir.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="1e8e1-110">Projenizi de ad alanı veya tür için bir başvuru eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="1e8e1-111">Daha fazla bilgi için "İçeren öğeleri içeri aktarma" bölümüne bakın. [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="1e8e1-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="1e8e1-112">Derleyiciye belirtilen kapsayıcı öğe bulamazsa, kullanılmakta başvuru çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="1e8e1-113">Öğeyi bulur ancak öğe herhangi kullanıma sunmuyor `Public` üyeleri, ardından hiçbir başvurusu olabilir başarılı.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="1e8e1-114">Her iki durumda da, içeri aktarma öğesi anlamsız.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="1e8e1-115">Bir kapsayıcı öğe içeri aktarma ve içeri aktarma diğer ad atayın, ardından bu içeri aktarma diğer ad başka bir öğe almak için kullanamazsınız olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="1e8e1-116">Aşağıdaki kod bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-116">The following code generates a compiler error.</span></span>  
  
 <span data-ttu-id="1e8e1-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span><span class="sxs-lookup"><span data-stu-id="1e8e1-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span></span>  
  
 <span data-ttu-id="1e8e1-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span><span class="sxs-lookup"><span data-stu-id="1e8e1-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span></span>  
  
 <span data-ttu-id="1e8e1-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span><span class="sxs-lookup"><span data-stu-id="1e8e1-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span></span>  
  
 <span data-ttu-id="1e8e1-120">**Hata Kimliği:** BC40056</span><span class="sxs-lookup"><span data-stu-id="1e8e1-120">**Error ID:** BC40056</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1e8e1-121">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1e8e1-121">To correct this error</span></span>  
  
1.  <span data-ttu-id="1e8e1-122">Kapsayıcı öğe projenizden erişilebilir olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-122">Verify that the containing element is accessible from your project.</span></span>  
  
2.  <span data-ttu-id="1e8e1-123">Kapsayıcı öğe belirtimi başka bir içeri aktarma ad alanından başka bir içeri aktarma içerip içermediğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-123">Verify that the specification of the containing element does not include any import alias from another import.</span></span>  
  
3.  <span data-ttu-id="1e8e1-124">Kapsayıcı öğe en az bir sunan doğrulayın `Public` üyesi.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-124">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e8e1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-125">See also</span></span>
- [<span data-ttu-id="1e8e1-126">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="1e8e1-126">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="1e8e1-127">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="1e8e1-127">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="1e8e1-128">Public</span><span class="sxs-lookup"><span data-stu-id="1e8e1-128">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="1e8e1-129">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="1e8e1-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="1e8e1-130">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="1e8e1-130">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
