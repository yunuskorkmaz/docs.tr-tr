---
title: "&#39; &lt;elementname&gt;&#39; artık kullanılmayan (Visual Basic uyarı)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd6580da794255a3324021a284816ef9700beee7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a><span data-ttu-id="c6086-102">&#39; &lt;elementname&gt;&#39; artık kullanılmayan (Visual Basic uyarı)</span><span class="sxs-lookup"><span data-stu-id="c6086-102">&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="c6086-103">Bir deyim ile işaretlenmiş bir programlama öğesi erişmeye <xref:System.ObsoleteAttribute> özniteliğini ve bir uyarı olarak işlemek için yönergesi.</span><span class="sxs-lookup"><span data-stu-id="c6086-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="c6086-104">Herhangi bir programlama öğesi artık uygulama tarafından kullanılmakta olarak işaretleyebilirsiniz <xref:System.ObsoleteAttribute> ona.</span><span class="sxs-lookup"><span data-stu-id="c6086-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="c6086-105">Bunu yaparsanız özniteliğin ayarlayabilirsiniz <xref:System.ObsoleteAttribute.IsError%2A> ya da özellik `True` veya `False`.</span><span class="sxs-lookup"><span data-stu-id="c6086-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="c6086-106">Ayarlarsanız `True`, hata olarak öğe kullanma girişimi derleyici değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c6086-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="c6086-107">Ayarlarsanız `False`, veya bu izin için varsayılan `False`, öğe kullanma girişimi ise derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="c6086-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="c6086-108">Varsayılan olarak, bu ileti bir uyarı çünkü <xref:System.ObsoleteAttribute.IsError%2A> özelliği <xref:System.ObsoleteAttribute> olan `False`.</span><span class="sxs-lookup"><span data-stu-id="c6086-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="c6086-109">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c6086-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c6086-110">**Hata Kimliği:** BC40008</span><span class="sxs-lookup"><span data-stu-id="c6086-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c6086-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c6086-111">To correct this error</span></span>  
  
-   <span data-ttu-id="c6086-112">Kaynak kodu başvurusu öğe adı doğru yazım olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="c6086-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6086-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6086-113">See Also</span></span>  
 [<span data-ttu-id="c6086-114">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="c6086-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
