---
title: "Nasıl yapılır: Görüntü Kırpma ve Ölçeklendirme"
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
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8fb5d527cd1047197f370c4a9a9b1f8f33461653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-crop-and-scale-images"></a>Nasıl yapılır: Görüntü Kırpma ve Ölçeklendirme
<xref:System.Drawing.Graphics> Sınıfı sağlar birkaç <xref:System.Drawing.Graphics.DrawImage%2A> yöntemleri, bazıları sahip kırpma ve ölçeklendirme görüntülere kullanabileceğiniz kaynak ve hedef dikdörtgen parametreler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> disk dosyasından Apple.gif nesnesi. Kod özgün boyutunda tüm apple resim çizer. Kod sonra çağırır <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> özgün apple görüntüden büyüktür hedef dikdörtgene apple görüntüsü bir kısmı çizmek için nesne.  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> Yöntemi beşinci ve altıncı bağımsız değişkenler üçüncü tarafından dördüncü, belirtilen kaynak dikdörtgene bakarak çizmek için apple hangi kısmının belirler. Bu durumda, apple eni yüzde 75'ini ve yüksekliğinin yüzde 75'ini kırpılır.  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> Yöntemi kırpılmış apple çizmek nerede ve nasıl büyük hedef dikdörtgene bakarak kırpılmış apple yapmak için hangi belirler ikinci bağımsız değişkeni tarafından belirtilen. Bu durumda hedef dikdörtgen yüzde 30 daha geniş ve yüzde 30'u orijinal görüntüden daha uzun olur.  
  
 Aşağıdaki çizimde, apple kırpılmış özgün apple ve ölçeklendirilmiş, gösterir.  
  
 ![Kırpma ve ölçeklendirme](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Değiştirdiğinizden emin olun `Apple.gif` bir görüntü dosyası adı ve, sisteminizde geçerli yolu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Resimler, bit eşlemler ve meta dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Resimler, bit eşlemler, simgeler ve meta dosyaları ile çalışma](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
