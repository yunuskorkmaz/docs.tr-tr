---
title: "'<constructorname>' öğesinin '<baseclassname>' temel sınıfındaki '<derivedclassname>' kullanılmıyor biçiminde işaretlendiğinden, bu 'Sub New' yönteminin ilk deyimi 'MyBase.New' veya 'MyClass.New' için açık çağrı olmalıdır: '<errormessage>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 4918ac2e11dfaf682b1c00275f30c171bf241fe3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874119"
---
# <a name="first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a><span data-ttu-id="e9bd3-102">'\<constructorname>' öğesinin '\<baseclassname>' temel sınıfındaki '\<derivedclassname>' kullanılmıyor biçiminde işaretlendiğinden, bu 'Sub New' yönteminin ilk deyimi 'MyBase.New' veya 'MyClass.New' için açık çağrı olmalıdır: '\<errormessage>'</span><span class="sxs-lookup"><span data-stu-id="e9bd3-102">First statement of this 'Sub New' must be an explicit call to 'MyBase.New' or 'MyClass.New' because the '\<constructorname>' in the base class '\<baseclassname>' of '\<derivedclassname>' is marked obsolete: '\<errormessage>'</span></span>

<span data-ttu-id="e9bd3-103">Bir sınıf Oluşturucusu bir temel sınıf oluşturucusunu açıkça çağırmaz ve örtük temel sınıf oluşturucusu <xref:System.ObsoleteAttribute> özniteliği ve bir hata olarak değerlendirmek için olan yönergeyle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="e9bd3-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>  
  
 <span data-ttu-id="e9bd3-104">Türetilmiş bir sınıf Oluşturucusu bir temel sınıf oluşturucusu çağırlamadığında, Visual Basic parametresiz temel sınıf oluşturucusuna örtük bir çağrı oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="e9bd3-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="e9bd3-105">Temel sınıfta bağımsız değişken olmadan çağrılabilecek erişilebilir bir Oluşturucu yoksa Visual Basic örtük bir çağrı üretemiyor.</span><span class="sxs-lookup"><span data-stu-id="e9bd3-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="e9bd3-106">Bu durumda, gerekli Oluşturucu <xref:System.ObsoleteAttribute> özniteliğiyle işaretlenir, bu nedenle Visual Basic çağrılamıyor.</span><span class="sxs-lookup"><span data-stu-id="e9bd3-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>  
  
 <span data-ttu-id="e9bd3-107">Herhangi bir programlama öğesini, bu uygulamaya uygulama tarafından artık kullanımda olmayacak şekilde işaretleyebilirsiniz <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="e9bd3-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="e9bd3-108">Bunu yaparsanız özniteliğin <xref:System.ObsoleteAttribute.IsError%2A> özelliğini ya da olarak ayarlayabilirsiniz `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="e9bd3-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="e9bd3-109">Öğesini olarak ayarlarsanız `True` , derleyici bir hata olarak öğeyi kullanma denemesine davranır.</span><span class="sxs-lookup"><span data-stu-id="e9bd3-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="e9bd3-110">Bunu olarak ayarlarsanız `False` veya varsayılan olarak izin verirseniz `False` , öğesini kullanma girişimi varsa derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="e9bd3-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="e9bd3-111">**Hata kimliği:** BC30920</span><span class="sxs-lookup"><span data-stu-id="e9bd3-111">**Error ID:** BC30920</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e9bd3-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e9bd3-112">To correct this error</span></span>  
  
1. <span data-ttu-id="e9bd3-113">Alıntı yapılan hata iletisini inceleyin ve uygun eylemi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="e9bd3-113">Examine the quoted error message and take appropriate action.</span></span>  
  
2. <span data-ttu-id="e9bd3-114">`MyBase.New()` `MyClass.New()` Türetilmiş sınıftaki öğesinin ilk ifadesine bir çağrı ekleyin `Sub New` .</span><span class="sxs-lookup"><span data-stu-id="e9bd3-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9bd3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9bd3-115">See also</span></span>

- [<span data-ttu-id="e9bd3-116">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="e9bd3-116">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
