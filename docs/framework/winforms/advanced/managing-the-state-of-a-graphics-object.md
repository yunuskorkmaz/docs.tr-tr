---
title: "Bir Grafik Nesnesinin Durumunu Yönetme"
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
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 438243d16d8031d99e27993cadb44fd58bbec0b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="managing-the-state-of-a-graphics-object"></a>Bir Grafik Nesnesinin Durumunu Yönetme
<xref:System.Drawing.Graphics> Sınıftır merkezinde [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Herhangi bir şey çizmek için elde bir <xref:System.Drawing.Graphics> nesne özelliklerini ayarlamak ve yöntemlerini çağırın <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>vb.).  
  
 Aşağıdaki örnek çağrıları <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi. Geçirilen ilk bağımsız değişken <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi bir <xref:System.Drawing.Pen> nesnesi.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue) ' Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  // Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100);  
```  
  
## <a name="graphics-state"></a>Grafik Durumu  
 A <xref:System.Drawing.Graphics> nesnesi birden fazla sağlayın çizim yöntemleri gibi <xref:System.Drawing.Graphics.DrawLine%2A> ve <xref:System.Drawing.Graphics.DrawRectangle%2A>. A <xref:System.Drawing.Graphics> nesne ayrıca aşağıdaki kategorilere ayrılabilir grafik durumu korur:  
  
-   Kalite ayarları  
  
-   Dönüşümler  
  
-   Kırpma bölgesinin  
  
### <a name="quality-settings"></a>Kalite ayarları  
 A <xref:System.Drawing.Graphics> nesnenin çizilir öğeleri kalitesini etkileyen çeşitli özellikler vardır. Örneğin, ayarlayabileceğiniz <xref:System.Drawing.Graphics.TextRenderingHint%2A> özelliği metne uygulanan düzgünleştirme (varsa) türünü belirtin. Kalite etkileyen diğer özellikleri <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, ve <xref:System.Drawing.Graphics.InterpolationMode%2A>.  
  
 Aşağıdaki örnek kümesine yumuşatma mod ile iki elips çizer <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> ve kümesine yumuşatma modu ile <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue)  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias  
graphics.DrawEllipse(pen, 0, 0, 200, 100)  
graphics.SmoothingMode = SmoothingMode.HighSpeed  
graphics.DrawEllipse(pen, 0, 150, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias;  
graphics.DrawEllipse(pen, 0, 0, 200, 100);  
graphics.SmoothingMode = SmoothingMode.HighSpeed;  
graphics.DrawEllipse(pen, 0, 150, 200, 100);  
```  
  
### <a name="transformations"></a>Dönüşümler  
 A <xref:System.Drawing.Graphics> nesnesi tarafından çizilmiş tüm öğelerine uygulanan iki Dönüşümleri (world ve sayfa) tutar <xref:System.Drawing.Graphics> nesnesi. Herhangi bir afin dönüştürme world dönüşümünde depolanabilir. Afin dönüşümler ölçeklendirme, döndürme, yansıtma, eğriltme ve çevirme içerir. Sayfa dönüşümü ölçekleme ve birimler (örneğin, piksel inç olarak) değiştirmek için kullanılabilir. Daha fazla bilgi için bkz: [koordinat sistemleri ve dönüştürmeler](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).  
  
 Aşağıdaki örnek, dünya ve sayfa dönüşümleri ayarlar bir <xref:System.Drawing.Graphics> nesnesi. Dünya dönüşümü için 30 derecelik döndürme ayarlanır. İkinci koordinatları geçirilen şekilde sayfa dönüşümü ayarlayın <xref:System.Drawing.Graphics.DrawEllipse%2A> piksel yerine milimetre olarak kabul edilir. Kod iki özdeş çağrılar <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi. Dünya dönüşümü ilk uygulanan <xref:System.Drawing.Graphics.DrawEllipse%2A> çağrısı ve her iki dönüştürmeler (world ve sayfa) ikinci uygulanır <xref:System.Drawing.Graphics.DrawEllipse%2A> çağırın.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Red)  
  
graphics.ResetTransform()  
graphics.RotateTransform(30) ' world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
graphics.PageUnit = GraphicsUnit.Millimeter ' page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Red);   
  
graphics.ResetTransform();  
graphics.RotateTransform(30);                    // world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
graphics.PageUnit = GraphicsUnit.Millimeter;     // page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
```  
  
 Aşağıdaki çizimde iki elips gösterir. 30 derecelik döndürme (istemci alanının sol üst köşesinde) koordinat sistemi kökeni hakkında elipsleri merkezleri konusunda olmamasından unutmayın. Ayrıca, 1 kalem genişliği için ikinci elips 1 piksel ilk üç nokta ve 1 milimetre anlamına unutmayın.  
  
 ![Oval](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")  
  
### <a name="clipping-region"></a>Kırpma bölgesinin  
 A <xref:System.Drawing.Graphics> nesnesi tarafından çizilmiş tüm öğelere uygulanır kırpma bölgesinin tutar <xref:System.Drawing.Graphics> nesnesi. Kırpma bölgesinin çağırarak ayarlayabileceğiniz <xref:System.Drawing.Graphics.SetClip%2A> yöntemi.  
  
 Aşağıdaki örnekte, iki dikdörtgen birleşimi oluşturan tarafından artı şeklinde bir bölge oluşturur. Bu bölge kırpma bölgesinin atanmış bir <xref:System.Drawing.Graphics> nesnesi. Ardından kod kırpma bölgesinin iç için kısıtlı iki satır çizer.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](New Rectangle(50, 0, 50, 150))  
[region].Union(New Rectangle(0, 50, 150, 50))  
graphics.FillRegion(brush, [region])  
  
' Set the clipping region.  
graphics.SetClip([region], CombineMode.Replace)  
  
' Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160)  
graphics.DrawLine(pen, 40, 20, 190, 150)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
  
// Opaque red, width 5  
Pen pen = new Pen(Color.Red, 5);    
  
// Opaque aqua  
SolidBrush brush = new SolidBrush(Color.FromArgb(255, 180, 255, 255));    
  
// Create a plus-shaped region by forming the union of two rectangles.  
Region region = new Region(new Rectangle(50, 0, 50, 150));  
region.Union(new Rectangle(0, 50, 150, 50));  
graphics.FillRegion(brush, region);  
  
// Set the clipping region.  
graphics.SetClip(region, CombineMode.Replace);  
  
// Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160);  
graphics.DrawLine(pen, 40, 20, 190, 150);  
```  
  
 Aşağıdaki çizimde kırpılmış satırları gösterir.  
  
 ![Sınırlı Kırpma bölgesinin](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Grafikler ve Windows Forms'ta çizme](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [İç içe grafik kapsayıcılarını kullanma](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)
