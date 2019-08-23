---
title: 'Nasıl yapılır: Windows Forms için Çalışma Zamanındaki Olay İşleyicileri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
ms.openlocfilehash: 440086bfd5384fc46aec2997dbdd9937f7a1b65f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964328"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="6900a-102">Nasıl yapılır: Windows Forms için Çalışma Zamanındaki Olay İşleyicileri</span><span class="sxs-lookup"><span data-stu-id="6900a-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>

<span data-ttu-id="6900a-103">Visual Studio 'da Windows Form Tasarımcısı kullanarak olay oluşturmaya ek olarak, çalışma zamanında bir olay işleyicisi de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6900a-103">In addition to creating events using the Windows Forms Designer in Visual Studio, you can also create an event handler at run time.</span></span> <span data-ttu-id="6900a-104">Bu eylem, çalışma zamanında kod içindeki koşullara bağlı olarak, program ilk başladığında bağlanmaktan farklı olarak olay işleyicilerini bağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6900a-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>

## <a name="create-an-event-handler-at-run-time"></a><span data-ttu-id="6900a-105">Çalışma zamanında olay işleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6900a-105">Create an event handler at run time</span></span>

1. <span data-ttu-id="6900a-106">Bir olay işleyicisi eklemek istediğiniz formu açın.</span><span class="sxs-lookup"><span data-stu-id="6900a-106">Open the form that you want to add an event handler to.</span></span>

2. <span data-ttu-id="6900a-107">İşlemek istediğiniz olay için yöntem imzasıyla formunuza bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6900a-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>

     <span data-ttu-id="6900a-108">Örneğin, bir <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.Button> denetimin olayını işsaydı, aşağıdaki gibi bir yöntem oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="6900a-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>

    ```vb
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)
       ' Add event handler code here.
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
    // Add event handler code here.
    }
    ```

    ```cpp
    private:
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          // Add event handler code here.
       }
    ```

3. <span data-ttu-id="6900a-109">Uygulamanıza uygun şekilde olay işleyicisine kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6900a-109">Add code to the event handler as appropriate to your application.</span></span>

4. <span data-ttu-id="6900a-110">Hangi form veya denetimi için bir olay işleyicisi oluşturmak istediğinizi saptayın.</span><span class="sxs-lookup"><span data-stu-id="6900a-110">Determine which form or control you want to create an event handler for.</span></span>

5. <span data-ttu-id="6900a-111">Formunuzun sınıfının içindeki bir yöntemde, olayı işlemek için olay işleyicisini belirten kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6900a-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="6900a-112">Örneğin, aşağıdaki kod olay işleyicisini `button1_Click` bir <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olayını işlediğini belirtir:</span><span class="sxs-lookup"><span data-stu-id="6900a-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <span data-ttu-id="6900a-113">Yukarıdaki Visual Basic kodda gösterilen yöntemidüğmeiçinbirtıklamaolayıişleyicisioluşturur.<xref:System.ComponentModel.EventHandlerList.AddHandler%2A></span><span class="sxs-lookup"><span data-stu-id="6900a-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>

## <a name="see-also"></a><span data-ttu-id="6900a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6900a-114">See also</span></span>

- [<span data-ttu-id="6900a-115">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6900a-115">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="6900a-116">Olay İşleyicilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6900a-116">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="6900a-117">Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme</span><span class="sxs-lookup"><span data-stu-id="6900a-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
