---
title: '&#39;&lt;ElementName&gt; &#39; eski (Visual Basic uyarı)'
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 4dc2d0b8eace9bc411a344b4f2c4c79f7e09ac22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586776"
---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a><span data-ttu-id="70a97-102">&#39;&lt;ElementName&gt; &#39; eski (Visual Basic uyarı)</span><span class="sxs-lookup"><span data-stu-id="70a97-102">&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="70a97-103">Bir deyim ile işaretlenmiş bir programlama öğesi erişmeye <xref:System.ObsoleteAttribute> özniteliğini ve bir uyarı olarak işlemek için yönergesi.</span><span class="sxs-lookup"><span data-stu-id="70a97-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="70a97-104">Herhangi bir programlama öğesi artık uygulama tarafından kullanılmakta olarak işaretleyebilirsiniz <xref:System.ObsoleteAttribute> ona.</span><span class="sxs-lookup"><span data-stu-id="70a97-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="70a97-105">Bunu yaparsanız özniteliğin ayarlayabilirsiniz <xref:System.ObsoleteAttribute.IsError%2A> ya da özellik `True` veya `False`.</span><span class="sxs-lookup"><span data-stu-id="70a97-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="70a97-106">Ayarlarsanız `True`, hata olarak öğe kullanma girişimi derleyici değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="70a97-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="70a97-107">Ayarlarsanız `False`, veya bu izin için varsayılan `False`, öğe kullanma girişimi ise derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="70a97-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="70a97-108">Varsayılan olarak, bu ileti bir uyarı çünkü <xref:System.ObsoleteAttribute.IsError%2A> özelliği <xref:System.ObsoleteAttribute> olan `False`.</span><span class="sxs-lookup"><span data-stu-id="70a97-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="70a97-109">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="70a97-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="70a97-110">**Hata Kimliği:** BC40008</span><span class="sxs-lookup"><span data-stu-id="70a97-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="70a97-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="70a97-111">To correct this error</span></span>  
  
-   <span data-ttu-id="70a97-112">Kaynak kodu başvurusu öğe adı doğru yazım olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="70a97-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a97-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70a97-113">See Also</span></span>  
 [<span data-ttu-id="70a97-114">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="70a97-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
