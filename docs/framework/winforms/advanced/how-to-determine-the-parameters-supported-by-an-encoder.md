---
title: 'Nasıl yapılır: Bir Kodlayıcı Tarafından Desteklenen Parametreleri Belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: 7f7c270c4ae590c070103d51f116158869b678c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521985"
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a>Nasıl yapılır: Bir Kodlayıcı Tarafından Desteklenen Parametreleri Belirleme
Kalite ve sıkıştırma düzeyi gibi görüntü parametreleri değiştirebilirsiniz ancak hangi parametreleri verilen görüntü Kodlayıcı tarafından desteklenen bilmeniz gerekir. <xref:System.Drawing.Image> SAX <xref:System.Drawing.Image.GetEncoderParameterList%2A> yöntemi hangi görüntü parametreleri için belirli bir kodlayıcı desteklenen belirleyebilmesi. Kodlayıcı ile bir GUID belirtin. <xref:System.Drawing.Image.GetEncoderParameterList%2A> Yöntemi bir dizi döndürür <xref:System.Drawing.Imaging.EncoderParameter> nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, JPEG Kodlayıcı için desteklenen parametreler çıkarır. Parametre kategorileri ve ilişkili GUID içinde listesini kullanın <xref:System.Drawing.Imaging.Encoder> her parametre için kategori belirlemek için sınıf genel bakış.  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir Windows Forms uygulaması.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [Bit Eşlem Türleri](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 [Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
