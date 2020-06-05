---
title: Code’da Öğe Adları Olarak Anahtar Sözcükler
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: a98f0b027700717b414d58e1284ddec655eb25f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403232"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="46334-102">Kodda Öğe Adları Olarak Anahtar Sözcükler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46334-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="46334-103">Değişken, sınıf veya üye gibi herhangi bir program öğesi, kısıtlanmış bir anahtar sözcükle aynı ada sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="46334-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="46334-104">Örneğin, adlı bir değişken oluşturabilirsiniz `Loop` .</span><span class="sxs-lookup"><span data-stu-id="46334-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="46334-105">Bununla birlikte, kısıtlanmış anahtar sözcüğüyle aynı ada sahip olan kendi sürümünüze başvurmak için, `Loop` `[ ]` Aşağıdaki örnekte gösterildiği gibi, tam nitelendirme dizesi ile önce veya köşeli ayraç () içine almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="46334-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="46334-106">Bunlardan herhangi birini yapmazsanız, Visual Basic iç `Loop` anahtar sözcüğünün kullanımını varsayar ve aşağıdaki örnekte olduğu gibi bir hata üretir:</span><span class="sxs-lookup"><span data-stu-id="46334-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="46334-107">Formlara ve denetimlere başvururken ve bir değişkeni bildirirken veya kısıtlanmış bir anahtar sözcükle aynı ada sahip bir yordam tanımlarken köşeli ayraçları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46334-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="46334-108">Adları nitelendirmek veya köşeli ayraçları dahil etmek kolay bir şekilde unutmak ve bu sayede kodunuzda hata ortaya çıkaracak ve okumayı zorlaştırmak kolaylaşır.</span><span class="sxs-lookup"><span data-stu-id="46334-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="46334-109">Bu nedenle, program öğelerinin adları olarak kısıtlı anahtar sözcükleri kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="46334-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="46334-110">Ancak, Visual Basic gelecek bir sürümü varolan bir formla veya denetim adıyla çakışan yeni bir anahtar sözcük tanımlıyorsa, kodunuzu yeni sürümle çalışacak şekilde güncelleştirirken bu tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46334-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46334-111">Programınız aynı zamanda başvurulan diğer derlemeler tarafından verilen öğe adlarını da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="46334-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="46334-112">Bu adlar, kısıtlanmış anahtar sözcüklerle çakışıyorsa, köşeli ayraç yerleştirmek Visual Basic, bunları tanımladığınız öğeler olarak yorumlamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="46334-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46334-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46334-113">See also</span></span>

- [<span data-ttu-id="46334-114">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="46334-114">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="46334-115">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="46334-115">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="46334-116">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="46334-116">Keywords</span></span>](../../language-reference/keywords/index.md)
