---
description: "Şu konuda daha fazla bilgi edinin: BC42107: ' <propertyname> ' özelliği tüm kod yollarında değer döndürmüyor"
title: "'<propertyname>' özelliği tüm kod yollarında değer döndürmüyor"
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 9aa0d6fea1feeaf7503f5f8831fbd3de910a4822
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774895"
---
# <a name="bc42107-property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="b1a20-103">BC42107: ' \<propertyname> ' özelliği tüm kod yollarında bir değer döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="b1a20-103">BC42107: Property '\<propertyname>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="b1a20-104">' \<propertyname> ' Özelliği tüm kod yollarında bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="b1a20-104">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="b1a20-105">Sonuç kullanıldığında çalışma zamanında null başvurusu özel durumu oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="b1a20-105">A null reference exception could occur at run time when the result is used.</span></span>

<span data-ttu-id="b1a20-106">Özellik `Get` yordamının, bir değer döndürmeyen kodu üzerinden en az bir olası yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="b1a20-106">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>

 <span data-ttu-id="b1a20-107">Aşağıdaki yollarla bir özellik yordamından bir değer döndürebilirsiniz `Get` :</span><span class="sxs-lookup"><span data-stu-id="b1a20-107">You can return a value from a property `Get` procedure in any of the following ways:</span></span>

- <span data-ttu-id="b1a20-108">Özellik adına değeri atayın ve sonra bir `Exit Property` ifade gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="b1a20-108">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>

- <span data-ttu-id="b1a20-109">Özellik adına değeri atayın ve sonra `End Get` ifadesini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="b1a20-109">Assign the value to the property name and then perform the `End Get` statement.</span></span>

- <span data-ttu-id="b1a20-110">Değeri [Return ifadesine](../statements/return-statement.md)ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b1a20-110">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>

<span data-ttu-id="b1a20-111">Denetim `Exit Property` veya ' a geçerse `End Get` ve özellik adına herhangi bir değer atamadıysanız, `Get` yordam özelliğin veri türünün varsayılan değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1a20-111">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="b1a20-112">Daha fazla bilgi için bkz. [Işlev deyimindeki](../statements/function-statement.md)"davranış".</span><span class="sxs-lookup"><span data-stu-id="b1a20-112">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>

<span data-ttu-id="b1a20-113">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="b1a20-113">By default, this message is a warning.</span></span> <span data-ttu-id="b1a20-114">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b1a20-114">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="b1a20-115">**Hata kimliği:** BC42107</span><span class="sxs-lookup"><span data-stu-id="b1a20-115">**Error ID:** BC42107</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b1a20-116">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b1a20-116">To correct this error</span></span>

- <span data-ttu-id="b1a20-117">Denetim akışı mantığınızı denetleyin ve dönüşe neden olan her deyimden önce bir değer atadığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b1a20-117">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>

  <span data-ttu-id="b1a20-118">Her zaman ifadesini kullanıyorsanız, yordamdan gelen her döndürün bir değer döndürdüğünden emin olmak daha kolay olur `Return` .</span><span class="sxs-lookup"><span data-stu-id="b1a20-118">It's easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="b1a20-119">Bunu yaparsanız, önceki son deyimin `End Get` bir ifade olması gerekir `Return` .</span><span class="sxs-lookup"><span data-stu-id="b1a20-119">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1a20-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1a20-120">See also</span></span>

- [<span data-ttu-id="b1a20-121">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="b1a20-121">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="b1a20-122">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="b1a20-122">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="b1a20-123">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="b1a20-123">Get Statement</span></span>](../statements/get-statement.md)
