---
title: '&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; temel sınıfı tarafından zaten uygulanmış &#39; &lt;baseclassname&gt;&#39;. Yeniden uyarlamasını &lt;türü&gt; varsayılır'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 9054c293ede9db4637f23579407f2f76db29f2ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588976"
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a><span data-ttu-id="4a7a4-103">&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; temel sınıfı tarafından zaten uygulanmış &#39; &lt;baseclassname&gt;&#39;.</span><span class="sxs-lookup"><span data-stu-id="4a7a4-103">&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;.</span></span> <span data-ttu-id="4a7a4-104">Yeniden uyarlamasını &lt;türü&gt; varsayılır</span><span class="sxs-lookup"><span data-stu-id="4a7a4-104">Re-implementation of &lt;type&gt; assumed</span></span>
<span data-ttu-id="4a7a4-105">Bir özellik, yordam veya türetilmiş bir sınıf olayda kullanan bir `Implements` yan tümcesi taban sınıf içinde zaten uygulanmış bir arabirim üyesini belirtme.</span><span class="sxs-lookup"><span data-stu-id="4a7a4-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="4a7a4-106">Türetilmiş bir sınıf kendi temel sınıfı tarafından uygulanan bir arabirim üyesini yeniden uygulamalı.</span><span class="sxs-lookup"><span data-stu-id="4a7a4-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="4a7a4-107">Bu taban sınıfı uygulama geçersiz kılma olarak aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="4a7a4-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="4a7a4-108">Daha fazla bilgi için bkz: [uygulayan](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4a7a4-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="4a7a4-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="4a7a4-109">By default, this message is a warning.</span></span> <span data-ttu-id="4a7a4-110">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="4a7a4-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="4a7a4-111">**Hata Kimliği:** BC42015</span><span class="sxs-lookup"><span data-stu-id="4a7a4-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4a7a4-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4a7a4-112">To correct this error</span></span>  
  
-   <span data-ttu-id="4a7a4-113">Arabirim üyesini yeniden uygulamalı yapmak istiyorsanız, herhangi bir eylemde bulunmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4a7a4-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="4a7a4-114">Kullanmadığınız sürece, türetilmiş bir sınıf kodda erişen reimplemented üye `MyBase` taban sınıfı uygulama erişmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="4a7a4-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="4a7a4-115">Arabirim üyesini yeniden uygulamalı düşünmüyorsanız kaldırmak `Implements` özelliği, yordam veya olay bildiriminin from yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="4a7a4-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a7a4-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a7a4-116">See Also</span></span>  
 [<span data-ttu-id="4a7a4-117">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="4a7a4-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
