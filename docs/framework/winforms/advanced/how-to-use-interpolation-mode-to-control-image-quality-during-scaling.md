---
title: 'Nasıl yapılır: Ölçeklendirme sırasında görüntü kalitesini denetlemek için ilişkilendirme modunu kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: 93430f521904d9d38ba98f4055480583fd650114
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410374"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a>Nasıl yapılır: Ölçeklendirme sırasında görüntü kalitesini denetlemek için ilişkilendirme modunu kullanma
İlişkilendirme modu bir <xref:System.Drawing.Graphics> nesnenin şeklini etkiler [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ölçeklendirir (uzatır ve küçülür) görüntüler. <xref:System.Drawing.Drawing2D.InterpolationMode> Sabit listesi tanımlar birkaç ilişkilendirme modu, bazıları aşağıda gösterilmiştir:  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 Görüntü esnetme için her piksel Orijinal görüntüdeki piksel cinsinden daha büyük resmi grubuna eşlenmelidir. Görüntü daraltmak için grupları piksel Orijinal görüntüdeki tek piksel cinsinden daha küçük resmi eşlenmesi gerekir. Bu eşlemeler gerçekleştiren algoritmalar verimliliğini ölçeklendirilmiş bir görüntü kalitesini belirler. Daha fazla işleme süresi gerektirecek şekilde ölçeklenen daha kaliteli görüntüler oluşturan algoritmaları eğilimindedir. Yukarıdaki listede <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> düşük kaliteli modudur ve <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> yüksek kaliteli modudur.  
  
 İlişkilendirme modu ayarlamak için üyeleri birini atamanız <xref:System.Drawing.Drawing2D.InterpolationMode> sabit listesine <xref:System.Drawing.Graphics.InterpolationMode%2A> özelliği bir <xref:System.Drawing.Graphics> nesne.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir resim çizer ve sonra üç farklı ilişkilendirme modu görüntüsüyle küçültür.  
  
 Aşağıdaki çizimde, orijinal görüntünün ve üç küçük resimleri gösterir.  
  
 ![Çeşitli ilişkilendirme ayarlarını içeren bir görüntü gösteren ekran görüntüsü.](./media/how-to-use-interpolation-mode-to-control-image-quality-during-scaling/varied-interpolation-settings.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
