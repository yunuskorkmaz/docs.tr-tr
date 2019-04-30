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
ms.openlocfilehash: b5f98e7bdef9ff8ed0a4cd0e040cb92a31f30503
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756929"
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>GDI+'da Görüntü Çizme, Konumlandırma ve Kopyalama
Kullanabileceğiniz <xref:System.Drawing.Bitmap> sınıfı yüklemek ve ızgara görüntüleri ve görüntülemek için kullanabileceğiniz <xref:System.Drawing.Imaging.Metafile> yüklemek ve vektör görüntüleri görüntülemek için sınıf. <xref:System.Drawing.Bitmap> Ve <xref:System.Drawing.Imaging.Metafile> sınıfları <xref:System.Drawing.Image> sınıfı. Bir vektör resim görüntülemek için örneği gerekir. <xref:System.Drawing.Graphics> sınıfı ve <xref:System.Drawing.Imaging.Metafile>. Izgara resim görüntülemek için örneği gerekir. <xref:System.Drawing.Graphics> sınıfı ve <xref:System.Drawing.Bitmap>. Örneğini <xref:System.Drawing.Graphics> sağlar sınıfını <xref:System.Drawing.Graphics.DrawImage%2A> alan yöntemi <xref:System.Drawing.Imaging.Metafile> veya <xref:System.Drawing.Bitmap> bağımsız değişken olarak.  
  
## <a name="file-types-and-cloning"></a>Dosya türleri ve kopyalama  
 Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:System.Drawing.Bitmap> Climber.jpg dosyasından ve bit eşlem görüntüler. Sol üst görüntünün hedef noktasının (10, 10), ikinci ve üçüncü parametre belirtilir.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 Aşağıdaki çizimde, görüntüyü gösterir.  
  
 ![Görüntü örnek](./media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 Oluşturulabilir <xref:System.Drawing.Bitmap> nesneleri grafik çeşitli dosya biçimleri: BMP, GIF, JPEG, EXIF, PNG, TIFF ve SİMGE.  
  
 Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir <xref:System.Drawing.Bitmap> nesneleri çeşitli dosya türlerinin ve bit eşlemler görüntüler.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <xref:System.Drawing.Bitmap> Sağlar sınıfını bir <xref:System.Drawing.Bitmap.Clone%2A> varolan bir kopyasını oluşturmak için kullanabileceğiniz yöntem <xref:System.Drawing.Bitmap>. <xref:System.Drawing.Bitmap.Clone%2A> Yöntemi kopyalamak istediğiniz özgün bit eşlem bölümünü belirlemek için kullanabileceğiniz bir kaynak dikdörtgenin parametresi vardır. Aşağıdaki kod örneğinde nasıl oluşturulacağını gösterir. bir <xref:System.Drawing.Bitmap> varolan üst kısmında kopyalayarak <xref:System.Drawing.Bitmap>. Ardından, her iki çizilir.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 Aşağıdaki çizimde, iki görüntü gösterir.  
  
 ![Kırpma](./media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Nasıl yapılır: Çizim için grafik nesneleri oluşturma](how-to-create-graphics-objects-for-drawing.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
