---
title: 'Nasıl yapılır: Ölçeklendirme Sırasında Görüntü Kalitesini Denetlemek için İlişkilendirme Modunu Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: 72a9cb3a19f0d449dcb376a65f1734b79ed61ab9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a>Nasıl yapılır: Ölçeklendirme Sırasında Görüntü Kalitesini Denetlemek için İlişkilendirme Modunu Kullanma
İlişkilendirme modunu bir <xref:System.Drawing.Graphics> nesne şeklini etkiler [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ölçekler (uzatır ve küçültür) görüntüler. <xref:System.Drawing.Drawing2D.InterpolationMode> Numaralandırma aşağıdaki listede gösterildiği bazıları birkaç ilişkilendirme modu tanımlar:  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 Bir görüntü uzatmak için Orijinal görüntüdeki her piksel piksel cinsinden büyük görüntü grubuna eşlenmesi gerekir. Görüntüyü daraltmak için Orijinal görüntüdeki piksel grupları tek piksel cinsinden daha küçük resim eşlenmesi gerekir. Bu eşlemeler gerçekleştirmek algoritmaları verimliliğini ölçeklendirilmiş bir görüntü kalitesini belirler. Daha fazla işleme süresi gerektirecek şekilde daha yüksek kaliteli ölçeklenen görüntüler oluşturmak algoritmaları eğilimlidir. Yukarıdaki listede <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> düşük kaliteli modudur ve <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> yüksek kaliteli modudur.  
  
 İlişkilendirme modu ayarlamak için üyelerinden birinde atamak <xref:System.Drawing.Drawing2D.InterpolationMode> numaralandırma <xref:System.Drawing.Graphics.InterpolationMode%2A> özelliği bir <xref:System.Drawing.Graphics> nesnesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir resim çizer ve üç farklı ilişkilendirme modu görüntüsüyle küçültür.  
  
 Aşağıdaki çizimde özgün resim ve üç küçük resimleri gösterir.  
  
 ![Çeşitli ilişkilendirme ayarlarını görüntüsüyle](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
