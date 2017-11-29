---
title: "Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64384e3c283b6596e36d5b2bd583a304faf080b4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma
<xref:System.Drawing> Ad alanı sağlar <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> depolamak ve görüntüleri düzenleme için sınıflar. Görüntü Kodlayıcıları kullanarak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], görüntüleri bellekten diske yazabilirsiniz. Görüntü kod çözücüleri kullanarak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], görüntüleri diskten belleğe yükleyebilir. Verileri bir kodlayıcı çeviren bir <xref:System.Drawing.Image> veya <xref:System.Drawing.Bitmap> ayrılan disk dosya biçimine nesnesi. Bir disk dosyası gerekli biçime verilerde bir kod çözücü çevirir <xref:System.Drawing.Image> ve <xref:System.Drawing.Bitmap> nesneleri.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Yerleşik Kodlayıcıları ve aşağıdaki dosya türlerini destekleyen kod çözücüleri sahiptir:  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Ayrıca, aşağıdaki dosya türlerini destekleyen yerleşik kod çözücüleri vardır:  
  
-   WMF  
  
-   EMF  
  
-   SİMGESİ  
  
 Aşağıdaki konular Kodlayıcıları ve kod çözücüleri daha ayrıntılı ele alınmıştır:  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: yüklenen Kodlayıcıları listeleme](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 Bir bilgisayarda kullanılabilir kodlayıcılar listelemek açıklar.  
  
 [Nasıl yapılır: yüklenen kod çözücüleri listeleme](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 Bir bilgisayarda kullanılabilir kod çözücüleri listelemek açıklar.  
  
 [Nasıl yapılır: bir kodlayıcı tarafından desteklenen parametreleri belirleme](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 Liste açıklar <xref:System.Drawing.Imaging.EncoderParameters> bir kodlayıcı tarafından desteklenir.  
  
 [Nasıl yapılır: BMP resmini PNG resmine dönüştürme](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 Farklı bir resim biçiminde bir görüntüsünü kaydetmek açıklar.  
  
 [Nasıl yapılır: JPEG sıkıştırma düzeyini ayarlama](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 Bir görüntü kalite düzeyini değiştirmek açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [GDI + yönetilen kodu hakkında](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [Resimler, bit eşlemler ve meta dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
