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
ms.openlocfilehash: 9475518a5f0422e0eac1ec521088071bb4d1c885
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519009"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>GDI+'da Fırçalar ve Dolgulu Şekiller
Dikdörtgene veya bir elips gibi kapalı bir şekil ana hattı ve bir iç oluşur. Anahat kalem ile çizilir ve iç fırça ile doldurulur. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kapalı şekiller evin içindekiler doldurmak için birkaç fırça sınıflar sağlar: <xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, ve <xref:System.Drawing.Drawing2D.PathGradientBrush>. Tüm bu sınıfların devralınmalıdır <xref:System.Drawing.Brush> sınıfı. Aşağıdaki çizimde bir dikdörtgen düz fırça ile doldurulur ve tarama fırça ile elips doldurulmuş gösterir.  
  
 ![Doldurulmuş şekiller](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>Düz Fırçalar  
 Kapalı bir şekil doldurmak için bir örneğini gereksinim <xref:System.Drawing.Graphics> sınıfı ve bir <xref:System.Drawing.Brush>. Örneğinin <xref:System.Drawing.Graphics> sınıfı yöntemleri gibi sağlar <xref:System.Drawing.Graphics.FillRectangle%2A> ve <xref:System.Drawing.Graphics.FillEllipse%2A>ve <xref:System.Drawing.Brush> dolgu rengini ve düzenini gibi özniteliklerini depolar. <xref:System.Drawing.Brush> Fill yöntemi bağımsız değişkenlerden biri geçirilir. Aşağıdaki kod örneğinde elips düz bir kırmızı renkle doldurma gösterilmektedir.  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  Önceki örnekte fırça türüdür <xref:System.Drawing.SolidBrush>, devralan <xref:System.Drawing.Brush>.  
  
## <a name="hatch-brushes"></a>Tarama fırçalarını  
 Bir şekli tarama fırça ile doldurduğunuzda ön plan rengini, arka plan rengi ve bir tarama stilini belirtin. Ön plan rengini tarama rengi ' dir.  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 50'den fazla tarama stili sağlar; Aşağıdaki çizimde gösterilen üç stillerdir <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>, <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>, ve <xref:System.Drawing.Drawing2D.HatchStyle.Cross>.  
  
 ![Doldurulmuş şekiller](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>Doku fırçaları  
 Doku fırça ile bir şekli bir bitmap depolanan bir desen ile doldurabilirsiniz. Örneğin, aşağıdaki resimde adlı bir disk dosyasında depolanan varsayalım `MyTexture.bmp`.  
  
 ![Doldurulmuş şekil](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 Aşağıdaki kod örneğinde depolanan resim tekrarlayarak elips doldurmak nasıl gösterir `MyTexture.bmp`.  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 Aşağıdaki çizimde doldurulmuş elips gösterir.  
  
 ![Doldurulmuş şekil](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>Gradyan Fırçalar  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Gradyan Fırçalar iki tür sağlar: doğrusal ve yolu. Bir şekli kademeli olarak şekli arasında taşıdığınızda gibi yatay, dikey veya çapraz değişiklikler renkle doldurmak için doğrusal gradyan fırçası kullanabilirsiniz. Aşağıdaki kod örneğinde elips elips sol kenarından sağ kenarı hareket ederken, yeşil mavi değişiklikler yatay bir gradyan fırçası doldurmak nasıl gösterir.  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 Aşağıdaki çizimde doldurulmuş elips gösterir.  
  
 ![Doldurulmuş şekil](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 Yolun gradyan fırçası kenar doğru şeklin Merkezi'nden taşırken rengini değiştirmek için yapılandırılabilir.  
  
 ![Doldurulmuş şekil](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 Yolun gradyan Fırçalar oldukça esnektir. Aşağıdaki çizimde değişikliklerden kademeli olarak kırmızı Center'da her üç farklı renk köşeleri adresindeki üçgen doldurmak için kullanılan gradyan fırçası.  
  
 ![Doldurulmuş şekil](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Nasıl yapılır: Bir Windows Formunda Doldurulmuş Dikdörtgen Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)  
 [Nasıl yapılır: Bir Windows Formunda Doldurulmuş Elips Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
