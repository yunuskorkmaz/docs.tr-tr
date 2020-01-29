---
title: 'Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
ms.openlocfilehash: 9bb094ce0b7945f23a2e9b8614e56c9492d5f832
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736029"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme (Windows Forms)
Bir form üzerinde Windows Forms <xref:System.Windows.Forms.PictureBox> denetimini kullanıyorsanız, üzerinde <xref:System.Windows.Forms.PictureBox.SizeMode%2A> özelliğini şu şekilde ayarlayabilirsiniz:  
  
- Resmin sol üst köşesini denetimin sol üst köşesinden hizalayın  
  
- Denetimin içindeki resmi Ortala  
  
- Denetimin boyutunu gösterdiği resme uyacak şekilde ayarlayın  
  
- Denetimin sığması için görüntülediği tüm resimleri uzat  
  
 Bir resmi uzatma (özellikle bit eşlem biçiminde), görüntü kalitesinde bir kayıp üretebilir. Çalışma zamanında görüntülerin çizilmesine yönelik grafik yönergelerinin listesi olan meta dosyalar, bit eşlemlerden uzama için daha uygundur.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Çalışma zamanında SizeMode özelliğini ayarlamak için  
  
1. <xref:System.Windows.Forms.PictureBox.SizeMode%2A> <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (varsayılan), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>veya <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>olarak ayarlayın. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal>, görüntünün denetimin sol üst köşesine yerleştirildiği anlamına gelir; görüntü denetimden büyükse, alt ve sağ kenarları kırpılır. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, görüntünün denetimin içinde ortalanmasıdır; görüntü denetimden büyükse, resmin dış kenarları kırpılır. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, denetimin boyutunun görüntünün boyutuna ayarlandığı anlamına gelir. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> ters ve görüntünün boyutunun denetimin boyutuna ayarlandığı anlamına gelir.  
  
     Aşağıdaki örnekte, görüntü konumu için ayarlanan yol Belgelerim klasörüdür. Bu, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içerdiğini varsaydığı için yapılır. Bu Ayrıca, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır. Aşağıdaki örnekte, <xref:System.Windows.Forms.PictureBox> denetimi zaten eklenmiş bir form varsayılır.  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PictureBox>
- [Nasıl yapılır: Tasarımcıyı Kullanarak Resim Yükleme](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [PictureBox Denetimine Genel Bakış](picturebox-control-overview-windows-forms.md)
- [Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox Denetimi](picturebox-control-windows-forms.md)
