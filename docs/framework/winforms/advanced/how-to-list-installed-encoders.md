---
title: 'Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
ms.openlocfilehash: ce297cb6d183bc63c8b276e30100aa4e864cd90d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078817"
---
# <a name="how-to-list-installed-encoders"></a>Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme
Uygulamanız için bir özel görüntü dosya biçimi tasarrufu yapıp yapamayacağınızı belirleyebilirsiniz için görüntü Kodlayıcıları bir bilgisayarda kullanılabilir listesinde isteyebilirsiniz. <xref:System.Drawing.Imaging.ImageCodecInfo> Sağlar sınıfını <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> statik yöntemler hangi görüntü Kodlayıcıları kullanılabilir belirleyebilirsiniz. <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> bir dizi döndürür <xref:System.Drawing.Imaging.ImageCodecInfo> nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, yüklenen Kodlayıcıları listesi ve özellik değerlerine çıkarır.  
  
 [!code-csharp[UsingImageEncodersDecoders#1](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir Windows Forms uygulaması.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Yüklenen kod çözücüleri listeleme](how-to-list-installed-decoders.md)
- [Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma](using-image-encoders-and-decoders-in-managed-gdi.md)
