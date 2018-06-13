---
title: Ad &lt;membername&gt; CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 26ff13de461d5a96724868b7928129a326cdf1d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593348"
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a><span data-ttu-id="6a1dd-102">Ad &lt;membername&gt; CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="6a1dd-102">Name &lt;membername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="6a1dd-103">Bir derlemeyi olarak işaretlenmiş `<CLSCompliant(True)>` ancak bir alt çizgi ile başlayan bir ada sahip bir üye gösterir (`_`).</span><span class="sxs-lookup"><span data-stu-id="6a1dd-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="6a1dd-104">Bir programlama öğesi ile uyumlu olmak ancak bir veya daha fazla alt çizgi, içerebilir [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), alt çizgi ile değil başlamalı.</span><span class="sxs-lookup"><span data-stu-id="6a1dd-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="6a1dd-105">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="6a1dd-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="6a1dd-106">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6a1dd-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="6a1dd-107">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6a1dd-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="6a1dd-108">Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6a1dd-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="6a1dd-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="6a1dd-109">By default, this message is a warning.</span></span> <span data-ttu-id="6a1dd-110">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6a1dd-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="6a1dd-111">**Hata Kimliği:** BC40031</span><span class="sxs-lookup"><span data-stu-id="6a1dd-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6a1dd-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6a1dd-112">To correct this error</span></span>  
  
-   <span data-ttu-id="6a1dd-113">Kaynak kodu denetim varsa, üye adı alt çizgi ile başlamıyor şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6a1dd-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
-   <span data-ttu-id="6a1dd-114">Üye adı değişmeden gerekiyorsa kaldırma <xref:System.CLSCompliantAttribute> kendi tanımındaki veya olarak işaretlemek `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="6a1dd-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="6a1dd-115">Derleme olarak hala işaretleyebilirsiniz `<CLSCompliant(True)>`.</span><span class="sxs-lookup"><span data-stu-id="6a1dd-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a1dd-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a1dd-116">See Also</span></span>  
 [<span data-ttu-id="6a1dd-117">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="6a1dd-117">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="6a1dd-118">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="6a1dd-118">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  

