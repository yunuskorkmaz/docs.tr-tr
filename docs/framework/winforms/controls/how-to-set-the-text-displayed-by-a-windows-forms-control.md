---
title: 'Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama'
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
ms.openlocfilehash: 59570af89e6236e3c13866d45dc5361d52b84274
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013094"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama
Windows Forms denetimleri, genellikle denetimin birincil işleve ilgili bazı metin görüntüler. Örneğin, bir <xref:System.Windows.Forms.Button> denetimi genellikle düğmesine tıklandığında hangi eylemin gerçekleştirileceğini belirten bir başlık görüntüler. Tüm denetimler için ayarlayabilir veya dönüş metni kullanarak <xref:System.Windows.Forms.Control.Text%2A> özelliği. Yazı tipi kullanarak değiştirebileceğiniz <xref:System.Windows.Forms.Control.Font%2A> özelliği. Tasarımcı kullanarak metin de ayarlayabilirsiniz.  Ayrıca bkz: [nasıl yapılır: Windows Forms Tasarımcısı'nı kullanarak denetimleri için erişim tuşları oluşturma](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [nasıl yapılır: Tarafından görüntülenen metni ayarlama bir Windows Forms Tasarımcısı'nı kullanarak denetimi](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [nasıl yapılır: Tarafından görüntülenen resmi ayarlama bir Windows Forms Tasarımcısı'nı kullanarak denetimi](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a>Program aracılığıyla bir denetimi tarafından görüntülenen metni ayarlama  
  
1. Ayarlama <xref:System.Windows.Forms.Control.Text%2A> bir dize özelliği.  
  
     Bir altı çizili erişim anahtarı oluşturmak için içeren bir ampersan (&) erişim anahtarı olacak harfi önce.  
  
2. Ayarlama <xref:System.Windows.Forms.Control.Font%2A> türünde bir nesne özelliğini <xref:System.Drawing.Font>.  
  
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
    >  Bir kaçış karakteri, bir özel karakter normalde bunları farklı menü öğeleri gibi yorumlar kullanıcı arabirimi öğelerini görüntülemek için kullanabilirsiniz. Örneğin, menü öğesinin metin okumak için aşağıdaki kod satırını ayarlar "& şimdi bir şey için tamamen farklı":  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Windows Forms denetimleri için erişim tuşları oluşturma](how-to-create-access-keys-for-windows-forms-controls.md)
- [Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme](how-to-respond-to-windows-forms-button-clicks.md)
