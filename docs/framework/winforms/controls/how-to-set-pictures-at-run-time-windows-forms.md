---
title: 'Nasıl yapılır: Çalışma zamanında resimleri ayarlama (Windows Forms)'
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
ms.openlocfilehash: 99d78a275c8ad8f55d9b0832a794545b65da7e20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917523"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Nasıl yapılır: Çalışma zamanında resimleri ayarlama (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PictureBox> denetimi tarafından görünen görüntüyü programlı bir şekilde ayarlayabilirsiniz.  
  
### <a name="to-set-a-picture-programmatically"></a>Bir resmi programlı bir şekilde ayarlamak için  
  
- <xref:System.Windows.Forms.PictureBox.Image%2A> Sınıfının yöntemini<xref:System.Drawing.Image.FromFile%2A>kullanaraközelliğiayarlayın. <xref:System.Drawing.Image>  
  
     Aşağıdaki örnekte, görüntü konumu için ayarlanan yol Belgelerim klasörüdür. Bu, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içerdiğini varsaydığı için yapılır. Bu Ayrıca, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır. Aşağıdaki örnekte, bir <xref:System.Windows.Forms.PictureBox> denetimin zaten eklendiği bir form varsayılır.  
  
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
    > <xref:System.Drawing.Image.Dispose%2A> Yöntemi bu şekilde nasıl kullanmanız gerektiği hakkında daha fazla bilgi için bkz. [yönetilmeyen kaynakları temizleme](../../../standard/garbage-collection/unmanaged.md).  
  
     Bu kod, tasarım zamanında denetime bir grafik yüklense bile görüntüyü temizler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [PictureBox Denetimine Genel Bakış](picturebox-control-overview-windows-forms.md)
- [Nasıl yapılır: Tasarımcıyı kullanarak resim yükleme](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Nasıl yapılır: Çalışma zamanında bir resmin boyutunu veya yerleşimini değiştirme](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox Denetimi](picturebox-control-windows-forms.md)
