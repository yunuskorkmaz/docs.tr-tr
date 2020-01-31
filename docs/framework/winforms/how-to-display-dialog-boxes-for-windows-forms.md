---
title: 'Nasıl yapılır: Iletişim kutularını görüntüleme'
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
ms.openlocfilehash: dd04a06eaa0dd7583ef2f72edb4cffa99aaaa60c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739468"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Nasıl yapılır: Windows Forms için İletişim Kutularını Görüntüleme
Bir iletişim kutusunu, bir uygulamadaki diğer formları görüntülerken kullandığınız şekilde görüntüleyebilirsiniz. Başlangıç formu, uygulama çalıştırıldığında otomatik olarak yüklenir. Uygulamada ikinci bir form veya iletişim kutusu görüntülenmesini sağlamak için kodu yazın ve görüntüleyin. Benzer şekilde, form veya iletişim kutusunun kaybolması için, kaldırmak veya gizlemek için kod yazın.  
  
### <a name="to-display-a-dialog-box"></a>Bir iletişim kutusunu göstermek için  
  
1. İletişim kutusunu açmak istediğiniz olay işleyicisine gidin. Bu, bir menü komutu seçildiğinde, bir düğmeye tıklandığında veya başka herhangi bir olay gerçekleştiğinde meydana gelir.  
  
2. Olay işleyicisinde, iletişim kutusunu açmak için kod ekleyin. Bu örnekte, iletişim kutusunu göstermek için bir düğme tıklama olayı kullanılır:  
  
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
