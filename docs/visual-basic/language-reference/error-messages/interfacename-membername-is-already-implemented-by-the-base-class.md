---
title: "&#39; &lt;InterfaceName&gt;.&lt; membername&gt;&#39; zaten temel sınıfı &#39; tarafından uygulanan&lt; baseclassname&gt;&#39;. Yeniden uyarlamasını &lt;türü&gt; varsayılır"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords: BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69884ed567e0046da5cf5c51b3e83e57e890d49f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a><span data-ttu-id="fde2a-103">&#39; &lt;InterfaceName&gt;.&lt; membername&gt;&#39; zaten temel sınıfı &#39; tarafından uygulanan&lt; baseclassname&gt;&#39;.</span><span class="sxs-lookup"><span data-stu-id="fde2a-103">&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;.</span></span> <span data-ttu-id="fde2a-104">Yeniden uyarlamasını &lt;türü&gt; varsayılır</span><span class="sxs-lookup"><span data-stu-id="fde2a-104">Re-implementation of &lt;type&gt; assumed</span></span>
<span data-ttu-id="fde2a-105">Bir özellik, yordam veya türetilmiş bir sınıf olayda kullanan bir `Implements` yan tümcesi taban sınıf içinde zaten uygulanmış bir arabirim üyesini belirtme.</span><span class="sxs-lookup"><span data-stu-id="fde2a-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="fde2a-106">Türetilmiş bir sınıf kendi temel sınıfı tarafından uygulanan bir arabirim üyesini yeniden uygulamalı.</span><span class="sxs-lookup"><span data-stu-id="fde2a-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="fde2a-107">Bu taban sınıfı uygulama geçersiz kılma olarak aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="fde2a-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="fde2a-108">Daha fazla bilgi için bkz: [uygulayan](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="fde2a-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="fde2a-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="fde2a-109">By default, this message is a warning.</span></span> <span data-ttu-id="fde2a-110">Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fde2a-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="fde2a-111">**Hata Kimliği:** BC42015</span><span class="sxs-lookup"><span data-stu-id="fde2a-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fde2a-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fde2a-112">To correct this error</span></span>  
  
-   <span data-ttu-id="fde2a-113">Arabirim üyesini yeniden uygulamalı yapmak istiyorsanız, herhangi bir eylemde bulunmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fde2a-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="fde2a-114">Kullanmadığınız sürece, türetilmiş bir sınıf kodda erişen reimplemented üye `MyBase` taban sınıfı uygulama erişmek için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="fde2a-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="fde2a-115">Arabirim üyesini yeniden uygulamalı düşünmüyorsanız kaldırmak `Implements` özelliği, yordam veya olay bildiriminin from yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="fde2a-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fde2a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fde2a-116">See Also</span></span>  
 [<span data-ttu-id="fde2a-117">Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fde2a-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
