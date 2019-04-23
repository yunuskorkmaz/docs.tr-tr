---
title: Bir Grafik Nesnesinin Durumunu Yönetme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
ms.openlocfilehash: 8fc92bf84def50bed54a054ae634a8a08c8835c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212459"
---
# <a name="managing-the-state-of-a-graphics-object"></a>Bir Grafik Nesnesinin Durumunu Yönetme
<xref:System.Drawing.Graphics> Sınıftır yaklaşımının temelindeki [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Herhangi bir şey çizmek için elde bir <xref:System.Drawing.Graphics> nesne özelliklerini ayarlayın ve yöntemlerinin çağrılması <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>vb.).  
  
 Aşağıdaki örnek çağrıları <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne. Geçirilen ilk bağımsız değişken <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi bir <xref:System.Drawing.Pen> nesne.  
  
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
 A <xref:System.Drawing.Graphics> nesnesi birden fazla sağlayın çizim yöntemleri gibi <xref:System.Drawing.Graphics.DrawLine%2A> ve <xref:System.Drawing.Graphics.DrawRectangle%2A>. A <xref:System.Drawing.Graphics> nesne Ayrıca, aşağıdaki kategorilere ayrılabilir grafik durumu, tutar:  
  
-   Kalite ayarları  
  
-   Dönüşümler  
  
-   Kırpma bölgesini  
  
### <a name="quality-settings"></a>Kalite ayarları  
 A <xref:System.Drawing.Graphics> nesne çizilir öğeleri kalitesini etkileyen çeşitli özelliklere sahiptir. Örneğin, ayarlayabilirsiniz <xref:System.Drawing.Graphics.TextRenderingHint%2A> özelliği metne uygulanan (varsa) düzgünleştirme türünü belirtin. Kalite etkileyen diğer özellikleri <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, ve <xref:System.Drawing.Graphics.InterpolationMode%2A>.  
  
 Aşağıdaki örnek kümesine yumuşatma modu ile iki elipsler çizer <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> kümesine yumuşatma modu ile diğerini <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:  
  
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
 A <xref:System.Drawing.Graphics> nesne tarafından çizilen tüm öğelere uygulanır iki Dönüşümleri (dünya ve sayfa) tutar <xref:System.Drawing.Graphics> nesne. Afin herhangi bir dönüştürme gerçek koordinat dönüştürmesini içinde depolanabilir. Afin dönüşümler ölçeklendirme, döndürme, yansıtma, eğme ve çevirme içerir. Sayfa dönüşümü, ölçekleme ve birimler (örneğin, piksel inç olarak) değiştirmek için kullanılabilir. Daha fazla bilgi için [koordinat sistemleri ve dönüştürmeler](coordinate-systems-and-transformations.md).  
  
 Aşağıdaki örnek, dünya ve sayfa dönüşümleri ayarlar bir <xref:System.Drawing.Graphics> nesne. Gerçek koordinat dönüştürmesini bir 30 derece döndürme için ayarlanır. Böylece ikinci koordinatları geçirilen sayfa dönüşümü ayarlanır <xref:System.Drawing.Graphics.DrawEllipse%2A> milimetre yerine piksel olarak kabul edilir. Kod iki özdeş çağrılar <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi. Gerçek koordinat dönüştürmesini ilk uygulanan <xref:System.Drawing.Graphics.DrawEllipse%2A> çağrısı ve her iki Dönüşümleri (dünya ve sayfa) ikinci uygulanır <xref:System.Drawing.Graphics.DrawEllipse%2A> çağırın.  
  
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
  
 Aşağıdaki çizimde, iki üç nokta simgesini gösterir. 30 derece döndürme koordinat sisteminde (istemci alanını sol üst köşesinde) kaynağı hakkında üç nokta simgesini merkezleri hakkında değil unutmayın. Ayrıca kalem genişliği 1 için ikinci üç noktanın 1 piksel artımlı ilk üç nokta işaretine ve 1 milimetre anlamına gelir.  
  
 ![İki üç nokta simgesini gösteren çizimde: döndürme ve Kalem genişliği.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>Kırpma bölgesini  
 A <xref:System.Drawing.Graphics> nesne tarafından çizilen tüm öğelere uygulanır bir kırpma bölgesini tutar <xref:System.Drawing.Graphics> nesne. Kırpma bölgesini çağırarak ayarlayabileceğiniz <xref:System.Drawing.Graphics.SetClip%2A> yöntemi.  
  
 Aşağıdaki örnek, iki dikdörtgenler birleşimi oluşturan tarafından artı şeklindeki bir bölgesi oluşturur. Bu bölge kırpma bölgesini belirlenmiş bir <xref:System.Drawing.Graphics> nesne. Ardından kod, kırpma bölgesini iç için kısıtlı olan iki satır çizer.  
  
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
  
 Kırpılmış satır aşağıda gösterilmiştir:  
  
 ![Sınırlı kırpma bölgesini gösteren diyagram.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [İç İçe Grafik Kapsayıcılarını Kullanma](using-nested-graphics-containers.md)
