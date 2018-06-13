---
title: Özellik &#39; &lt;propertyname&gt; &#39; mevcut değil&#39;t tüm kod yolları bir değer döndürür
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 72bc7e45cadd2528f29c88bf6e80ee5f381052dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594220"
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="5e9f1-102">Özellik &#39; &lt;propertyname&gt; &#39; mevcut değil&#39;t tüm kod yolları bir değer döndürür</span><span class="sxs-lookup"><span data-stu-id="5e9f1-102">Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="5e9f1-103">Özellik '\<propertyname >' tüm kod yolları bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="5e9f1-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="5e9f1-104">Sonuç kullanıldığında çalışma zamanında bir null başvuru özel durumu oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="5e9f1-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="5e9f1-105">Bir özellik `Get` yordamının bir değer döndürmüyor kendi kod aracılığıyla en az bir olası yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="5e9f1-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="5e9f1-106">Bir özellikten değer döndürme `Get` aşağıdaki yollardan birini yordamda:</span><span class="sxs-lookup"><span data-stu-id="5e9f1-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="5e9f1-107">Özellik adı değeri atayın ve ardından gerçekleştirmek bir `Exit Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5e9f1-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="5e9f1-108">Özellik adı değeri atayın ve ardından gerçekleştirmek `End Get` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5e9f1-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="5e9f1-109">Değer içeren bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5e9f1-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="5e9f1-110">Denetim geçirir, `Exit Property` veya `End Get` ve özellik adı için herhangi bir değer atamadığınız `Get` yordamı özelliğin veri türünün varsayılan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e9f1-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="5e9f1-111">Daha fazla bilgi için bkz: "Davranışı" [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5e9f1-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="5e9f1-112">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="5e9f1-112">By default, this message is a warning.</span></span> <span data-ttu-id="5e9f1-113">Uyarıları gizleme veya uyarıları hata olarak davranma daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5e9f1-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5e9f1-114">**Hata Kimliği:** BC42107</span><span class="sxs-lookup"><span data-stu-id="5e9f1-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5e9f1-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5e9f1-115">To correct this error</span></span>  
  
-   <span data-ttu-id="5e9f1-116">Denetim akışı mantığınızı denetleyin ve satır başı neden olan her deyimi önce bir değer atadığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="5e9f1-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="5e9f1-117">Her zaman kullanıyorsanız her return yordamdan bir değer döndürür güvence altına almak daha kolay `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5e9f1-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="5e9f1-118">Bu, son deyim önce yaparsanız `End Get` olması gereken bir `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5e9f1-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e9f1-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e9f1-119">See Also</span></span>  
 [<span data-ttu-id="5e9f1-120">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="5e9f1-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="5e9f1-121">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="5e9f1-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="5e9f1-122">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="5e9f1-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
