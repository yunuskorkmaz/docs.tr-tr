---
title: "Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme (Windows Forms)"
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
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df67871b0b133297a6f53ff9e4a42c7630a5f56d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme (Windows Forms)
Windows Forms kullanırsanız <xref:System.Windows.Forms.PictureBox> denetim bir form üzerinde ayarladığınız <xref:System.Windows.Forms.PictureBox.SizeMode%2A> özelliği için:  
  
-   Resmin sol üst köşedeki denetimin sol üst köşedeki ile hizalayın  
  
-   Merkezi Denetim içindeki resmi  
  
-   Görüntülediği resim uymak için denetimi boyutunu ayarlama  
  
-   Denetim uyacak şekilde görüntüler herhangi bir resmi uzatma  
  
 Bir resmi (özellikle bir bit eşlem biçimi) uzatma görüntü kalitesini kaybına üretebilir. Çalışma zamanında resimleri çizim için grafik yönergeleri listeleridir, meta dosyaları, bit eşlemler daha uzatma için daha uygundur.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Çalışma zamanında SizeMode özelliğini ayarlamak için  
  
1.  Ayarlama <xref:System.Windows.Forms.PictureBox.SizeMode%2A> için <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (varsayılan), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, veya <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal>Görüntü denetimin sol üst köşede yerleştirilir anlamına gelir; Görüntü Denetim daha büyükse, alt ve sağ kenarları kırpılır. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>görüntü denetim içinde ortalanır anlamına gelir; Görüntü Denetim daha büyükse resmin dış kenarları kırpılır. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>Denetimin boyutunu görüntü boyutuna ayarlanır anlamına gelir. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>geriye doğru olduğundan ve görüntünün boyutuna denetimi boyutuna ayarlanır anlamına gelir.  
  
     Aşağıdaki örnekte görüntüsünün konumunu ayarlayın Belgelerim klasörünü yoludur. Windows işletim sistemi çalıştıran bilgisayarların çoğu bu dizin içerdiğini varsayar çünkü bu, gerçekleştirilir. Bu, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri olan kullanıcılar da sağlar. Aşağıdaki örnek bir formla varsayar bir <xref:System.Windows.Forms.PictureBox> denetimi zaten eklendi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.PictureBox>  
 [Nasıl yapılır: tasarımcıyı kullanarak resim yükleme](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [PictureBox denetimine genel bakış](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [Nasıl yapılır: çalışma zamanında resimleri ayarlama](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [PictureBox denetimi](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
