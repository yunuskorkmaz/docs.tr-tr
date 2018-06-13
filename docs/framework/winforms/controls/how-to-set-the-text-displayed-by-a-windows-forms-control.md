---
title: 'Nasıl yapılır: Windows Formları Denetimi Tarafından Görüntülenen Metni Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: d39b0b7ccf95f0da22086a72aa2cee424d7ea8ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535619"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Nasıl yapılır: Windows Formları Denetimi Tarafından Görüntülenen Metni Ayarlama
Windows Forms denetimleri genellikle denetimi birincil işlev için ilgili bazı metinleri görüntüler. Örneğin, bir <xref:System.Windows.Forms.Button> denetimi genellikle düğme tıklatıldığında ne gerçekleştirilen gösteren resim yazısı görüntüler. Tüm denetimler için ayarlama veya kullanarak metin döndürme <xref:System.Windows.Forms.Control.Text%2A> özelliği. Yazı tipi kullanarak değiştirebilirsiniz <xref:System.Windows.Forms.Control.Font%2A> özelliği. Tasarımcı kullanarak metin de ayarlayabilirsiniz.  Ayrıca bkz. [nasıl yapılır: oluşturmak erişim anahtarları için Windows Forms denetimleri kullanarak Tasarımcı](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [nasıl yapılır: Tasarımcı kullanarak bir Windows Forms denetimi görüntülenen metin ayarlamak](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [nasıl: resmi ayarlama Tarafından görüntülenen Tasarımcı kullanarak bir Windows Formları denetimi](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a>Program aracılığıyla bir denetimi tarafından görüntülenen metni ayarlamak için  
  
1.  Ayarlama <xref:System.Windows.Forms.Control.Text%2A> bir dize özelliği.  
  
     Bir altı çizili erişim anahtarı oluşturmak için içerir ve işareti (&) erişim tuşu olacaktır harf önce.  
  
2.  Ayarlama <xref:System.Windows.Forms.Control.Font%2A> türünde bir nesne için özellik <xref:System.Drawing.Font>.  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  Çıkış karakteri, bir özel karakter normalde bunları farklı şekilde, menü öğeleri gibi yorumlar kullanıcı arabirimi öğeleri görüntülemek için kullanabilirsiniz. Örneğin, aşağıdaki kod satırını okumak için menü öğesinin metin ayarlar "& bir şey için şimdi tamamen farklı":  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>  
 [Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
