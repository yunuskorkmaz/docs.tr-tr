---
title: "Özellik &#39; &lt;propertyname&gt;&#39; belirlemeden #39; tüm kod yolları bir değer döndürmesi t"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c9ef5b2ac62412f5684cbc78ab6bebf6bc7b6752
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="936c9-102">Özellik &#39; &lt;propertyname&gt;&#39; belirlemeden #39; tüm kod yolları bir değer döndürmesi t</span><span class="sxs-lookup"><span data-stu-id="936c9-102">Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="936c9-103">Özellik '\<propertyname >' tüm kod yolları bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="936c9-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="936c9-104">Sonuç kullanıldığında çalışma zamanında bir null başvuru özel durumu oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="936c9-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="936c9-105">Bir özellik `Get` yordamının bir değer döndürmüyor kendi kod aracılığıyla en az bir olası yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="936c9-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="936c9-106">Bir özellikten değer döndürme `Get` aşağıdaki yollardan birini yordamda:</span><span class="sxs-lookup"><span data-stu-id="936c9-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="936c9-107">Özellik adı değeri atayın ve ardından gerçekleştirmek bir `Exit Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="936c9-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="936c9-108">Özellik adı değeri atayın ve ardından gerçekleştirmek `End Get` deyimi.</span><span class="sxs-lookup"><span data-stu-id="936c9-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="936c9-109">Değer içeren bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="936c9-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="936c9-110">Denetim geçirir, `Exit Property` veya `End Get` ve özellik adı için herhangi bir değer atamadığınız `Get` yordamı özelliğin veri türünün varsayılan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="936c9-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="936c9-111">Daha fazla bilgi için bkz: "Davranışı" [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="936c9-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="936c9-112">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="936c9-112">By default, this message is a warning.</span></span> <span data-ttu-id="936c9-113">Uyarıları gizleme veya uyarıları hata olarak davranma daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="936c9-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="936c9-114">**Hata Kimliği:** BC42107</span><span class="sxs-lookup"><span data-stu-id="936c9-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="936c9-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="936c9-115">To correct this error</span></span>  
  
-   <span data-ttu-id="936c9-116">Denetim akışı mantığınızı denetleyin ve satır başı neden olan her deyimi önce bir değer atadığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="936c9-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="936c9-117">Her zaman kullanıyorsanız her return yordamdan bir değer döndürür güvence altına almak daha kolay `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="936c9-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="936c9-118">Bu, son deyim önce yaparsanız `End Get` olması gereken bir `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="936c9-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="936c9-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="936c9-119">See Also</span></span>  
 [<span data-ttu-id="936c9-120">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="936c9-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="936c9-121">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="936c9-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="936c9-122">Get deyimi</span><span class="sxs-lookup"><span data-stu-id="936c9-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
