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
ms.openlocfilehash: fc6d6857e912ba14fca382eb49373655004534d5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720949"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>GDI+'da Fırçalar ve Dolgulu Şekiller
Kapalı şekil, bir elips ya da dikdörtgen gibi bir anahat ve bir iç oluşur. Ana hat kalem ile çizilir ve iç fırça ile doldurulur. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kapalı şekiller evin içindekiler doldurmak için birkaç fırça sınıfları sağlar: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, ve <xref:System.Drawing.Drawing2D.PathGradientBrush>. Bu sınıfların tümü devralınacak <xref:System.Drawing.Brush> sınıfı. Aşağıdaki çizimde, bir dikdörtgen ile düz fırça doldurulmuş ve elips tarama fırça ile doldurulmuş gösterir.  
  
 ![Doldurulmuş şekiller](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>Düz fırça  
 Örneği ihtiyacınız kapalı şekil doldurmak için <xref:System.Drawing.Graphics> sınıfı ve <xref:System.Drawing.Brush>. Örneğini <xref:System.Drawing.Graphics> yöntemleri gibi sağlar sınıfını <xref:System.Drawing.Graphics.FillRectangle%2A> ve <xref:System.Drawing.Graphics.FillEllipse%2A>ve <xref:System.Drawing.Brush> renk ve desen gibi dolgu özniteliklerini depolar. <xref:System.Drawing.Brush> Dolgu yöntemine geçirilen bağımsız değişkenlerden biri. Aşağıdaki kod örneği, bir elips kırmızı düz renk ile doldurun gösterilmektedir.  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  Önceki örnekte, fırça türünde <xref:System.Drawing.SolidBrush>, işlevinden devralan <xref:System.Drawing.Brush>.  
  
## <a name="hatch-brushes"></a>Tarama fırçalarını  
 Bir şekli tarama fırça doldururken bir ön plan rengi, bir arka plan rengi ve bir tarama stilini belirtin. Ön plan rengini tarama renktir.  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 50'den fazla tarama stili sağlar; Aşağıdaki çizimde gösterilen üç stillerdir <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, ve <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.  
  
 ![Doldurulmuş şekiller](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>Doku fırçaları  
 Bir doku fırçası ile bir şekli bir bit eşlem içinde depolanan bir desen ile doldurabilirsiniz. Örneğin, aşağıdaki resimde adlı bir disk dosyasında depolanan varsayalım `MyTexture.bmp`.  
  
 ![Şekil doldurulmuş](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 Aşağıdaki kod örneği, bir elips depolanan resim tekrarlayarak doldurmak gösterilmektedir `MyTexture.bmp`.  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 Dolu Elips aşağıda gösterilmiştir.  
  
 ![Şekil doldurulmuş](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>Gradyan Fırçalar  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Gradyan Fırçalar iki çeşit sağlar: doğrusal ve yolu. Bir şekli şekli arasında hareket ettikçe yatay, dikey kademeli olarak veya çapraz değişiklikleri rengi ile doldurmak için doğrusal gradyan fırçası kullanabilirsiniz. Aşağıdaki kod örneği, bir elips sağ kenarına elipsin sol kenardan geçerken yeşil maviye değiştiren yatay bir gradyan fırçası doldurmak gösterilmektedir.  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 Dolu Elips aşağıda gösterilmiştir.  
  
 ![Şekil doldurulmuş](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 Yolun gradyan fırçası edge doğru bir şeklin Merkezi'nden geçerken rengini değiştirmek için yapılandırılabilir.  
  
 ![Şekil doldurulmuş](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 Yolun gradyan Fırçalar oldukça esnektir. Aşağıdaki çizimde değişiklikleri aşamalı olarak kırmızı merkezinde her köşe, üç farklı renkler üçgeni doldurmak için kullanılan gradyan fırçası.  
  
 ![Şekil doldurulmuş](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Nasıl yapılır: Bir Windows formunda doldurulmuş dikdörtgen çizme](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [Nasıl yapılır: Bir Windows formunda doldurulmuş elips çizme](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
