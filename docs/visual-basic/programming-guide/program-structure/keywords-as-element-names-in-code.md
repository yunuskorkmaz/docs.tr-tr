---
title: "Kodda Öğe Adları Olarak Anahtar Sözcükler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f410a0eaac0dcc034d406a89ed1d01a8f228a583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="de381-102">Kodda Öğe Adları Olarak Anahtar Sözcükler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de381-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="de381-103">Herhangi bir program öğesi — bir değişkeni, sınıf veya üye gibi — sınırlı anahtar sözcüğü ile aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="de381-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="de381-104">Örneğin, adında bir değişken oluşturabilirsiniz `Loop`.</span><span class="sxs-lookup"><span data-stu-id="de381-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="de381-105">Ancak, bunu sürümünüz için başvurmak için — kısıtlanmış aynı ada sahip `Loop` anahtar sözcüğü — tam nitelenmiş dizesiyle önünde veya köşeli parantez içine almanız (`[ ]`), aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="de381-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 <span data-ttu-id="de381-106">Bunlardan birini yapmak sonra Visual Basic varsayar iç kullanımını `Loop` anahtar sözcüğü ve aşağıdaki örnekteki gibi bir hata üretir:</span><span class="sxs-lookup"><span data-stu-id="de381-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="de381-107">Formlar ve denetimler için söz konusu olduğunda ve ne zaman köşeli kullanabileceğiniz bir değişken bildirme veya aynı ada sahip bir yordamı kısıtlanmış bir anahtar sözcük olarak tanımlama.</span><span class="sxs-lookup"><span data-stu-id="de381-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="de381-108">Adları nitelemeniz veya köşeli içerir ve bu nedenle kodunuza hatalara ve okumak daha zor hale unuttunuz kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="de381-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="de381-109">Bu nedenle, sınırlı anahtar sözcükleri program öğe adları olarak kullanmamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="de381-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="de381-110">Visual Basic gelecek bir sürümünde yeni bir anahtar sözcük varolan form veya denetim adı ile çakışan tanımlıyorsa, ancak daha sonra bu teknik kodunuzu güncelleştirilirken yeni sürümle çalışmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de381-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de381-111">Programınızı diğer başvurulan derlemeler tarafından sağlanan öğe adları de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="de381-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="de381-112">Bu adları sınırlı anahtar sözcükleriyle çakışma varsa, bunları köşeli ayraç yerleştirme tanımlanan öğelerinizi yorumlamak Visual Basic neden olur.</span><span class="sxs-lookup"><span data-stu-id="de381-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de381-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de381-113">See Also</span></span>  
 [<span data-ttu-id="de381-114">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="de381-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="de381-115">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="de381-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="de381-116">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="de381-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
