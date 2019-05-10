---
title: <namespacename> kök ad alanındaki <fullnamespacename> adı CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: faed46eaf21513945ef4eb0c76d36780e960d380
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592034"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a><span data-ttu-id="6fa0c-102">Adı \<namespacename > kök ad alanındaki \<fullnamespacename > CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="6fa0c-102">Name \<namespacename> in the root namespace \<fullnamespacename> is not CLS-compliant</span></span>
<span data-ttu-id="6fa0c-103">Bir derleme olarak işaretlenmiş `<CLSCompliant(True)>`, ancak bir öğe kök ad alanı adının alt çizgi ile başlar (`_`).</span><span class="sxs-lookup"><span data-stu-id="6fa0c-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="6fa0c-104">Bir programlama öğesi ile uyumlu olmak ancak bir veya daha fazla alt çizgi içerebilir [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) bir alt çizgiyle değil başlamalı.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="6fa0c-105">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="6fa0c-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="6fa0c-106">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesine özniteliğin ayarladığınız `isCompliant` ya da parametre `True` veya `False` uyumluluk veya uyumsuzluk belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="6fa0c-107">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="6fa0c-108">Geçerli <xref:System.CLSCompliantAttribute> bir öğe için uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="6fa0c-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-109">By default, this message is a warning.</span></span> <span data-ttu-id="6fa0c-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6fa0c-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="6fa0c-111">**Hata Kimliği:** BC40039</span><span class="sxs-lookup"><span data-stu-id="6fa0c-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6fa0c-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6fa0c-112">To correct this error</span></span>  
  
- <span data-ttu-id="6fa0c-113">CLS uyumluluğu gerektiriyorsa, böylece nBir öğelerinden bir alt çizgiyle başlayan kök ad alanı adı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
- <span data-ttu-id="6fa0c-114">Ad alanı adı değişmeden kalmasını gerektiriyorsa, ardından kaldırın <xref:System.CLSCompliantAttribute> derlemesinden veya olarak işaretlemek `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa0c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-115">See also</span></span>

- [<span data-ttu-id="6fa0c-116">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="6fa0c-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="6fa0c-117">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="6fa0c-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="6fa0c-118">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="6fa0c-118">/rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [<span data-ttu-id="6fa0c-119">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fa0c-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="6fa0c-120">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="6fa0c-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="6fa0c-121">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="6fa0c-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
