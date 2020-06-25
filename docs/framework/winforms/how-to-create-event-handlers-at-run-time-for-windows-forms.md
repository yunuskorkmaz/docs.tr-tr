---
title: 'Nasıl yapılır: çalışma zamanında olay Işleyicileri oluşturma'
description: Visual Studio 'daki Windows Form Tasarımcısı çalışma zamanında olay işleyicisi oluşturmayı öğrenin. Bu eylem, çalışma zamanında olay işleyicilerini bağlamanıza olanak tanır.
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
ms.openlocfilehash: 857076c46377b3276154d9b193d4bbe51841828f
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325804"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="dea25-104">Nasıl yapılır: Windows Forms için Çalışma Zamanındaki Olay İşleyicileri</span><span class="sxs-lookup"><span data-stu-id="dea25-104">How to: Create Event Handlers at Run Time for Windows Forms</span></span>

<span data-ttu-id="dea25-105">Visual Studio 'da Windows Form Tasarımcısı kullanarak olay oluşturmaya ek olarak, çalışma zamanında bir olay işleyicisi de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dea25-105">In addition to creating events using the Windows Forms Designer in Visual Studio, you can also create an event handler at run time.</span></span> <span data-ttu-id="dea25-106">Bu eylem, çalışma zamanında kod içindeki koşullara bağlı olarak, program ilk başladığında bağlanmaktan farklı olarak olay işleyicilerini bağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dea25-106">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>

## <a name="create-an-event-handler-at-run-time"></a><span data-ttu-id="dea25-107">Çalışma zamanında olay işleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="dea25-107">Create an event handler at run time</span></span>

1. <span data-ttu-id="dea25-108">Bir olay işleyicisi eklemek istediğiniz formu açın.</span><span class="sxs-lookup"><span data-stu-id="dea25-108">Open the form that you want to add an event handler to.</span></span>

2. <span data-ttu-id="dea25-109">İşlemek istediğiniz olay için yöntem imzasıyla formunuza bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dea25-109">Add a method to your form with the method signature for the event that you want to handle.</span></span>

     <span data-ttu-id="dea25-110">Örneğin, <xref:System.Windows.Forms.Control.Click> bir <xref:System.Windows.Forms.Button> denetimin olayını işsaydı, aşağıdaki gibi bir yöntem oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="dea25-110">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>

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

3. <span data-ttu-id="dea25-111">Uygulamanıza uygun şekilde olay işleyicisine kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dea25-111">Add code to the event handler as appropriate to your application.</span></span>

4. <span data-ttu-id="dea25-112">Hangi form veya denetimi için bir olay işleyicisi oluşturmak istediğinizi saptayın.</span><span class="sxs-lookup"><span data-stu-id="dea25-112">Determine which form or control you want to create an event handler for.</span></span>

5. <span data-ttu-id="dea25-113">Formunuzun sınıfının içindeki bir yöntemde, olayı işlemek için olay işleyicisini belirten kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dea25-113">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="dea25-114">Örneğin, aşağıdaki kod olay işleyicisini `button1_Click` <xref:System.Windows.Forms.Control.Click> bir denetimin olayını işlediğini belirtir <xref:System.Windows.Forms.Button> :</span><span class="sxs-lookup"><span data-stu-id="dea25-114">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <span data-ttu-id="dea25-115"><xref:System.ComponentModel.EventHandlerList.AddHandler%2A>Yukarıdaki Visual Basic kodda gösterilen yöntemi düğme için bir tıklama olayı işleyicisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dea25-115">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>

## <a name="see-also"></a><span data-ttu-id="dea25-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dea25-116">See also</span></span>

- [<span data-ttu-id="dea25-117">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="dea25-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="dea25-118">Olay İşleyicilerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dea25-118">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="dea25-119">Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="dea25-119">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
