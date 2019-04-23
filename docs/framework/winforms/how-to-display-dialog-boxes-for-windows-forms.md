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
ms.openlocfilehash: b99f2273dae88faf86448da6e1d2986a83803abf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773824"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Nasıl yapılır: Windows Forms için İletişim Kutularını Görüntüleme
Uygulamada herhangi bir biçimde görüntüler aynı şekilde bir iletişim kutusu görüntüler. Uygulamayı çalıştırdığınızda başlangıç formu otomatik olarak yükler. İkinci form veya iletişim kutusu uygulamada görünür hale getirmek için yükleme ve görüntüleme için kod yazın. Benzer şekilde, form veya iletişim kutusu kaybolur, kaldırma veya gizlemek için kod yazın.  
  
### <a name="to-display-a-dialog-box"></a>İletişim kutusunu görüntülemek için  
  
1. İletişim kutusunu açmak istediğiniz olay işleyicisine Git. Bir menü komutu seçildiğinde bir düğme tıklandığında ya da başka bir olay meydana geldiğinde bu durum oluşabilir.  
  
2. Olay işleyicisi, iletişim kutusunu açmak için kodu ekleyin. Bu örnekte, bir düğme tıklama olayı, iletişim kutusunu göstermek için kullanılır:  
  
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
