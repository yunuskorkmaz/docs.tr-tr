---
title: "&#39; &lt;classname&gt;&#39; CLS uyumlu olmadığından arabirimi &#39;&lt; InterfaceName&gt;&#39; uygular, CLS uyumlu değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords: BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7bad6aa4c8fa9979824766e83aba75697d6e98d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a><span data-ttu-id="8e46c-102">&#39; &lt;classname&gt;&#39; CLS uyumlu olmadığından arabirimi &#39;&lt; InterfaceName&gt;&#39; uygular, CLS uyumlu değil</span><span class="sxs-lookup"><span data-stu-id="8e46c-102">&#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant</span></span>
<span data-ttu-id="8e46c-103">Bir sınıf veya arabirim olarak işaretlenmiş `<CLSCompliant(True)>` zaman türetilen veya olarak işaretlenmiş bir tür uygular `<CLSCompliant(False)>` veya değil olarak işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="8e46c-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="8e46c-104">Bir sınıf veya uyumlu olması için arabirimi için [dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/12a7a7h3) (CLS) tüm Devralma Hiyerarşisi olmalıdır uyumlu.</span><span class="sxs-lookup"><span data-stu-id="8e46c-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="8e46c-105">Her tür devraldığı, doğrudan veya dolaylı olarak, uyumlu olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8e46c-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="8e46c-106">Bir sınıf bir veya daha fazla arabirimlerini uygular, benzer şekilde, tüm kullanıcıların devralma hiyerarşileri uyumlu olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e46c-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="8e46c-107">Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesi için ayarladığınız özniteliğin `isCompliant` ya da parametre `True` veya `False` uyumluluğu veya uyumsuzluğu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="8e46c-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="8e46c-108">Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e46c-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="8e46c-109">Geçerli <xref:System.CLSCompliantAttribute> bir öğe olarak uyumsuz olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8e46c-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="8e46c-110">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="8e46c-110">By default, this message is a warning.</span></span> <span data-ttu-id="8e46c-111">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8e46c-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="8e46c-112">**Hata Kimliği:** BC40029</span><span class="sxs-lookup"><span data-stu-id="8e46c-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8e46c-113">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8e46c-113">To correct this error</span></span>  
  
-   <span data-ttu-id="8e46c-114">CLS uyumluluğu gerektiriyorsa, farklı bir devralma hiyerarşisi veya uygulama düzeni içinde bu tür tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="8e46c-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
-   <span data-ttu-id="8e46c-115">Bu tür, geçerli Devralma Hiyerarşisi veya uygulama düzeni içinde kalmasını gerekiyorsa kaldırma <xref:System.CLSCompliantAttribute> kendi tanımındaki veya olarak işaretlemek `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="8e46c-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e46c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e46c-116">See Also</span></span>  
 [<span data-ttu-id="8e46c-117">\<PAVE üzerinden > CLS uyumlu kod yazma</span><span class="sxs-lookup"><span data-stu-id="8e46c-117">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
