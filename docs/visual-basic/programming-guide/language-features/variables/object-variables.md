---
title: Visual Basic'de Nesne Değişkenleri
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 8383261c1806732c4c8abea9834000f003a848a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649119"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="97941-102">Visual Basic'de Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="97941-102">Object Variables in Visual Basic</span></span>
<span data-ttu-id="97941-103">Bir değişken değerlerini doğrudan depolama yanı sıra, bir nesneye başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="97941-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="97941-104">Aynı nedenden dolayı bir değişkene herhangi bir değer atamak için bir nesne bir değişkene atayın:</span><span class="sxs-lookup"><span data-stu-id="97941-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>  
  
-   <span data-ttu-id="97941-105">Bir değişken adı daha kısa ve yöntemleri ve özellikleri nesnesine erişmek gerekli tam yolunu anımsaması kolay görülür.</span><span class="sxs-lookup"><span data-stu-id="97941-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>  
  
-   <span data-ttu-id="97941-106">Nesneye başvuran bir değişkeni kullanarak, art arda nesne özellikleri ve gerekli yöntemleri erişimden çok daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="97941-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>  
  
-   <span data-ttu-id="97941-107">Kodunuzun çalıştığı sırada başka nesnelere atıfta için bir değişken değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97941-107">You can change a variable to refer to other objects while your code is running.</span></span>  
  
## <a name="making-code-shorter"></a><span data-ttu-id="97941-108">Kod kısa yapma</span><span class="sxs-lookup"><span data-stu-id="97941-108">Making Code Shorter</span></span>  
 <span data-ttu-id="97941-109">Nesne değişkenleri yazmak zorunda kod kısaltmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97941-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="97941-110">Aşağıdaki örnek, erişmek için yöntemler ve özellikler tam yolunu kullanır. bir <xref:System.Windows.Forms.Control> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="97941-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 <span data-ttu-id="97941-111">Bu kod kısaltın ve denetim için bir nesne değişkeni kullanırsanız yürütmesini kurma hızı.</span><span class="sxs-lookup"><span data-stu-id="97941-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="97941-112">Nesne değişkeni atamak istediğiniz belirli sınıfı ile bildirmelisiniz (`Control` bu durumda).</span><span class="sxs-lookup"><span data-stu-id="97941-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="97941-113">Değişkenine bir nesne atadıktan sonra başvurduğu nesne işlemek gibi onu tam olarak aynı şekilde davranabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97941-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="97941-114">Ayarlayabilir veya nesne özelliklerini al veya yöntemlerinden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="97941-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="97941-115">Aşağıdaki örnek, önceki örnekte kodu basitleştirmek için bir nesne değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="97941-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a><span data-ttu-id="97941-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97941-116">See Also</span></span>  
 [<span data-ttu-id="97941-117">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="97941-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="97941-118">Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma</span><span class="sxs-lookup"><span data-stu-id="97941-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [<span data-ttu-id="97941-119">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="97941-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="97941-120">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="97941-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="97941-121">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="97941-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
