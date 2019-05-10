---
title: 'Nasıl yapılır: Çalışma zamanında (Windows Forms) boyutunu veya bir resim yerleşimini Değiştir'
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
ms.openlocfilehash: 695abf51870ef9164e4543a91b3183e801eee55f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649249"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Nasıl yapılır: Çalışma zamanında (Windows Forms) boyutunu veya bir resim yerleşimini Değiştir
Windows Forms kullanırsanız <xref:System.Windows.Forms.PictureBox> denetimi bir form üzerinde ayarladığınız <xref:System.Windows.Forms.PictureBox.SizeMode%2A> özelliği için:  
  
- Resmin sol üst köşesinde denetimin sol üst köşesinde ile Hizala  
  
- Merkezi Denetim içindeki resmi  
  
- Denetimin görüntülediği resmi uyacak şekilde boyutu değiştirin  
  
- Denetime sığması için görüntüler herhangi bir resmi Uzat  
  
 Bir resim (özellikle bir bit eşlem biçimi) uzatma görüntü kalitesini kaybına neden olabilir. Çalışma zamanında resimleri çizim için grafik yönergeleri listeleridir, meta dosyaları, bit eşlemler daha uzatma için daha uygundur.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Çalışma zamanında SizeMode özelliğini ayarlamak için  
  
1. Ayarlama <xref:System.Windows.Forms.PictureBox.SizeMode%2A> için <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (varsayılan), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, veya <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> Görüntü denetimin sol üst köşedeki yerleştirilir anlamına gelir; görüntü denetimi büyükse, kendi alt ve sağ kenarları kırpılır. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> görüntü denetimi içinde ortalanır anlamına gelir; görüntü denetimi büyükse, resmin dış kenarları kırpılır. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> Denetimin boyutunu görüntü boyutuna ayarlanır anlamına gelir. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> geriye doğru olduğundan ve görüntünün boyutu denetimin boyutuna ayarlanır anlamına gelir.  
  
     Aşağıdaki örnekte, görüntüsünün konumunu ayarlayın Belgelerim klasörünü yoludur. Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu dizin içerdiğini varsayar çünkü bu, gerçekleştirilir. Bu, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeylerine sahip kullanıcılar da sağlar. Aşağıdaki örnekte bir form varsayar bir <xref:System.Windows.Forms.PictureBox> denetim zaten eklendi.  
  
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
- [Nasıl yapılır: Tasarımcıyı kullanarak resim yükleme](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [PictureBox Denetimine Genel Bakış](picturebox-control-overview-windows-forms.md)
- [Nasıl yapılır: Çalışma zamanında resimleri ayarlama](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox Denetimi](picturebox-control-windows-forms.md)
