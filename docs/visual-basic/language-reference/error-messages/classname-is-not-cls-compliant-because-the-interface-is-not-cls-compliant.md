---
title: Uyguladığı '<classname>' arabirimi CLS uyumlu olmadığından, '<interfacename>' CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
ms.openlocfilehash: 063c42249abbfb506fd15311659599b4777d397f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101321"
---
# <a name="classname-is-not-cls-compliant-because-the-interface-interfacename-it-implements-is-not-cls-compliant"></a><span data-ttu-id="3363b-102">'\<SınıfAdı >' CLS uyumlu olmadığından, arabirim '\<InterfaceName >', uygular, CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="3363b-102">'\<classname>' is not CLS-compliant because the interface '\<interfacename>' it implements is not CLS-compliant</span></span>
<span data-ttu-id="3363b-103">Bir sınıf veya arabirim olarak işaretlenmiş `<CLSCompliant(True)>` ne zaman türetilen veya olarak işaretlenmiş bir türün uyguladığı `<CLSCompliant(False)>` veya hiçbir işaret konulmadıysa.</span><span class="sxs-lookup"><span data-stu-id="3363b-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="3363b-104">Bir sınıfı veya arabirimi ile uyumlu olacak şekilde [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) tüm Devralma Hiyerarşisi olmalıdır uyumlu.</span><span class="sxs-lookup"><span data-stu-id="3363b-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="3363b-105">Her türün devraldığı, doğrudan veya dolaylı olarak, uyumlu olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3363b-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="3363b-106">Bir sınıf, bir veya daha fazla arabirim uygularsa, benzer şekilde, tüm bunların devralma hiyerarşilerini uyumlu olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="3363b-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="3363b-107">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesine özniteliğin ayarladığınız `isCompliant` ya da parametre `True` veya `False` uyumluluk veya uyumsuzluk belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="3363b-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="3363b-108">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3363b-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="3363b-109">Geçerli <xref:System.CLSCompliantAttribute> bir öğe için uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3363b-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="3363b-110">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="3363b-110">By default, this message is a warning.</span></span> <span data-ttu-id="3363b-111">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3363b-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="3363b-112">**Hata Kimliği:** BC40029</span><span class="sxs-lookup"><span data-stu-id="3363b-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3363b-113">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3363b-113">To correct this error</span></span>  
  
-   <span data-ttu-id="3363b-114">CLS uyumluluğu gerektiriyorsa, bu tür içinde farklı bir devralma hiyerarşisi veya uygulama düzeni tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3363b-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
-   <span data-ttu-id="3363b-115">Bu tür, geçerli bir devralma hiyerarşisi veya uygulama düzeni içinde kalmasını gerektiriyorsa, kaldırma <xref:System.CLSCompliantAttribute> kendi tanımından veya olarak işaretlemek `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="3363b-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
