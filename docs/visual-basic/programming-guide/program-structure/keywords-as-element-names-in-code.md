---
title: Kodda Öğe Adları Olarak Anahtar Sözcükler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: c247ada67f6554362f287cf252dd49856c4995da
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841153"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="74c01-102">Kodda Öğe Adları Olarak Anahtar Sözcükler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74c01-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="74c01-103">Herhangi bir program öğesi — bir değişkeni, sınıf veya üye gibi — kısıtlı bir anahtar sözcüğü ile aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="74c01-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="74c01-104">Örneğin, adında bir değişken oluşturabilirsiniz `Loop`.</span><span class="sxs-lookup"><span data-stu-id="74c01-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="74c01-105">Ancak, sürümü için başvuruda bulunmak için — kısıtlı aynı ada sahip `Loop` anahtar sözcüğü — tam nitelenmiş dizesiyle önünde veya köşeli parantez içine (`[ ]`), aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="74c01-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="74c01-106">Bunlardan birini yapmak sonra Visual Basic varsayar iç kullanımı `Loop` anahtar sözcüğü ve aşağıdaki örnekte olduğu gibi bir hata oluşturur:</span><span class="sxs-lookup"><span data-stu-id="74c01-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="74c01-107">Formlar ve denetimler için söz konusu olduğunda ve ne zaman köşeli ayraç kullanabileceğiniz bir değişken bildirme veya kısıtlanmış bir anahtar aynı ada sahip bir yordam tanımlama.</span><span class="sxs-lookup"><span data-stu-id="74c01-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="74c01-108">Adları uygun veya köşeli ayraçlar dahil olan ve bu nedenle kodunuza hatalara ve okumak daha zor hale unutmak çok kolaydır olabilir.</span><span class="sxs-lookup"><span data-stu-id="74c01-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="74c01-109">Bu nedenle, sınırlı anahtar sözcükleri program öğelerinin adlarını kullanmamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="74c01-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="74c01-110">Visual Basic gelecek bir sürümünde yeni bir anahtar sözcüğü bir var olan form veya denetim adı ile çakışan tanımlar, ancak daha sonra bu tekniği kodunuzu güncelleştirirken yeni sürümle çalışmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74c01-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74c01-111">Programınız, ayrıca diğer başvurulan derlemelerde tarafından sağlanan öğe adları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="74c01-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="74c01-112">Bu adlar sınırlı anahtar sözcüklerle arasında çakışma varsa, daha sonra bunları köşeli ayraç yerleştirme tanımlanmış, öğelerin yorumlamaya Visual Basic neden olur.</span><span class="sxs-lookup"><span data-stu-id="74c01-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c01-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74c01-113">See also</span></span>

- [<span data-ttu-id="74c01-114">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="74c01-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="74c01-115">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="74c01-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="74c01-116">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="74c01-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
