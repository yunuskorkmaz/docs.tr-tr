---
title: 'Nasıl yapılır: Bir kodlayıcı tarafından desteklenen parametreleri belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: f5af00833c8d8373444b475673709d902598d9d0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719708"
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a>Nasıl yapılır: Bir kodlayıcı tarafından desteklenen parametreleri belirleme
Kalite ve sıkıştırma düzeyi gibi görüntü parametreleri ayarlayabilirsiniz ancak belirtilen görüntü Kodlayıcı tarafından desteklenen parametreleri bilmeniz gerekir. <xref:System.Drawing.Image> Sağlar sınıfını <xref:System.Drawing.Image.GetEncoderParameterList%2A> yöntemi görüntü parametreleri için belirli bir kodlayıcı desteklenen belirleyebilirsiniz. Size encoder bir GUID ile belirtin. <xref:System.Drawing.Image.GetEncoderParameterList%2A> Yöntemi, bir dizi döndürür <xref:System.Drawing.Imaging.EncoderParameter> nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, JPEG Kodlayıcı için desteklenen parametreler çıkarır. Parametre kategorileri ve ilişkili GUID'lerinin listesini kullanın <xref:System.Drawing.Imaging.Encoder> her parametre için bir kategori belirlemek için sınıfına genel bakış.  
  
 [!code-csharp[UsingImageEncodersDecoders#3](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir Windows Forms uygulaması.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Yüklenen Kodlayıcıları listeleme](how-to-list-installed-encoders.md)
- [Bit Eşlem Türleri](types-of-bitmaps.md)
- [Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma](using-image-encoders-and-decoders-in-managed-gdi.md)
