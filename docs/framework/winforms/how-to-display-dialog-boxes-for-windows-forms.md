---
title: 'Nasıl yapılır: Windows Forms için İletişim Kutularını Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, displaying
- Windows Forms dialog boxes [Windows Forms], displaying
- Windows Forms, calling one form from another
- dialog boxes [Windows Forms], displaying for Windows Forms
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
ms.openlocfilehash: a25fe86c4dde1fed69e192956d77615bf2a70402
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Nasıl yapılır: Windows Forms için İletişim Kutularını Görüntüleme
Diğer bir uygulamada görüntülemek aynı şekilde bir iletişim kutusu görüntüler. Başlangıç formu uygulama çalıştırıldığında otomatik olarak yükler. İkinci form veya iletişim kutusu uygulamada görünür yapmak için yükleme ve görüntülemek için kod yazma. Benzer şekilde, form veya iletişim kutusu kaybolur, kaldırma veya gizlemek için kod yazma.  
  
### <a name="to-display-a-dialog-box"></a>Bir iletişim kutusu görüntülemek için  
  
1.  İletişim kutusunu açmak istediğiniz olay işleyicisi gidin. Menü komutu seçildiğinde bir düğme tıklatıldığında veya başka bir olay olduğunda oluşabilir.  
  
2.  Olay işleyicisi iletişim kutusunu açmak için kodu ekleyin. Bu örnekte, bir düğme tıklama olayı iletişim kutusunu göstermek için kullanılır:  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim dlg1 as new Form()  
       dlg1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       Form dlg1 = new Form();  
       dlg1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:   
      void button1_Click(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        Form ^ dlg1 = gcnew Form();  
        dlg1->ShowDialog();  
      }  
    ```
