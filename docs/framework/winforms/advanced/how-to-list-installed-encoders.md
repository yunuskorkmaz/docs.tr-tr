---
title: "Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme"
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
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70f913acb2620b5c01e1aec1f1eb98b041b82a59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-installed-encoders"></a>Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme
Uygulamanızı bir belirli görüntü dosyası biçimi kaydedin olup olmadığını belirlemek için görüntü Kodlayıcıları bir bilgisayarda kullanılabilir listelemek istediğiniz. <xref:System.Drawing.Imaging.ImageCodecInfo> SAX <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> statik yöntemler hangi görüntü Kodlayıcıları kullanılabilir belirleyebilmesi. <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A>bir dizi döndürür <xref:System.Drawing.Imaging.ImageCodecInfo> nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde yüklü kodlayıcılar listesi ve özellik değerlerine çıkarır.  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir Windows Forms uygulaması.  
  
-   A <xref:System.Windows.Forms.PaintEventArgs>, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: yüklenen kod çözücüleri listeleme](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 [Yönetilen GDI +'GÖRÜNTÜ Kodlayıcıları ve kod çözücüleri kullanma](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
