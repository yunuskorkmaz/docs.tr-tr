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
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Nasıl yapılır: Windows Forms için Çalışma Zamanındaki Olay İşleyicileri

Visual Studio 'da Windows Form Tasarımcısı kullanarak olay oluşturmaya ek olarak, çalışma zamanında bir olay işleyicisi de oluşturabilirsiniz. Bu eylem, çalışma zamanında kod içindeki koşullara bağlı olarak, program ilk başladığında bağlanmaktan farklı olarak olay işleyicilerini bağlamanıza olanak tanır.

## <a name="create-an-event-handler-at-run-time"></a>Çalışma zamanında olay işleyicisi oluşturma

1. Bir olay işleyicisi eklemek istediğiniz formu açın.

2. İşlemek istediğiniz olay için yöntem imzasıyla formunuza bir yöntem ekleyin.

     Örneğin, <xref:System.Windows.Forms.Control.Click> bir <xref:System.Windows.Forms.Button> denetimin olayını işsaydı, aşağıdaki gibi bir yöntem oluşturursunuz:

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

5. Formunuzun sınıfının içindeki bir yöntemde, olayı işlemek için olay işleyicisini belirten kodu ekleyin. Örneğin, aşağıdaki kod olay işleyicisini `button1_Click` <xref:System.Windows.Forms.Control.Click> bir denetimin olayını işlediğini belirtir <xref:System.Windows.Forms.Button> :

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <xref:System.ComponentModel.EventHandlerList.AddHandler%2A>Yukarıdaki Visual Basic kodda gösterilen yöntemi düğme için bir tıklama olayı işleyicisi oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)
- [Olay İşleyicilerine Genel Bakış](event-handlers-overview-windows-forms.md)
- [Visual Basic'de Devralınmış Olay İşleyicileri İle İlgili Sorun Giderme](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
