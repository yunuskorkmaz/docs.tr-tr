---
title: Visual Basic'de Nesne Değişkenleri
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: cc5be13293a89e73d1790e94a99d7936f1711e12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961240"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="bba73-102">Visual Basic'de Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="bba73-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="bba73-103">Bir değişken değerlerini doğrudan depolama ek olarak, bir nesneye başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="bba73-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="bba73-104">Aynı nedenden dolayı bir değişkene bir değer atamak için bir nesne değişkenine atayın:</span><span class="sxs-lookup"><span data-stu-id="bba73-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="bba73-105">Bir değişken adı genellikle daha kısa ve kolay yöntemlere ve özelliklere nesneye erişmek için gereken tam yolunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bba73-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="bba73-106">Bir nesneye başvuruda bulunan bir değişken kullanarak sürekli nesne özellikleri ve gerekli yöntemleri erişimden çok daha verimli olur.</span><span class="sxs-lookup"><span data-stu-id="bba73-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="bba73-107">Bir değişken, kodunuzun çalıştığı sırada başka nesnelere atıfta değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bba73-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="bba73-108">Kodu kısa yapma</span><span class="sxs-lookup"><span data-stu-id="bba73-108">Making Code Shorter</span></span>

<span data-ttu-id="bba73-109">Kod yazmak zorunda kısaltmak için nesne değişkenleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bba73-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="bba73-110">Aşağıdaki örnek, erişmek için yöntemleri ve özellikleri tam yolunu kullanır. bir <xref:System.Windows.Forms.Control> nesne.</span><span class="sxs-lookup"><span data-stu-id="bba73-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="bba73-111">Bu kod kısaltın ve denetim için bir nesne değişkeninin kullanırsanız yürütme, hızlandırın.</span><span class="sxs-lookup"><span data-stu-id="bba73-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="bba73-112">Atamak istediğiniz belirli sınıfı ile nesne değişkeni bildirmelidir (`Control` bu durumda).</span><span class="sxs-lookup"><span data-stu-id="bba73-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="bba73-113">Bir nesne değişkenine atadığınızda, başvurduğu nesneyi kabul gibi bu tamamen aynı şekilde davranabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bba73-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="bba73-114">Ayarlayabilir veya nesnenin özelliklerini almak veya yöntemlerinden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bba73-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="bba73-115">Aşağıdaki örnek, önceki örnekte kodu basitleştirmek için bir nesne değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bba73-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="bba73-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bba73-116">See also</span></span>

- [<span data-ttu-id="bba73-117">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="bba73-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="bba73-118">Nasıl yapılır: Uzun bir nitelenmiş yola sahip nesneye erişimi hızlandırma</span><span class="sxs-lookup"><span data-stu-id="bba73-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="bba73-119">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="bba73-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="bba73-120">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="bba73-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="bba73-121">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="bba73-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
