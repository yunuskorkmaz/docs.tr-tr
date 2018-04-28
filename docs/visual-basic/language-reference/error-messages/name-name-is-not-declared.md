---
title: Ad &#39; &lt;adı&gt; &#39; bildirilmemiş olan
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26245952a2dc5341dedba6c497c47773b882b49b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="name-39ltnamegt39-is-not-declared"></a><span data-ttu-id="bab9d-102">Ad &#39; &lt;adı&gt; &#39; bildirilmemiş olan</span><span class="sxs-lookup"><span data-stu-id="bab9d-102">Name &#39;&lt;name&gt;&#39; is not declared</span></span>
<span data-ttu-id="bab9d-103">Bir deyim programlama bir öğesiyle ancak derleyici tam ada sahip bir öğe bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="bab9d-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="bab9d-104">**Hata Kimliği:** BC30451</span><span class="sxs-lookup"><span data-stu-id="bab9d-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bab9d-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bab9d-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="bab9d-106">Başvuran deyiminde adının yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bab9d-106">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="bab9d-107">Visual Basic büyük/küçük harfe duyarlıdır, ancak başka bir değişim yazım tamamen farklı bir ad kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="bab9d-107">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="bab9d-108">Unutmayın alt çizgi (`_`) adının bir parçası ve bu nedenle yazımı parçası.</span><span class="sxs-lookup"><span data-stu-id="bab9d-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2.  <span data-ttu-id="bab9d-109">Üye erişimi işleci olup olmadığını denetleyin (`.`) bir nesne ve onun üyesi arasında.</span><span class="sxs-lookup"><span data-stu-id="bab9d-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="bab9d-110">Örneğin, bir <xref:System.Windows.Forms.TextBox> adlı Denetim `TextBox1`erişmek için kendi <xref:System.Windows.Forms.TextBoxBase.Text%2A> yazın özelliği `TextBox1.Text`.</span><span class="sxs-lookup"><span data-stu-id="bab9d-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="bab9d-111">Bunun yerine yazarsanız, `TextBox1Text`, farklı bir ad oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="bab9d-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3.  <span data-ttu-id="bab9d-112">Yazım denetimi doğru olduğundan ve hiçbir nesne üye erişimi sözdizimini doğru ise, öğenin bildirilmiş doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="bab9d-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="bab9d-113">Daha fazla bilgi için bkz: [bildirilen öğeler](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="bab9d-113">For more information, see [Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4.  <span data-ttu-id="bab9d-114">Programlama öğesi bildirilmiş, kapsam içinde olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bab9d-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="bab9d-115">Başvuran deyimi programlama öğesi bildirme bölgesinin dışındaki ise, öğe adı nitelemek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="bab9d-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="bab9d-116">Daha fazla bilgi için bkz: [Visual Basic'de kapsam](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="bab9d-116">For more information, see [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab9d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bab9d-117">See Also</span></span>  
 [<span data-ttu-id="bab9d-118">Bildirimler ve Sabitlere İlişkin Özet</span><span class="sxs-lookup"><span data-stu-id="bab9d-118">Declarations and Constants Summary</span></span>](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [<span data-ttu-id="bab9d-119">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="bab9d-119">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="bab9d-120">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="bab9d-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="bab9d-121">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="bab9d-121">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
