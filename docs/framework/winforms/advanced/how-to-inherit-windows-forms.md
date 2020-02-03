---
title: Form devralma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: cc3a4cc75fd13e8f193a6920ed5b4a9bc8fd5d74
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743329"
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="79e4d-102">Nasıl yapılır: Windows Formlarını Devralma</span><span class="sxs-lookup"><span data-stu-id="79e4d-102">How to: Inherit Windows Forms</span></span>

<span data-ttu-id="79e4d-103">Temel formlardan devralarak yeni Windows Forms oluşturmak, her ihtiyacınız olduğunda bir formu tamamen yeniden oluşturma işlemini gerçekleştirmeden en iyi çabalarınızı yinelemek için kullanışlı bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="79e4d-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>

<span data-ttu-id="79e4d-104">**Devralma Seçici** iletişim kutusunu kullanarak formları tasarım zamanında devralma ve devralınan denetimlerin güvenlik düzeyleri arasında görsel açıdan ayrım yapma hakkında daha fazla bilgi için bkz. [nasıl yapılır: formları devralma Seçicisi iletişim kutusu kullanarak](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)devralma.</span><span class="sxs-lookup"><span data-stu-id="79e4d-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>

> [!NOTE]
> <span data-ttu-id="79e4d-105">Formdan devralması için, bu formu içeren dosya veya ad alanı yürütülebilir bir dosyaya veya DLL 'ye derlenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="79e4d-105">In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="79e4d-106">Projeyi derlemek için **derleme** menüsünden **Oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="79e4d-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="79e4d-107">Ayrıca, form devralan sınıfa ad alanı başvurusu eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="79e4d-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span>

## <a name="inherit-a-form-programmatically"></a><span data-ttu-id="79e4d-108">Formu programlı bir şekilde devralma</span><span class="sxs-lookup"><span data-stu-id="79e4d-108">Inherit a form programmatically</span></span>

1. <span data-ttu-id="79e4d-109">Sınıfınıza, devralması istediğiniz formu içeren ad alanına bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="79e4d-109">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>

2. <span data-ttu-id="79e4d-110">Sınıf tanımı ' nda, formunu devralacak bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="79e4d-110">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="79e4d-111">Başvuru, formu içeren ad alanını, ardından bir nokta ve ardından temel formun adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="79e4d-111">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>

    ```vb
    Public Class Form2
        Inherits Namespace1.Form1
    ```

    ```csharp
    public class Form2 : Namespace1.Form1
    ```

 <span data-ttu-id="79e4d-112">Formları devralırken, her olay hem temel sınıf hem de devralınan sınıf tarafından işlendiği için, iki kez çağrılan olay işleyicileriyle ilgili sorunların olabileceğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="79e4d-112">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="79e4d-113">Bu sorundan kaçınmak hakkında daha fazla bilgi için bkz. [Visual Basic devralınan olay Işleyicilerinin sorunlarını giderme](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="79e4d-113">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79e4d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79e4d-114">See also</span></span>

- [<span data-ttu-id="79e4d-115">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="79e4d-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="79e4d-116">Imports Deyimi (.NET Ad Alanı ve Türü)</span><span class="sxs-lookup"><span data-stu-id="79e4d-116">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="79e4d-117">using</span><span class="sxs-lookup"><span data-stu-id="79e4d-117">using</span></span>](../../../csharp/language-reference/keywords/using.md)
- [<span data-ttu-id="79e4d-118">Taban Formun Görünüşünü Değiştirmenin Etkileri</span><span class="sxs-lookup"><span data-stu-id="79e4d-118">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)
- [<span data-ttu-id="79e4d-119">Windows Forms Görsel Devralma</span><span class="sxs-lookup"><span data-stu-id="79e4d-119">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
