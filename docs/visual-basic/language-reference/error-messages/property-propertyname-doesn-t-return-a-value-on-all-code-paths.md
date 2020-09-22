---
title: "'<propertyname>' özelliği tüm kod yollarında değer döndürmüyor"
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 6a80a8275a7b9c5e3cbfa410ee219e0d16ce5918
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870943"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="648ce-102">'\<propertyname>' özelliği tüm kod yollarında değer döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="648ce-102">Property '\<propertyname>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="648ce-103">' \<propertyname> ' Özelliği tüm kod yollarında bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="648ce-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="648ce-104">Sonuç kullanıldığında çalışma zamanında null başvurusu özel durumu oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="648ce-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="648ce-105">Özellik `Get` yordamının, bir değer döndürmeyen kodu üzerinden en az bir olası yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="648ce-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="648ce-106">Aşağıdaki yollarla bir özellik yordamından bir değer döndürebilirsiniz `Get` :</span><span class="sxs-lookup"><span data-stu-id="648ce-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="648ce-107">Özellik adına değeri atayın ve sonra bir `Exit Property` ifade gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="648ce-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
- <span data-ttu-id="648ce-108">Özellik adına değeri atayın ve sonra `End Get` ifadesini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="648ce-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
- <span data-ttu-id="648ce-109">Değeri [Return ifadesine](../statements/return-statement.md)ekleyin.</span><span class="sxs-lookup"><span data-stu-id="648ce-109">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="648ce-110">Denetim `Exit Property` veya ' a geçerse `End Get` ve özellik adına herhangi bir değer atamadıysanız, `Get` yordam özelliğin veri türünün varsayılan değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="648ce-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="648ce-111">Daha fazla bilgi için bkz. [Işlev deyimindeki](../statements/function-statement.md)"davranış".</span><span class="sxs-lookup"><span data-stu-id="648ce-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="648ce-112">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="648ce-112">By default, this message is a warning.</span></span> <span data-ttu-id="648ce-113">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="648ce-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="648ce-114">**Hata kimliği:** BC42107</span><span class="sxs-lookup"><span data-stu-id="648ce-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="648ce-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="648ce-115">To correct this error</span></span>  
  
- <span data-ttu-id="648ce-116">Denetim akışı mantığınızı denetleyin ve dönüşe neden olan her deyimden önce bir değer atadığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="648ce-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="648ce-117">Her zaman ifadesini kullanıyorsanız, yordamdan gelen her döndürün bir değer döndürdüğünden emin olmak daha kolaydır `Return` .</span><span class="sxs-lookup"><span data-stu-id="648ce-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="648ce-118">Bunu yaparsanız, önceki son deyimin `End Get` bir ifade olması gerekir `Return` .</span><span class="sxs-lookup"><span data-stu-id="648ce-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="648ce-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="648ce-119">See also</span></span>

- [<span data-ttu-id="648ce-120">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="648ce-120">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="648ce-121">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="648ce-121">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="648ce-122">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="648ce-122">Get Statement</span></span>](../statements/get-statement.md)
