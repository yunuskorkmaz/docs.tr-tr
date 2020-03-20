---
title: 'Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama'
ms.date: 03/30/2017
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
ms.openlocfilehash: cd599ac7e07b5210f8bcff1ffbc76b3d9ee563d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182113"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PictureBox> denetimi tarafından görüntülenen görüntüyü programlı olarak ayarlayabilirsiniz.  
  
### <a name="to-set-a-picture-programmatically"></a>Resmi programlı olarak ayarlamak için  
  
- Sınıfın <xref:System.Windows.Forms.PictureBox.Image%2A> yöntemini <xref:System.Drawing.Image.FromFile%2A> kullanarak özelliği ayarlayın. <xref:System.Drawing.Image>  
  
     Aşağıdaki örnekte, görüntünün konumu için ayarlanan yol Belgelerim klasörüdür. Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içereceğini varsayabileceğinizden, bu işlem yapılır. Bu aynı zamanda en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenli bir şekilde çalıştırmasına olanak tanır. Aşağıdaki <xref:System.Windows.Forms.PictureBox> örnekte, denetimzaten eklenmiştir.  
  
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
  
### <a name="to-clear-a-graphic"></a>Bir grafiği temizlemek için  
  
- Önce görüntü tarafından kullanılan belleği bırakın ve ardından grafiği temizleyin. Bellek yönetimi bir sorun haline gelirse çöp toplama daha sonra bellek kadar serbest olacaktır.  
  
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
    > <xref:System.Drawing.Image.Dispose%2A> Yöntemi neden bu şekilde kullanmanız gerektiği hakkında daha fazla bilgi için, [Yönetilmeyen Kaynakları Temizleme'ye](../../../standard/garbage-collection/unmanaged.md)bakın.  
  
     Bu kod, bir grafik tasarım zamanında denetime yüklense bile görüntüyü temizler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [PictureBox Denetimine Genel Bakış](picturebox-control-overview-windows-forms.md)
- [Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox Denetimi](picturebox-control-windows-forms.md)
