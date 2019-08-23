---
title: GDI+'da Fırçalar ve Dolgulu Şekiller
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 45ef0b5920e43300e047d363149ea10a7833477b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912226"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>GDI+'da Fırçalar ve Dolgulu Şekiller
Dikdörtgen veya elips gibi kapalı bir şekil, bir ana hat ve iç öğesinden oluşur. Ana hat bir kalemle çizilir ve iç kısım fırçayla doldurulur. GDI+ kapalı şekillerin,,, ve özelliklerini doldurmak için çeşitli fırça sınıfları sağlar: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush> <xref:System.Drawing.Drawing2D.LinearGradientBrush>, ve <xref:System.Drawing.Drawing2D.PathGradientBrush>. Bu sınıfların hepsi <xref:System.Drawing.Brush> sınıfından devralınır. Aşağıdaki çizimde, düz fırçayla doldurulmuş bir dikdörtgen ve bir tarama fırçası ile doldurulmuş bir elips gösterilmektedir.  
  
 ![Doldurulmuş şekiller](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>Düz fırçalar  
 Kapalı bir şekli doldurmanız için, <xref:System.Drawing.Graphics> sınıfının ve bir <xref:System.Drawing.Brush>örneğinin olması gerekir. <xref:System.Drawing.Graphics> Sınıfının örneği, <xref:System.Drawing.Graphics.FillRectangle%2A> ve <xref:System.Drawing.Graphics.FillEllipse%2A> gibiyöntemlersağlarveörneğinColorvemodelgibi<xref:System.Drawing.Brush> dolgunun özniteliklerini depolar. , <xref:System.Drawing.Brush> Fill metoduna bağımsız değişkenlerden biri olarak geçirilir. Aşağıdaki kod örneği, bir elipsin düz kırmızı renkle nasıl doldurulacağını gösterir.  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
> Yukarıdaki örnekte, fırça, ' den <xref:System.Drawing.SolidBrush> <xref:System.Drawing.Brush>devralan türüdür.  
  
## <a name="hatch-brushes"></a>Tarama fırçaları  
 Bir şekli tarama fırçası ile doldururken bir ön plan rengi, arka plan rengi ve tarama stili belirtirsiniz. Ön plan rengi, tarama renggidir.  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 GDI+ 50 'den fazla tarama stili sağlar; Aşağıdaki çizimde gösterilen üç stil, <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal> <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>ve <xref:System.Drawing.Drawing2D.HatchStyle.Cross>' dir.  
  
 ![Doldurulmuş şekiller](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>Doku fırçaları  
 Bir doku fırçası ile bir şekli bit eşlemde depolanan bir desenli doldurabilirsiniz. Örneğin, aşağıdaki resmin adlı `MyTexture.bmp`bir disk dosyasında depolandığını varsayalım.  
  
 ![Doldurulmuş şekil](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 Aşağıdaki kod örneği, içinde `MyTexture.bmp`depolanan resmi tekrarlayarak nasıl bir elips doldurulacağını gösterir.  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 Aşağıdaki çizimde doldurulmuş elips gösterilmektedir.  
  
 ![Doldurulmuş şekil](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>Gradyan fırçaları  
 GDI+ iki tür gradyan fırça sağlar: doğrusal ve yol. Doğrusal bir gradyan fırçası kullanarak şekli yatay, dikey veya çapraz bir şekilde hareket ettirmek için kademeli olarak değişen renkle doldurabilirsiniz. Aşağıdaki kod örneği, elips sol kenarından sağ kenara hareket ettirmek için mavi ile yeşil arasında değişen bir elipsi yatay bir gradyan fırçayla nasıl dolduracağı gösterilmektedir.  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 Aşağıdaki çizimde doldurulmuş elips gösterilmektedir.  
  
 ![Doldurulmuş şekil](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 Bir yol gradyan fırçası, bir şeklin merkezinden kenara doğru hareket eden rengi değiştirecek şekilde yapılandırılabilir.  
  
 ![Doldurulmuş şekil](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 Yol gradyan fırçaları oldukça esnektir. Aşağıdaki çizimde yer değiştiren üçgeni doldurmaları için kullanılan gradyan fırçası, köşelerin her üç farklı rengin her biri için ortadaki kırmızı 'dan kırmızıya değişir.  
  
 ![Doldurulmuş şekil](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Nasıl yapılır: Bir Windows formunda doldurulmuş dikdörtgen çizme](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [Nasıl yapılır: Bir Windows formunda doldurulmuş Elips çizme](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
