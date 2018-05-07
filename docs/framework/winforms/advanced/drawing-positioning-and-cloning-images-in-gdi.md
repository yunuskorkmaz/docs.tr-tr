---
title: GDI+'da Görüntü Çizme, Konumlandırma ve Kopyalama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
ms.openlocfilehash: 5ff502884874e21e8f34acb2f15db4c651a0a273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>GDI+'da Görüntü Çizme, Konumlandırma ve Kopyalama
Kullanabileceğiniz <xref:System.Drawing.Bitmap> sınıfı yüklemek ve ızgara görüntüleri ve görüntülemek için kullanabileceğiniz <xref:System.Drawing.Imaging.Metafile> yüklemek ve vektör görüntüleri göstermek için sınıf. <xref:System.Drawing.Bitmap> Ve <xref:System.Drawing.Imaging.Metafile> sınıfları <xref:System.Drawing.Image> sınıfı. Vektör resim görüntülemek için örneği gerekir <xref:System.Drawing.Graphics> sınıfı ve bir <xref:System.Drawing.Imaging.Metafile>. Izgara resim görüntülemek için örneği gerekir <xref:System.Drawing.Graphics> sınıfı ve bir <xref:System.Drawing.Bitmap>. Örneğinin <xref:System.Drawing.Graphics> SAX <xref:System.Drawing.Graphics.DrawImage%2A> alır yöntemi <xref:System.Drawing.Imaging.Metafile> veya <xref:System.Drawing.Bitmap> bağımsız değişken olarak.  
  
## <a name="file-types-and-cloning"></a>Dosya türleri ve kopyalama  
 Aşağıdaki kod örneğinde nasıl oluşturulacağını gösteren bir <xref:System.Drawing.Bitmap> Climber.jpg dosyasından ve bit eşlem görüntüler. Görüntüyü, sol üst köşe için hedef noktasını (10, 10), ikinci ve üçüncü parametre belirtildi.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 Aşağıdaki çizimde, görüntüyü gösterir.  
  
 ![Görüntü örnek](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 Oluşturabileceğiniz <xref:System.Drawing.Bitmap> nesneleri grafik çeşitli dosya biçimleri: BMP, GIF, JPEG, EXIF, PNG, TIFF ve SİMGE.  
  
 Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir <xref:System.Drawing.Bitmap> nesneleri çeşitli dosya türleri ve bit eşlemler görüntüler.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <xref:System.Drawing.Bitmap> SAX bir <xref:System.Drawing.Bitmap.Clone%2A> varolan bir kopyasını oluşturmak için kullanabileceğiniz yöntemi <xref:System.Drawing.Bitmap>. <xref:System.Drawing.Bitmap.Clone%2A> Yöntemi kopyalamak istediğiniz özgün bit eşlem kısmı belirtmek için kullanabileceğiniz bir kaynak dikdörtgen parametresine sahip. Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir bir <xref:System.Drawing.Bitmap> varolan üst yarısındaki kopyalayarak <xref:System.Drawing.Bitmap>. Ardından her iki görüntüsü çizilir.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 Aşağıdaki çizimde iki görüntü gösterir.  
  
 ![Kırpma](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
