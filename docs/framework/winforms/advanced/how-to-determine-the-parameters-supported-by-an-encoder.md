---
title: "Nasıl yapılır: Bir Kodlayıcı Tarafından Desteklenen Parametreleri Belirleme"
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
helpviewer_keywords: encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e041434e9ace24618dbdc45341a0e8468721c3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Nasıl yapılır: yüklenen Kodlayıcıları listeleme](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [Bit eşlem türleri](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 [Yönetilen GDI +'GÖRÜNTÜ Kodlayıcıları ve kod çözücüleri kullanma](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
