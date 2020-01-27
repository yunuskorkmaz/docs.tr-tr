---
title: 'Nasıl yapılır: çalışma zamanında olay Işleyicileri oluşturma'
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
ms.openlocfilehash: 0b496a3da77c5bcf7a08c435edba468a7c5809cb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739502"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Nasıl yapılır: Windows Forms için Çalışma Zamanındaki Olay İşleyicileri

Visual Studio 'da Windows Form Tasarımcısı kullanarak olay oluşturmaya ek olarak, çalışma zamanında bir olay işleyicisi de oluşturabilirsiniz. Bu eylem, çalışma zamanında kod içindeki koşullara bağlı olarak, program ilk başladığında bağlanmaktan farklı olarak olay işleyicilerini bağlamanıza olanak tanır.

## <a name="create-an-event-handler-at-run-time"></a>Çalışma zamanında olay işleyicisi oluşturma

1. Bir olay işleyicisi eklemek istediğiniz formu açın.

2. İşlemek istediğiniz olay için yöntem imzasıyla formunuza bir yöntem ekleyin.

     Örneğin, bir <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Click> olayını işlebiliyorsanız, aşağıdaki gibi bir yöntem oluşturursunuz:

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

3. Uygulamanıza uygun şekilde olay işleyicisine kod ekleyin.

4. Hangi form veya denetimi için bir olay işleyicisi oluşturmak istediğinizi saptayın.

5. Formunuzun sınıfının içindeki bir yöntemde, olayı işlemek için olay işleyicisini belirten kodu ekleyin. Örneğin, aşağıdaki kod, bir <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Click> olayını işleyen `button1_Click` olay işleyicisini belirtir:

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     Yukarıdaki Visual Basic kodda gösterilen <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> yöntemi düğme için bir tıklama olayı işleyicisi oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)
- [Olay İşleyicilerine Genel Bakış](event-handlers-overview-windows-forms.md)
- [Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
