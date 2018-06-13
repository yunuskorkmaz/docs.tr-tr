---
title: Non-CLS ile uyumlu &lt;membername&gt; CLS uyumlu arabiriminde izin verilmiyor
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: ee533df5e06352034b24651b9173a88d090da0a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594152"
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="09a7d-102">Non-CLS ile uyumlu &lt;membername&gt; CLS uyumlu arabiriminde izin verilmiyor</span><span class="sxs-lookup"><span data-stu-id="09a7d-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="09a7d-103">Bir özellik, yordam veya olay arabirimdeki olarak işaretlenmiş `<CLSCompliant(True)>` zaman arabirimi olarak işaretli `<CLSCompliant(False)>` veya değil olarak işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="09a7d-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="09a7d-104">Uyumlu olması bir arabirim için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), tüm üyeleri olmalıdır uyumlu.</span><span class="sxs-lookup"><span data-stu-id="09a7d-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="09a7d-105">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="09a7d-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="09a7d-106">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="09a7d-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="09a7d-107">Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="09a7d-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="09a7d-108">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="09a7d-108">By default, this message is a warning.</span></span> <span data-ttu-id="09a7d-109">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="09a7d-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="09a7d-110">**Hata Kimliği:** BC40033</span><span class="sxs-lookup"><span data-stu-id="09a7d-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="09a7d-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="09a7d-111">To correct this error</span></span>  
  
-   <span data-ttu-id="09a7d-112">CLS uyumluluğu gerektiriyorsa ve arabirim kaynak kodu üzerinde denetim sahibi yoksa arabirimi olarak işaretlemek `<CLSCompliant(True)>` tüm üyeleri uyumlu olması durumunda.</span><span class="sxs-lookup"><span data-stu-id="09a7d-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="09a7d-113">CLS uyumluluğu gerektirir ve arabirim kaynak kodu üzerinde denetim sahibi değildir veya da uyumlu olması uygun değilse, bu üye içinde farklı bir arabirim tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="09a7d-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="09a7d-114">Bu üye, geçerli arabirimi içinde kalmasını gerekiyorsa kaldırma <xref:System.CLSCompliantAttribute> kendi tanımındaki veya olarak işaretlemek `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="09a7d-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a7d-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09a7d-115">See Also</span></span>  
 [<span data-ttu-id="09a7d-116">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="09a7d-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 
