---
title: "Nasıl yapılır: Windows Forms için Çalışma Zamanındaki Olay İşleyicileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53664bcf8c776338399297687a16ec430bca128b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="4ad32-102">Nasıl yapılır: Windows Forms için Çalışma Zamanındaki Olay İşleyicileri</span><span class="sxs-lookup"><span data-stu-id="4ad32-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>
<span data-ttu-id="4ad32-103">Windows Forms Tasarımcısı'nı kullanarak olayları oluşturmaya ek olarak, çalışma zamanında bir olay işleyicisi de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ad32-103">In addition to creating events using the Windows Forms Designer, you can also create an event handler at run time.</span></span> <span data-ttu-id="4ad32-104">Bu eylem, onları programı ilk kez başlatıldığında, bağlı olan aksine çalışma zamanında koşulları kod göre olay işleyicileri bağlanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ad32-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>  
  
### <a name="to-create-an-event-handler-at-run-time"></a><span data-ttu-id="4ad32-105">Çalışma zamanında bir olay işleyicisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4ad32-105">To create an event handler at run time</span></span>  
  
1.  <span data-ttu-id="4ad32-106">Formu kod bir olay işleyicisi eklemek istediğiniz düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="4ad32-106">Open the form in the Code Editor that you want to add an event handler to.</span></span>  
  
2.  <span data-ttu-id="4ad32-107">Formunuz yöntemi imzalı işlemek istediğiniz olayı için bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4ad32-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>  
  
     <span data-ttu-id="4ad32-108">Örneğin, işleme <xref:System.Windows.Forms.Control.Click> olayı bir <xref:System.Windows.Forms.Button> denetimi, aşağıdaki gibi bir yöntem oluşturma:</span><span class="sxs-lookup"><span data-stu-id="4ad32-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>  
  
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
  
3.  <span data-ttu-id="4ad32-109">Uygulamanız için uygun şekilde olay işleyicisi için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4ad32-109">Add code to the event handler as appropriate to your application.</span></span>  
  
4.  <span data-ttu-id="4ad32-110">Hangi form veya denetim için bir olay işleyicisi oluşturmak istediğiniz belirler.</span><span class="sxs-lookup"><span data-stu-id="4ad32-110">Determine which form or control you want to create an event handler for.</span></span>  
  
5.  <span data-ttu-id="4ad32-111">İçindeki bir yöntemi, formun sınıfı içinde olayını işlemek için olay işleyicisini belirtir kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4ad32-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="4ad32-112">Örneğin, aşağıdaki kodu olay işleyicisi belirtir `button1_Click` tanıtıcıları <xref:System.Windows.Forms.Control.Click> olayı bir <xref:System.Windows.Forms.Button> denetimi:</span><span class="sxs-lookup"><span data-stu-id="4ad32-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="4ad32-113"><xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Yukarıdaki Visual Basic kodunda gösterilen yöntemi düğmenin click olay işleyicisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4ad32-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad32-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ad32-114">See Also</span></span>  
 [<span data-ttu-id="4ad32-115">Windows Forms'ta olay işleyicileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ad32-115">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="4ad32-116">Olay işleyicilerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="4ad32-116">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 [<span data-ttu-id="4ad32-117">Devralınmış olay işleyicileri Visual Basic sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="4ad32-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
