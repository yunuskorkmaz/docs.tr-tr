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
ms.workload: dotnet
ms.openlocfilehash: 2ee2669c41f4ee558d9457cee7df0ae8425cf065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 [Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 [Bit Eşlem Türleri](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
