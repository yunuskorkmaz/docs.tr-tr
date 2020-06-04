---
title: CLS uyumlu olmayan <membername> öğesine CLS uyumlu arabirimde izin verilmez.
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: e572189b958612bf9527c82ce702df3ab929a23f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409406"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="62bb6-102">CLS uyumlu olmayan \<membername> öğesine CLS uyumlu arabirimde izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="62bb6-102">Non-CLS-compliant \<membername> is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="62bb6-103">Arabirimdeki bir özellik, yordam veya olay, `<CLSCompliant(True)>` arabirimin kendisi olarak işaretlendiğinde `<CLSCompliant(False)>` veya işaretlenmediğinde olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="62bb6-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="62bb6-104">Bir arabirimin, [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için tüm üyelerinin uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="62bb6-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="62bb6-105"><xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="62bb6-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="62bb6-106">Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="62bb6-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="62bb6-107"><xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="62bb6-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="62bb6-108">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="62bb6-108">By default, this message is a warning.</span></span> <span data-ttu-id="62bb6-109">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="62bb6-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="62bb6-110">**Hata kimliği:** BC40033</span><span class="sxs-lookup"><span data-stu-id="62bb6-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="62bb6-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="62bb6-111">To correct this error</span></span>  
  
- <span data-ttu-id="62bb6-112">CLS uyumluluğuna ihtiyacınız varsa ve arabirim kaynak kodu üzerinde denetiminiz varsa, arabirimi `<CLSCompliant(True)>` tüm üyeleri uyumlu olduğu gibi işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="62bb6-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
- <span data-ttu-id="62bb6-113">CLS uyumluluğu varsa ve arabirim kaynak kodu üzerinde denetiminiz yoksa veya uyumlu hale getirmek için uygun değilse, bu üyeyi farklı bir arabirim içinde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="62bb6-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
- <span data-ttu-id="62bb6-114">Bu üyenin geçerli arabiriminde kalmasını gerektiriyorsa, öğesini <xref:System.CLSCompliantAttribute> tanımından kaldırın veya olarak işaretleyin `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="62bb6-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62bb6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62bb6-115">See also</span></span>

- [<span data-ttu-id="62bb6-116">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="62bb6-116">Interface Statement</span></span>](../statements/interface-statement.md)
