---
title: "Nasıl yapılır: BMP Resmini PNG Resmine Dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 542dd132ece543b6a53a9e6d867b49fce4d15a58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a>Nasıl yapılır: BMP Resmini PNG Resmine Dönüştürme
Görmemeleri, bir görüntü dosyası biçimden diğerine dönüştürmeyi isteyeceksiniz. Çağırarak bu dönüştürme kolayca yapabilirsiniz <xref:System.Drawing.Image.Save%2A> yöntemi <xref:System.Drawing.Image> sınıfı ve belirterek <xref:System.Drawing.Imaging.ImageFormat> istenen görüntü dosyası biçimi için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir türden BMP resmini yükler ve görüntü PNG biçiminde kaydeder.  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir Windows Forms uygulaması.  
  
-   Bir başvuru `System.Drawing.Imaging` ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: yüklenen Kodlayıcıları listeleme](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [Yönetilen GDI +'GÖRÜNTÜ Kodlayıcıları ve kod çözücüleri kullanma](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 [Bit eşlem türleri](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
