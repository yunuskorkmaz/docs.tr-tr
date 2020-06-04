---
title: Nesne Değişkenleri
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: a5e61f9308d3484dc228a7d09cc2fd30a2f41b35
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410341"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="f87e3-102">Visual Basic'de Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f87e3-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="f87e3-103">Değerleri doğrudan depolamanın yanı sıra bir değişken bir nesneye başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="f87e3-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="f87e3-104">Bir değişkene herhangi bir değer atadığınız nedenlerle bir nesne atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f87e3-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="f87e3-105">Değişken adı genellikle daha kısadır ve nesneye erişmek için gereken yöntemlerin ve özelliklerin tam yolundan daha kolay anımsanacak.</span><span class="sxs-lookup"><span data-stu-id="f87e3-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="f87e3-106">Bir nesneye başvuran bir değişken kullanmak, gerekli yöntemler veya özellikler aracılığıyla nesnenin kendine sürekli olarak erişilmesinin daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="f87e3-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="f87e3-107">Kodunuzun çalıştığı sırada diğer nesnelere başvurmak için bir değişken değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f87e3-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="f87e3-108">Kodu daha kısa hale getirme</span><span class="sxs-lookup"><span data-stu-id="f87e3-108">Making Code Shorter</span></span>

<span data-ttu-id="f87e3-109">Yazmanız istediğiniz kodu kısaltmak için nesne değişkenlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f87e3-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="f87e3-110">Aşağıdaki örnek, bir nesneye erişmek için yöntemlerin ve özelliklerin tam yolunu kullanır <xref:System.Windows.Forms.Control> .</span><span class="sxs-lookup"><span data-stu-id="f87e3-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="f87e3-111">Denetim için bir nesne değişkeni kullanıyorsanız, bu kodu kısaltabilir ve yürütmeyi hızlandıraseçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f87e3-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="f87e3-112">Nesne değişkenini kendisine atamak istediğiniz belirli bir sınıfla bildirmeniz gerekir ( `Control` Bu durumda).</span><span class="sxs-lookup"><span data-stu-id="f87e3-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="f87e3-113">Değişkene bir nesne atadıktan sonra, başvurduğu nesneyi değerlendirdiğiniz kadar tam olarak aynı şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="f87e3-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="f87e3-114">Nesnenin özelliklerini ayarlayabilir veya alabilir ya da yöntemlerinden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f87e3-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="f87e3-115">Aşağıdaki örnek, önceki örnekteki kodu basitleştirmek için bir nesne değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="f87e3-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="f87e3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f87e3-116">See also</span></span>

- [<span data-ttu-id="f87e3-117">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="f87e3-117">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="f87e3-118">Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma</span><span class="sxs-lookup"><span data-stu-id="f87e3-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="f87e3-119">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="f87e3-119">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="f87e3-120">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="f87e3-120">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="f87e3-121">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="f87e3-121">Object Variable Values</span></span>](object-variable-values.md)
