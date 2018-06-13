---
title: 'Bu ilk deyimi &#39;Sub New&#39; için açık bir çağrı olmalıdır &#39;MyBase.New&#39; veya &#39;MyClass.New&#39; çünkü &#39; &lt;constructorname&gt; &#39; temel sınıf &#39; &lt;baseclassname&gt; &#39; , &#39; &lt;derivedclassname&gt; &#39; kullanımdan kaldırılmış olarak işaretlenmiş: &#39; &lt;errormessage&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: dbce2a9edcc38ff137cb7ec0c97e5c259c0a0979
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589899"
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="6fe97-102">Bu ilk deyimi &#39;Sub New&#39; için açık bir çağrı olmalıdır &#39;MyBase.New&#39; veya &#39;MyClass.New&#39; çünkü &#39; &lt;constructorname&gt; &#39; temel sınıf &#39; &lt;baseclassname&gt; &#39; , &#39; &lt;derivedclassname&gt; &#39; kullanımdan kaldırılmış olarak işaretlenmiş: &#39; &lt;errormessage&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="6fe97-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="6fe97-103">Bir sınıf oluşturucu açıkça bir temel sınıf oluşturucu çağırmaz ve örtük temel sınıf oluşturucu ile işaretlenmiş <xref:System.ObsoleteAttribute> özniteliği ve yönergesi hata olarak ele alın.</span><span class="sxs-lookup"><span data-stu-id="6fe97-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="6fe97-104">Bir türetilmiş sınıf oluşturucu bir temel sınıf oluşturucu çağırmaz başlatıldığında, bir taban sınıf parametresiz oluşturucuya örtük bir çağrı oluşturmak Visual Basic dener.</span><span class="sxs-lookup"><span data-stu-id="6fe97-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="6fe97-105">Bağımsız değişkenler çağrılabilir temel sınıf erişilebilir bir oluşturucu yok ise, Visual Basic örtük bir çağrı oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="6fe97-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="6fe97-106">Bu durumda, gerekli Oluşturucusu ile işaretlenmiş <xref:System.ObsoleteAttribute> Visual Basic çağıramaz şekilde özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6fe97-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>  
  
 <span data-ttu-id="6fe97-107">Herhangi bir programlama öğesi artık uygulama tarafından kullanılmakta olarak işaretleyebilirsiniz <xref:System.ObsoleteAttribute> ona.</span><span class="sxs-lookup"><span data-stu-id="6fe97-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="6fe97-108">Bunu yaparsanız özniteliğin ayarlayabilirsiniz <xref:System.ObsoleteAttribute.IsError%2A> ya da özellik `True` veya `False`.</span><span class="sxs-lookup"><span data-stu-id="6fe97-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="6fe97-109">Ayarlarsanız `True`, hata olarak öğe kullanma girişimi derleyici değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="6fe97-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="6fe97-110">Ayarlarsanız `False`, veya bu izin için varsayılan `False`, öğe kullanma girişimi ise derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="6fe97-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="6fe97-111">**Hata Kimliği:** BC30920</span><span class="sxs-lookup"><span data-stu-id="6fe97-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6fe97-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6fe97-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="6fe97-113">Tırnak işaretli hata iletisini inceleyin ve uygun eylemi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="6fe97-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="6fe97-114">Bir çağrı ekleyin `MyBase.New()` veya `MyClass.New()` ilk ifadesi olarak `Sub New` türetilen sınıfta.</span><span class="sxs-lookup"><span data-stu-id="6fe97-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe97-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6fe97-115">See Also</span></span>  
 [<span data-ttu-id="6fe97-116">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="6fe97-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
 
