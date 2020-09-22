---
title: "'<elementname>' eski (Visual Basic Uyarısı)"
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: faad25c08a012674e9d5ba569025bead8ffdec90
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874439"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="352d6-102">'\<elementname>' eski (Visual Basic Uyarısı)</span><span class="sxs-lookup"><span data-stu-id="352d6-102">'\<elementname>' is obsolete (Visual Basic Warning)</span></span>

<span data-ttu-id="352d6-103">Bir ifade, özniteliğiyle işaretlenmiş bir programlama öğesine <xref:System.ObsoleteAttribute> ve bir uyarı olarak kabul edilecek yönergeye erişmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="352d6-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="352d6-104">Herhangi bir programlama öğesini, bu uygulamaya uygulama tarafından artık kullanımda olmayacak şekilde işaretleyebilirsiniz <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="352d6-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="352d6-105">Bunu yaparsanız özniteliğin <xref:System.ObsoleteAttribute.IsError%2A> özelliğini ya da olarak ayarlayabilirsiniz `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="352d6-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="352d6-106">Öğesini olarak ayarlarsanız `True` , derleyici bir hata olarak öğeyi kullanma denemesine davranır.</span><span class="sxs-lookup"><span data-stu-id="352d6-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="352d6-107">Bunu olarak ayarlarsanız `False` veya varsayılan olarak izin verirseniz `False` , öğesini kullanma girişimi varsa derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="352d6-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="352d6-108">Varsayılan olarak, bu ileti bir uyarıdır, çünkü <xref:System.ObsoleteAttribute.IsError%2A> öğesinin özelliği <xref:System.ObsoleteAttribute> olur `False` .</span><span class="sxs-lookup"><span data-stu-id="352d6-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="352d6-109">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="352d6-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="352d6-110">**Hata kimliği:** BC40008</span><span class="sxs-lookup"><span data-stu-id="352d6-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="352d6-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="352d6-111">To correct this error</span></span>  
  
- <span data-ttu-id="352d6-112">Kaynak kodu başvurusunun öğe adının doğru yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="352d6-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="352d6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="352d6-113">See also</span></span>

- [<span data-ttu-id="352d6-114">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="352d6-114">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
