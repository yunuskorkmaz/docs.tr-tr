---
title: "Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama (Windows Forms)"
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
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 429c0c928d8bff4f837186040288d9447fc18687
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama (Windows Forms)
Programlı olarak bir Windows Forms tarafından görüntülenen resmi ayarlama <xref:System.Windows.Forms.PictureBox> denetim.  
  
### <a name="to-set-a-picture-programmatically"></a>Bir resmi programlı olarak ayarlamak için  
  
-   Ayarlama <xref:System.Windows.Forms.PictureBox.Image%2A> özelliğini kullanarak <xref:System.Drawing.Image.FromFile%2A> yöntemi <xref:System.Drawing.Image> sınıfı.  
  
     Aşağıdaki örnekte görüntüsünün konumunu ayarlayın Belgelerim klasörünü yoludur. Windows işletim sistemi çalıştıran bilgisayarların çoğu bu dizin içerdiğini varsayar çünkü bu, gerçekleştirilir. Bu, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri olan kullanıcılar da sağlar. Aşağıdaki örnek bir formla varsayar bir <xref:System.Windows.Forms.PictureBox> denetimi zaten eklendi.  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a>Grafik temizlemek için  
  
-   İlk olarak, görüntü tarafından kullanılan belleği serbest ve grafiğin temizleyin. Bellek yönetimi bir sorun olursa çöp toplama belleği daha sonra boş.  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    >  Neden hakkında daha fazla bilgi için kullanmanız gereken <xref:System.Drawing.Image.Dispose%2A> yöntemi bu şekilde bkz [yönetilmeyen kaynakları Temizleme](../../../../docs/standard/garbage-collection/unmanaged.md).  
  
     Grafik tasarım zamanında denetime yüklendi olsa bile bu kodu görüntü temizleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.PictureBox>  
 <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>  
 [PictureBox denetimine genel bakış](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [Nasıl yapılır: tasarımcıyı kullanarak resim yükleme](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [Nasıl yapılır: çalışma zamanında boyutunu veya resim konumunu değiştirme](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [PictureBox denetimi](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
