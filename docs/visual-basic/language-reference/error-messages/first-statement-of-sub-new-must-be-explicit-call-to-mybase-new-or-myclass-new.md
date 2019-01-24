---
title: 'Bu ilk deyimi &#39;Sub New&#39; açık çağrı olmalıdır &#39;MyBase.New&#39; veya &#39;MyClass.New&#39; çünkü &#39; &lt;constructorname&gt; &#39; temel sınıfta &#39; &lt;baseclassname&gt; &#39; , &#39; &lt;derivedclassname&gt; &#39; artık kullanılmıyor olarak işaretlendiğinden: &#39; &lt;errormessage&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 9d07a68fd8d9790178427c512375323f23f46772
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566789"
---
# <a name="first-statement-of-this-39sub-new39-must-be-an-explicit-call-to-39mybasenew39-or-39myclassnew39-because-the-39ltconstructornamegt39-in-the-base-class-39ltbaseclassnamegt39-of-39ltderivedclassnamegt39-is-marked-obsolete-39lterrormessagegt39"></a><span data-ttu-id="96d8b-102">Bu ilk deyimi &#39;Sub New&#39; açık çağrı olmalıdır &#39;MyBase.New&#39; veya &#39;MyClass.New&#39; çünkü &#39; &lt;constructorname&gt; &#39; temel sınıfta &#39; &lt;baseclassname&gt; &#39; , &#39; &lt;derivedclassname&gt; &#39; artık kullanılmıyor olarak işaretlendiğinden: &#39; &lt;errormessage&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="96d8b-102">First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;</span></span>
<span data-ttu-id="96d8b-103">Bir sınıf oluşturucusu bir temel sınıf oluşturucu açıkça çağırmaz ve örtük temel sınıf oluşturucusu ile işaretlenmiş <xref:System.ObsoleteAttribute> özniteliği ve hata olarak değerlendirilecek yönergesi.</span><span class="sxs-lookup"><span data-stu-id="96d8b-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="96d8b-104">Bir türetilen sınıf oluşturucusu bir temel sınıf oluşturucusunu çağırma değil, Visual Basic bir parametresiz bir temel sınıf oluşturucusu örtük çağrıyla oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="96d8b-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="96d8b-105">Temel sınıfında bağımsız değişken çağrılabilecek erişilebilir hiçbir oluşturucu ise, Visual Basic örtük çağrıyla oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="96d8b-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="96d8b-106">Bu durumda, gerekli Oluşturucusu ile işaretlenmiş <xref:System.ObsoleteAttribute> çağıramaz Visual Basic için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="96d8b-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>  
  
 <span data-ttu-id="96d8b-107">Herhangi bir programlama öğesi artık uygulayarak kullanımda olarak işaretleyebilirsiniz <xref:System.ObsoleteAttribute> ona.</span><span class="sxs-lookup"><span data-stu-id="96d8b-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="96d8b-108">Bunu yaparsanız özniteliğin ayarlayabilirsiniz <xref:System.ObsoleteAttribute.IsError%2A> ya da özellik `True` veya `False`.</span><span class="sxs-lookup"><span data-stu-id="96d8b-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="96d8b-109">Ayarlarsanız `True`, derleyici bir hata öğe kullanma girişimi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="96d8b-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="96d8b-110">Ayarlarsanız `False`, veya bu izin varsayılan `False`, öğe kullanma girişimi varsa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="96d8b-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="96d8b-111">**Hata Kimliği:** BC30920</span><span class="sxs-lookup"><span data-stu-id="96d8b-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="96d8b-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="96d8b-112">To correct this error</span></span>  
  
1.  <span data-ttu-id="96d8b-113">Tırnak işaretli hata iletisini inceleyin ve uygun eylemi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="96d8b-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2.  <span data-ttu-id="96d8b-114">Bir çağrı ekleyin `MyBase.New()` veya `MyClass.New()` ilk deyimi olarak `Sub New` türetilen sınıfta.</span><span class="sxs-lookup"><span data-stu-id="96d8b-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96d8b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96d8b-115">See also</span></span>
- [<span data-ttu-id="96d8b-116">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="96d8b-116">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

