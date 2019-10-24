---
title: <namespacename> kök ad alanındaki <fullnamespacename> adı CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 821044d3ee359a052fa6a763e9c5a89da5d6f607
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775576"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a><span data-ttu-id="0f3ec-102">@No__t_1fullnamespacename > kök ad alanındaki > ad \<namespacename CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="0f3ec-102">Name \<namespacename> in the root namespace \<fullnamespacename> is not CLS-compliant</span></span>
<span data-ttu-id="0f3ec-103">Bir derleme `<CLSCompliant(True)>` olarak işaretlenir, ancak kök ad alanı adının bir öğesi bir alt çizgi (`_`) ile başlar.</span><span class="sxs-lookup"><span data-stu-id="0f3ec-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="0f3ec-104">Bir programlama öğesi bir veya daha fazla alt çizgi içerebilir, ancak [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olmak için bir alt çizgiyle başlamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f3ec-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="0f3ec-105">Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="0f3ec-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="0f3ec-106">Bir programlama öğesine <xref:System.CLSCompliantAttribute> ' ı uyguladığınızda, `isCompliant` parametresini `True` ' ye veya `False` ' ü, uyumluluk veya uyumsuzluk olduğunu gösterecek şekilde ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="0f3ec-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="0f3ec-107">Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f3ec-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="0f3ec-108">@No__t_0 bir öğeye uygulamazsanız, uyumsuz olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="0f3ec-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="0f3ec-109">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="0f3ec-109">By default, this message is a warning.</span></span> <span data-ttu-id="0f3ec-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0f3ec-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0f3ec-111">**Hata kimliği:** BC40039</span><span class="sxs-lookup"><span data-stu-id="0f3ec-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f3ec-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0f3ec-112">To correct this error</span></span>  
  
- <span data-ttu-id="0f3ec-113">CLS uyumluluğu gerekiyorsa, kök ad alanı adını değiştirerek öğelerinden hiçbiri alt çizgiyle başlamaktadır.</span><span class="sxs-lookup"><span data-stu-id="0f3ec-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
- <span data-ttu-id="0f3ec-114">Ad alanı adının değişmeden kalmasını gerektiriyorsa, <xref:System.CLSCompliantAttribute> derlemeden kaldırın veya `<CLSCompliant(False)>` olarak işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="0f3ec-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f3ec-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f3ec-115">See also</span></span>

- [<span data-ttu-id="0f3ec-116">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="0f3ec-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="0f3ec-117">Visual Basic ad alanları</span><span class="sxs-lookup"><span data-stu-id="0f3ec-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="0f3ec-118">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="0f3ec-118">-rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [<span data-ttu-id="0f3ec-119">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f3ec-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="0f3ec-120">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="0f3ec-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="0f3ec-121">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="0f3ec-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
