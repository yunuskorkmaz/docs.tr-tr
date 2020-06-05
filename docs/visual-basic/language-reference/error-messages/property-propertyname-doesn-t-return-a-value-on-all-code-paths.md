---
title: "'<propertyname>' özelliği tüm kod yollarında değer döndürmüyor"
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 21a1c4dbab6e26cd1cb848e270bbda9a544c2a67
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400428"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="95a44-102">'\<propertyname>' özelliği tüm kod yollarında değer döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="95a44-102">Property '\<propertyname>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="95a44-103">' \<propertyname> ' Özelliği tüm kod yollarında bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="95a44-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="95a44-104">Sonuç kullanıldığında çalışma zamanında null başvurusu özel durumu oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="95a44-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="95a44-105">Özellik `Get` yordamının, bir değer döndürmeyen kodu üzerinden en az bir olası yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="95a44-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="95a44-106">Aşağıdaki yollarla bir özellik yordamından bir değer döndürebilirsiniz `Get` :</span><span class="sxs-lookup"><span data-stu-id="95a44-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="95a44-107">Özellik adına değeri atayın ve sonra bir `Exit Property` ifade gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="95a44-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
- <span data-ttu-id="95a44-108">Özellik adına değeri atayın ve sonra `End Get` ifadesini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="95a44-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
- <span data-ttu-id="95a44-109">Değeri [Return ifadesine](../statements/return-statement.md)ekleyin.</span><span class="sxs-lookup"><span data-stu-id="95a44-109">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="95a44-110">Denetim `Exit Property` veya ' a geçerse `End Get` ve özellik adına herhangi bir değer atamadıysanız, `Get` yordam özelliğin veri türünün varsayılan değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="95a44-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="95a44-111">Daha fazla bilgi için bkz. [Işlev deyimindeki](../statements/function-statement.md)"davranış".</span><span class="sxs-lookup"><span data-stu-id="95a44-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="95a44-112">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="95a44-112">By default, this message is a warning.</span></span> <span data-ttu-id="95a44-113">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="95a44-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="95a44-114">**Hata kimliği:** BC42107</span><span class="sxs-lookup"><span data-stu-id="95a44-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="95a44-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="95a44-115">To correct this error</span></span>  
  
- <span data-ttu-id="95a44-116">Denetim akışı mantığınızı denetleyin ve dönüşe neden olan her deyimden önce bir değer atadığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="95a44-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="95a44-117">Her zaman ifadesini kullanıyorsanız, yordamdan gelen her döndürün bir değer döndürdüğünden emin olmak daha kolaydır `Return` .</span><span class="sxs-lookup"><span data-stu-id="95a44-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="95a44-118">Bunu yaparsanız, önceki son deyimin `End Get` bir ifade olması gerekir `Return` .</span><span class="sxs-lookup"><span data-stu-id="95a44-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a44-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95a44-119">See also</span></span>

- [<span data-ttu-id="95a44-120">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="95a44-120">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="95a44-121">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="95a44-121">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="95a44-122">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="95a44-122">Get Statement</span></span>](../statements/get-statement.md)
