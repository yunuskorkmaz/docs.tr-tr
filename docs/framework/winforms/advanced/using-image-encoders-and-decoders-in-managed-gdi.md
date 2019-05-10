---
title: Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: e56bc20eb55d694d19b25d9e94e5c9d9e3952628
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666442"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma
<xref:System.Drawing> Ad alanı sağlar <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> depolamak ve bu görüntüleri düzenleme için sınıflar. İçindeki görüntü Kodlayıcıları kullanarak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], görüntüleri bellekten diske yazabilirsiniz. Görüntü kod çözücüleri kullanarak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], görüntüleri diskten belleğe yükleyebilirsiniz. Verileri bir kodlayıcı çeviren bir <xref:System.Drawing.Image> veya <xref:System.Drawing.Bitmap> ayrılan disk dosya formatına nesne. Bir kod çözücü tarafından gerekli biçime bir disk dosyasındaki verilerin çevirir <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> nesneleri.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Yerleşik Kodlayıcıları ve aşağıdaki dosya türlerini destekleyen kod çözücüleri sahiptir:  
  
- BMP  
  
- GIF  
  
- JPEG  
  
- PNG  
  
- TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Ayrıca, aşağıdaki dosya türlerini destekleyen yerleşik kod çözücüleri vardır:  
  
- WMF  
  
- EMF  
  
- SİMGESİ  
  
 Aşağıdaki konular Kodlayıcıları ve kod çözücüleri daha ayrıntılı açıklanmaktadır:  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Yüklenen Kodlayıcıları listeleme](how-to-list-installed-encoders.md)  
 Bir bilgisayar üzerinde sunulan kodlayıcılarda listesinde açıklar.  
  
 [Nasıl yapılır: Yüklenen kod çözücüleri listeleme](how-to-list-installed-decoders.md)  
 Bir bilgisayarda kullanılabilir kod çözücüleri listeleme açıklar.  
  
 [Nasıl yapılır: Bir kodlayıcı tarafından desteklenen parametreleri belirleme](how-to-determine-the-parameters-supported-by-an-encoder.md)  
 Liste açıklar <xref:System.Drawing.Imaging.EncoderParameters> bir kodlayıcı tarafından desteklenen.  
  
 [Nasıl yapılır: BMP resmini PNG resmine dönüştürme](how-to-convert-a-bmp-image-to-a-png-image.md)  
 Farklı görüntü biçimi'nde bir görüntüsünü kaydetmek açıklar.  
  
 [Nasıl yapılır: JPEG sıkıştırma düzeyini ayarlama](how-to-set-jpeg-compression-level.md)  
 Görüntü kalite düzeyini değiştirmek açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [GDI+ Yönetilen Kodu Hakkında](about-gdi-managed-code.md)  
  
 [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
