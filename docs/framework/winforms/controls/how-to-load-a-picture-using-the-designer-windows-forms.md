---
title: 'Nasıl yapılır: (Windows Forms) tasarımcıyı kullanarak resim yükleme'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 6bdf7c3df0ffd97dd88a4c442a8a73593a0447ee
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336388"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Nasıl yapılır: (Windows Forms) tasarımcıyı kullanarak resim yükleme
Windows Forms ile <xref:System.Windows.Forms.PictureBox> denetimi, yüklemek ve bir resim, ayarlayarak tasarım zamanında bir formda görüntülemek <xref:System.Windows.Forms.PictureBox.Image%2A> geçerli bir resim özelliği. Aşağıdaki tabloda, kabul edilebilir dosya türleri gösterilmektedir.  
  
|Tür|Dosya adı uzantısı|  
|----------|-------------------------|  
|Bit eşlem|.bmp|  
|Simge|.ico|  
|GIF|.gif|  
|Meta dosyası|.wmf|  
|JPEG|.jpg|  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-display-a-picture-at-design-time"></a>Tasarım zamanında bir resim görüntülemek için  
  
1. Çizim bir <xref:System.Windows.Forms.PictureBox> form denetimi.  
  
2. Özellikler penceresinde seçin <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği, sonra üç nokta düğmesini görüntülemek için tıklatın **açık** iletişim kutusu.  
  
3. Belirli bir dosya türü için (örneğin, .gif dosyaları) arıyorsanız, onu seçip **dosya türü** kutusu.  
  
4. Görüntülemek istediğiniz dosyayı seçin.  
  
### <a name="to-clear-the-picture-at-design-time"></a>Tasarım zamanında resmi temizlemek için  
  
1. Üzerinde **özellikleri** penceresinde <xref:System.Windows.Forms.PictureBox.Image%2A> özelliği ve sağ görüntü nesnesinin adını solunda görünür küçük resmine tıklayın. Seçin **sıfırlama**.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox Denetimine Genel Bakış](picturebox-control-overview-windows-forms.md)
- [Nasıl yapılır: Çalışma Zamanında Resmin Boyutunu veya Konumunu Değiştirme](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Nasıl yapılır: Çalışma Zamanında Resimleri Ayarlama](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox Denetimi](picturebox-control-windows-forms.md)
