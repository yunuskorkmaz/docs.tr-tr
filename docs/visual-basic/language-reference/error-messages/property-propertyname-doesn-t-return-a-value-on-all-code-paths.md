---
title: "'<propertyname>' özelliği tüm kod yollarında değer döndürmüyor"
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: a5cb28a024274e58da1755b437d6ba4ca6712610
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661709"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="ed366-102">Özellik '\<propertyname >' bütün kod yollarında değer döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="ed366-102">Property '\<propertyname>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="ed366-103">Özellik '\<propertyname >' bütün kod yollarında değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="ed366-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="ed366-104">Sonuç kullanıldığında çalışma zamanında null başvurusu özel durumu oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="ed366-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="ed366-105">Bir özellik `Get` yordamının bir değer döndürmeyen kendi kod aracılığıyla en az bir olası yol vardır.</span><span class="sxs-lookup"><span data-stu-id="ed366-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="ed366-106">Bir özelliği bir değer döndürebilir `Get` aşağıdaki yollardan biriyle yordamda:</span><span class="sxs-lookup"><span data-stu-id="ed366-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="ed366-107">Özellik adlarının değer atamak ve ardından gerçekleştirin bir `Exit Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ed366-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
- <span data-ttu-id="ed366-108">Özellik adlarının değer atamak ve ardından gerçekleştirin `End Get` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ed366-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
- <span data-ttu-id="ed366-109">Değer bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ed366-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="ed366-110">Denetim için geçerse `Exit Property` veya `End Get` ve özellik adı için herhangi bir değer atamadınız `Get` yordamı özelliğinin veri türünün varsayılan değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed366-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="ed366-111">Daha fazla bilgi için "Davranışı" bölümüne bakın. [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ed366-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="ed366-112">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="ed366-112">By default, this message is a warning.</span></span> <span data-ttu-id="ed366-113">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ed366-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="ed366-114">**Hata Kimliği:** BC42107</span><span class="sxs-lookup"><span data-stu-id="ed366-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ed366-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ed366-115">To correct this error</span></span>  
  
- <span data-ttu-id="ed366-116">Denetim akışı mantığınızı denetleyin ve bir dönüş neden her deyiminden önce bir değer atadığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="ed366-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="ed366-117">Her zaman kullanırsanız her iade yordamdan gelen bir değer döndürür garanti daha kolaydır `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ed366-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="ed366-118">Bu, son deyim önce yaparsanız `End Get` olmalıdır bir `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ed366-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed366-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed366-119">See also</span></span>

- [<span data-ttu-id="ed366-120">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="ed366-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="ed366-121">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="ed366-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="ed366-122">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="ed366-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
