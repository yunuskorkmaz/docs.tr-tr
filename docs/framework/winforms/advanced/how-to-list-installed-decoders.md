---
title: 'Nasıl yapılır: Yüklenen Kod Çözücüleri Listeleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
ms.openlocfilehash: c92b8010def2f77f859ee0bd9cdb1ed51dd15f27
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079423"
---
# <a name="how-to-list-installed-decoders"></a>Nasıl yapılır: Yüklenen Kod Çözücüleri Listeleme
Uygulamanızın belirli resim dosyası biçimi erişip erişemeyeceğini belirlemek için görüntü kod çözücüleri bir bilgisayarda kullanılabilir listesinde isteyebilirsiniz. <xref:System.Drawing.Imaging.ImageCodecInfo> Sağlar sınıfını <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> statik yöntemler hangi görüntü kod çözücüleri kullanılabilir belirleyebilirsiniz. <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> Bir dizi döndürür <xref:System.Drawing.Imaging.ImageCodecInfo> nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, yüklenen kod çözücüleri listesi ve özellik değerlerine çıkarır.  
  
 [!code-csharp[UsingImageEncodersDecoders#2](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir Windows Forms uygulaması.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme](how-to-list-installed-encoders.md)
- [Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma](using-image-encoders-and-decoders-in-managed-gdi.md)
