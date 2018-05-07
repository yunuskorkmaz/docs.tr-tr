---
title: Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: b2e51587209cb4df41ea1fd18ce5c2088ee07a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma
<xref:System.Drawing> Ad alanı sağlar <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> depolamak ve görüntüleri düzenleme için sınıflar. Görüntü Kodlayıcıları kullanarak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], görüntüleri bellekten diske yazabilirsiniz. Görüntü kod çözücüleri kullanarak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], görüntüleri diskten belleğe yükleyebilir. Verileri bir kodlayıcı çeviren bir <xref:System.Drawing.Image> veya <xref:System.Drawing.Bitmap> ayrılan disk dosya biçimine nesnesi. Bir disk dosyası gerekli biçime verilerde bir kod çözücü çevirir <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> nesneleri.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Yerleşik Kodlayıcıları ve aşağıdaki dosya türlerini destekleyen kod çözücüleri sahiptir:  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Ayrıca, aşağıdaki dosya türlerini destekleyen yerleşik kod çözücüleri vardır:  
  
-   WMF  
  
-   EMF  
  
-   SİMGESİ  
  
 Aşağıdaki konular Kodlayıcıları ve kod çözücüleri daha ayrıntılı ele alınmıştır:  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 Bir bilgisayarda kullanılabilir kodlayıcılar listelemek açıklar.  
  
 [Nasıl yapılır: Yüklenen Kod Çözücüleri Listeleme](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 Bir bilgisayarda kullanılabilir kod çözücüleri listelemek açıklar.  
  
 [Nasıl yapılır: Bir Kodlayıcı Tarafından Desteklenen Parametreleri Belirleme](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 Liste açıklar <xref:System.Drawing.Imaging.EncoderParameters> bir kodlayıcı tarafından desteklenir.  
  
 [Nasıl yapılır: BMP Resmini PNG Resmine Dönüştürme](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 Farklı bir resim biçiminde bir görüntüsünü kaydetmek açıklar.  
  
 [Nasıl Yapılır: JPEG Sıkıştırma Düzeyini Ayarlama](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 Bir görüntü kalite düzeyini değiştirmek açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [GDI+ Yönetilen Kodu Hakkında](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
