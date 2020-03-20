---
title: 'Nasıl Yapılsın: İletişim Kutularını Görüntüle'
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
ms.openlocfilehash: 3625080c7c322e297a9de92e4f95a40c0caf3e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181968"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Nasıl yapılır: Windows Forms için İletişim Kutularını Görüntüleme
Bir iletişim kutusunu, bir uygulamada başka bir formu görüntülediğiniz gibi görüntülersiniz. Uygulama çalıştırıldığında başlangıç formu otomatik olarak yüklenir. Uygulamada ikinci bir form veya iletişim kutusunun görünmesini sağlamak için yüklemek ve görüntülemek için kod yazın. Benzer şekilde, form veya iletişim kutusunun kaybolmasını sağlamak için, kaldırmak veya gizlemek için kod yazın.  
  
### <a name="to-display-a-dialog-box"></a>İletişim kutusunu görüntülemek için  
  
1. İletişim kutusunu açmak istediğiniz olay işleyicisine gidin. Bu, bir menü komutu seçildiğinde, bir düğme tıklatıldığında veya başka bir olay oluştuğunda oluşabilir.  
  
2. Olay işleyicisinde, iletişim kutusunu açmak için kod ekleyin. Bu örnekte, iletişim kutusunu göstermek için bir düğme tıklatma olayı kullanılır:  
  
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
