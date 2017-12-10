---
title: "Ad &lt;namespacename&gt; kök ad alanındaki &lt;fullnamespacename&gt; CLS uyumlu değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords: BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36de8b6a27c47e9e7192aed10e6b561bb0c07acc
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a><span data-ttu-id="f7a15-102">Ad &lt;namespacename&gt; kök ad alanındaki &lt;fullnamespacename&gt; CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="f7a15-102">Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="f7a15-103">Bir derlemeyi olarak işaretlenmiş `<CLSCompliant(True)>`, ancak kök ad alanı adı öğesi bir alt çizgi ile başlayan (`_`).</span><span class="sxs-lookup"><span data-stu-id="f7a15-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="f7a15-104">Bir programlama öğesi ile uyumlu olmak ancak bir veya daha fazla alt çizgi, içerebilir [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), alt çizgi ile değil başlamalı.</span><span class="sxs-lookup"><span data-stu-id="f7a15-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="f7a15-105">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="f7a15-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="f7a15-106">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f7a15-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="f7a15-107">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7a15-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="f7a15-108">Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f7a15-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="f7a15-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="f7a15-109">By default, this message is a warning.</span></span> <span data-ttu-id="f7a15-110">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f7a15-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f7a15-111">**Hata Kimliği:** BC40039</span><span class="sxs-lookup"><span data-stu-id="f7a15-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f7a15-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f7a15-112">To correct this error</span></span>  
  
-   <span data-ttu-id="f7a15-113">CLS uyumluluğu gerektiriyorsa, kök ad alanı adı öğelerinden hiçbiri alt çizgiyle başlıyorsa şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f7a15-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
-   <span data-ttu-id="f7a15-114">Ad alanı adı değişmeden gerektiriyorsa, ardından kaldırın <xref:System.CLSCompliantAttribute> derlemesinden veya olarak işaretlemek `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="f7a15-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a15-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7a15-115">See Also</span></span>  
 [<span data-ttu-id="f7a15-116">Namespace deyimi</span><span class="sxs-lookup"><span data-stu-id="f7a15-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="f7a15-117">Visual Basic'de ad alanları</span><span class="sxs-lookup"><span data-stu-id="f7a15-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="f7a15-118">/ RootNamespace</span><span class="sxs-lookup"><span data-stu-id="f7a15-118">/rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)  
 [<span data-ttu-id="f7a15-119">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7a15-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="f7a15-120">Bildirilen öğe adları</span><span class="sxs-lookup"><span data-stu-id="f7a15-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="f7a15-121">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="f7a15-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="f7a15-122">\<PAVE üzerinden > CLS uyumlu kod yazma</span><span class="sxs-lookup"><span data-stu-id="f7a15-122">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
