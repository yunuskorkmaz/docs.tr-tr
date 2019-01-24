---
title: '&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; taban sınıfı tarafından zaten uygulanmış &#39; &lt;baseclassname&gt;&#39;. Yeniden uygulanmasına &lt;türü&gt; varsayıldı'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 22a3bd4e8c09c0d070e7fa5e75571a7215c3a274
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507206"
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a><span data-ttu-id="f8f59-103">&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; taban sınıfı tarafından zaten uygulanmış &#39; &lt;baseclassname&gt;&#39;.</span><span class="sxs-lookup"><span data-stu-id="f8f59-103">&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;.</span></span> <span data-ttu-id="f8f59-104">Yeniden uygulanmasına &lt;türü&gt; varsayıldı</span><span class="sxs-lookup"><span data-stu-id="f8f59-104">Re-implementation of &lt;type&gt; assumed</span></span>
<span data-ttu-id="f8f59-105">Bir özellik, yordam veya türetilmiş bir sınıf içinde olay kullanan bir `Implements` temel sınıfta zaten uygulanmış bir arabirim üyesi belirleme yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f8f59-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="f8f59-106">Türetilmiş bir sınıf, taban sınıfı tarafından uygulanan bir arabirim üyesi yeniden uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f8f59-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="f8f59-107">Bu temel sınıf uygulamasına geçersiz kılma ile aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="f8f59-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="f8f59-108">Daha fazla bilgi için [uygular](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f8f59-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="f8f59-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="f8f59-109">By default, this message is a warning.</span></span> <span data-ttu-id="f8f59-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f8f59-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f8f59-111">**Hata Kimliği:** BC42015</span><span class="sxs-lookup"><span data-stu-id="f8f59-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f8f59-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f8f59-112">To correct this error</span></span>  
  
-   <span data-ttu-id="f8f59-113">Arabirim üyesini yeniden uygulayın yapmak istiyorsanız, herhangi bir eylemde bulunmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f8f59-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="f8f59-114">Türetilmiş sınıfınızın kodda erişen reimplemented üye kullanılmadıkça `MyBase` temel sınıf uygulamasına erişmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="f8f59-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="f8f59-115">Arabirim üyesini yeniden uygulayın düşünmüyorsanız kaldırmak `Implements` özellik, yordam veya olay bildiriminin from yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f8f59-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f59-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8f59-116">See also</span></span>
- [<span data-ttu-id="f8f59-117">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="f8f59-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
