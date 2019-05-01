---
title: CLS uyumlu olmayan <membername> öğesine CLS uyumlu arabirimde izin verilmez.
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: dbffe2bd196e798b90104aebb74269387660c794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918209"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="11288-102">CLS uyumlu olmayan \<membername > CLS uyumlu arabirimde izin verilmez</span><span class="sxs-lookup"><span data-stu-id="11288-102">Non-CLS-compliant \<membername> is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="11288-103">Bir özellik, yordam veya bir arabirim olay olarak işaretlenmiş `<CLSCompliant(True)>` olarak arabirimi işaretlendiğinde `<CLSCompliant(False)>` veya hiçbir işaret konulmadıysa.</span><span class="sxs-lookup"><span data-stu-id="11288-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="11288-104">Bir arabirim ile uyumlu olması için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), tüm üyeleri olmalıdır uyumlu.</span><span class="sxs-lookup"><span data-stu-id="11288-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="11288-105">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesine özniteliğin ayarladığınız `isCompliant` ya da parametre `True` veya `False` uyumluluk veya uyumsuzluk belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="11288-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="11288-106">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="11288-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="11288-107">Geçerli <xref:System.CLSCompliantAttribute> bir öğe için uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="11288-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="11288-108">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="11288-108">By default, this message is a warning.</span></span> <span data-ttu-id="11288-109">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="11288-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="11288-110">**Hata Kimliği:** BC40033</span><span class="sxs-lookup"><span data-stu-id="11288-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="11288-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="11288-111">To correct this error</span></span>  
  
- <span data-ttu-id="11288-112">CLS uyumluluğu gerektir ve denetime arabirimi kaynak kodu varsa arabirimi olarak işaretlemek `<CLSCompliant(True)>` tüm üyeleri uyumlu ise.</span><span class="sxs-lookup"><span data-stu-id="11288-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
- <span data-ttu-id="11288-113">CLS uyumluluğu gerektir ve arabirimi kaynak kod üzerinde denetim sahibi olmadığınız veya uyumlu olması uymuyorsa, farklı bir arabirim içinde bu üye tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="11288-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
- <span data-ttu-id="11288-114">Bu üye, geçerli arabirimi içinde kalmasını gerektiriyorsa, kaldırma <xref:System.CLSCompliantAttribute> kendi tanımından veya olarak işaretlemek `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="11288-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11288-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11288-115">See also</span></span>

- [<span data-ttu-id="11288-116">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="11288-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
