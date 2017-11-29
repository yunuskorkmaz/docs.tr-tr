---
title: "Nasıl yapılır: Meta Dosyalarını Yükleme ve Görüntüleme"
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
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 722b6d36801c69e500535a32e952ef8f45634d03
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-load-and-display-metafiles"></a>Nasıl yapılır: Meta Dosyalarını Yükleme ve Görüntüleme
<xref:System.Drawing.Imaging.Metafile> Devraldığı sınıfı <xref:System.Drawing.Image> sınıfı, kaydetme, görüntüleme ve vektör görüntüleri inceleyerek için yöntemleri sağlar.  
  
## <a name="example"></a>Örnek  
 Ekranda bir vektör görüntüsü (meta dosyası) görüntülemek için gereken bir <xref:System.Drawing.Imaging.Metafile> nesne ve <xref:System.Drawing.Graphics> nesne. Bir dosya (veya bir akış) adını geçişi için bir <xref:System.Drawing.Imaging.Metafile> Oluşturucusu. Oluşturduktan sonra bir <xref:System.Drawing.Imaging.Metafile> nesne, bu geçirmek <xref:System.Drawing.Imaging.Metafile> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi.  
  
 Örnekte bir <xref:System.Drawing.Imaging.Metafile> EMF (Gelişmiş Meta dosyası) dosyasından nesnesi ve ardından, sol üst köşede ile resim çizer (60, 10).  
  
 Aşağıda belirtilen konumda çizilmiş meta dosyası gösterilmektedir.  
  
 ![Görüntü konumu](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Resimler, bit eşlemler, simgeler ve meta dosyaları ile çalışma](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
