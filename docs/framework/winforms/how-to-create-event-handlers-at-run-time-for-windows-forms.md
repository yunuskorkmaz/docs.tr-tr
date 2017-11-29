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
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Nasıl yapılır: Windows Forms için Çalışma Zamanındaki Olay İşleyicileri
Windows Forms Tasarımcısı'nı kullanarak olayları oluşturmaya ek olarak, çalışma zamanında bir olay işleyicisi de oluşturabilirsiniz. Bu eylem, onları programı ilk kez başlatıldığında, bağlı olan aksine çalışma zamanında koşulları kod göre olay işleyicileri bağlanmanızı sağlar.  
  
### <a name="to-create-an-event-handler-at-run-time"></a>Çalışma zamanında bir olay işleyicisi oluşturmak için  
  
1.  Formu kod bir olay işleyicisi eklemek istediğiniz düzenleyicisinde açın.  
  
2.  Formunuz yöntemi imzalı işlemek istediğiniz olayı için bir yöntem ekleyin.  
  
     Örneğin, işleme <xref:System.Windows.Forms.Control.Click> olayı bir <xref:System.Windows.Forms.Button> denetimi, aşağıdaki gibi bir yöntem oluşturma:  
  
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
  
3.  Uygulamanız için uygun şekilde olay işleyicisi için kod ekleyin.  
  
4.  Hangi form veya denetim için bir olay işleyicisi oluşturmak istediğiniz belirler.  
  
5.  İçindeki bir yöntemi, formun sınıfı içinde olayını işlemek için olay işleyicisini belirtir kodu ekleyin. Örneğin, aşağıdaki kodu olay işleyicisi belirtir `button1_Click` tanıtıcıları <xref:System.Windows.Forms.Control.Click> olayı bir <xref:System.Windows.Forms.Button> denetimi:  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Yukarıdaki Visual Basic kodunda gösterilen yöntemi düğmenin click olay işleyicisi oluşturur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'ta olay işleyicileri oluşturma](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Olay işleyicilerine genel bakış](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 [Devralınmış olay işleyicileri Visual Basic sorunlarını giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
