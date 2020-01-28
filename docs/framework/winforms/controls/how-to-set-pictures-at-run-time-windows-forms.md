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
ms.openlocfilehash: bd0509c05fd9c1cfc0c631fcd613c64d20296f6b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746740"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama (Windows Forms)
Bir Windows Forms <xref:System.Windows.Forms.PictureBox> denetimi tarafından görünen görüntüyü programlı bir şekilde ayarlayabilirsiniz.  
  
### <a name="to-set-a-picture-programmatically"></a>Bir resmi programlı bir şekilde ayarlamak için  
  
- <xref:System.Drawing.Image> sınıfının <xref:System.Drawing.Image.FromFile%2A> yöntemini kullanarak <xref:System.Windows.Forms.PictureBox.Image%2A> özelliğini ayarlayın.  
  
     Aşağıdaki örnekte, görüntü konumu için ayarlanan yol Belgelerim klasörüdür. Bu, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içerdiğini varsaydığı için yapılır. Bu Ayrıca, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır. Aşağıdaki örnekte, <xref:System.Windows.Forms.PictureBox> denetimi zaten eklenmiş bir form varsayılır.  
  
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
  
### <a name="to-clear-a-graphic"></a>Grafiği temizlemek için  
  
- İlk olarak, görüntü tarafından kullanılan belleği serbest bırakın ve grafiği temizleyin. Bellek yönetimi bir sorun haline gelirse çöp toplama belleği daha sonra boşaltacaktır.  
  
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
    > <xref:System.Drawing.Image.Dispose%2A> yöntemini bu şekilde nasıl kullanmanız gerektiği hakkında daha fazla bilgi için bkz. [yönetilmeyen kaynakları temizleme](../../../standard/garbage-collection/unmanaged.md).  
  
     Bu kod, tasarım zamanında denetime bir grafik yüklense bile görüntüyü temizler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [PictureBox Denetimine Genel Bakış](picturebox-control-overview-windows-forms.md)
- [Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox Denetimi](picturebox-control-windows-forms.md)
