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
ms.openlocfilehash: fea813d7b9fe585e35b729b8b64e3a5f414ef76d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141972"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme (Windows Forms)
Bir formüzerinde Windows <xref:System.Windows.Forms.PictureBox> Forms denetimini kullanırsanız, bu formdaki <xref:System.Windows.Forms.PictureBox.SizeMode%2A> özelliği şu şekilde ayarlayabilirsiniz:  
  
- Resmin sol üst köşesini kontrolün sol üst köşesiyle hizala  
  
- Resmi denetim içinde ortala  
  
- Denetimin boyutunu görüntülenebilmek için ayarlama  
  
- Görüntülenedeki herhangi bir resmi denetime uyacak şekilde esnetin  
  
 Bir resmi germe (özellikle bitmap biçiminde) görüntü kalitesinde bir kayıp yaratabilir. Çalışma zamanında resim çizmek için grafik yönergeleri listeleri olan metafiles, bit eşlemler daha germe için daha uygundur.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>SizeMode özelliğini çalışma zamanında ayarlamak için  
  
1. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (varsayılan), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> <xref:System.Windows.Forms.PictureBox.SizeMode%2A> , , <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>veya <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal>görüntünün kontrolün sol üst köşesine yerleştirildiği anlamına gelir; görüntü denetimden daha büyükse, alt ve sağ kenarları kırpılır. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>görüntünün denetim içinde ortalanmış olduğu anlamına gelir; görüntü denetimden daha büyükse, resmin dış kenarları kırpılır. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>denetimboyutunu görüntünün boyutuna ayarlanır anlamına gelir. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>tersidir ve görüntünün boyutunun denetimboyutuna ayarlanması anlamına gelir.  
  
     Aşağıdaki örnekte, görüntünün konumu için ayarlanan yol Belgelerim klasörüdür. Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içereceğini varsayabileceğinizden, bu işlem yapılır. Bu aynı zamanda en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenli bir şekilde çalıştırmasına olanak tanır. Aşağıdaki <xref:System.Windows.Forms.PictureBox> örnekte, denetimzaten eklenmiştir.  
  
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
