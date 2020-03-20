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
ms.openlocfilehash: d1e7e6eac775ca779fb68605adcc9bc2b9915e49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182448"
---
# <a name="managing-the-state-of-a-graphics-object"></a>Bir Grafik Nesnesinin Durumunu Yönetme
Sınıf <xref:System.Drawing.Graphics> GDI+'nin kalbinde yer aldı. Bir <xref:System.Drawing.Graphics> şey çizmek için, bir nesne elde, özelliklerini <xref:System.Drawing.Graphics.DrawLine%2A> <xref:System.Drawing.Graphics.DrawImage%2A>ayarlamak <xref:System.Drawing.Graphics.DrawString%2A>ve yöntemleri , , , ve benzeri) diyoruz.  
  
 Aşağıdaki örnek, <xref:System.Drawing.Graphics.DrawRectangle%2A> bir <xref:System.Drawing.Graphics> nesnenin yöntemini çağırır. <xref:System.Drawing.Graphics.DrawRectangle%2A> Yönteme geçirilen ilk bağımsız <xref:System.Drawing.Pen> değişken bir nesnedir.  
  
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
 Bir <xref:System.Drawing.Graphics> nesne, çizim yöntemleri sağlamaktan <xref:System.Drawing.Graphics.DrawLine%2A> <xref:System.Drawing.Graphics.DrawRectangle%2A>daha fazlasını yapar, gibi ve. Bir <xref:System.Drawing.Graphics> nesne, aşağıdaki kategorilere bölünebilen grafik durumunu da korur:  
  
- Kalite ayarları  
  
- Dönüşümler  
  
- Kırpma bölgesi  
  
### <a name="quality-settings"></a>Kalite Ayarları  
 Nesne, <xref:System.Drawing.Graphics> çizilen öğelerin kalitesini etkileyen çeşitli özelliklere sahiptir. Örneğin, <xref:System.Drawing.Graphics.TextRenderingHint%2A> özelliği metne uygulanan antiialiasing türünü (varsa) belirtecek şekilde ayarlayabilirsiniz. Kaliteyi etkileyen diğer <xref:System.Drawing.Graphics.SmoothingMode%2A> <xref:System.Drawing.Graphics.CompositingMode%2A>özellikler <xref:System.Drawing.Graphics.CompositingQuality%2A>, <xref:System.Drawing.Graphics.InterpolationMode%2A>, , ve .  
  
 Aşağıdaki örnek, biri yumuşatma modu <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> ayarlanmış, diğeri yumuşatma modu aşağıdakiler için ayarlanmış <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>iki elips çizer:  
  
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
 Nesne, <xref:System.Drawing.Graphics> o <xref:System.Drawing.Graphics> nesne tarafından çizilen tüm öğelere uygulanan iki dönüşüm (dünya ve sayfa) tutar. Herhangi bir affine dönüşüm dünya dönüşümünde saklanabilir. Affine dönüşümleri ölçekleme, döndürme, yansıtma, eğriltme ve çevirmeyi içerir. Sayfa dönüştürme ölçekleme ve birimleri değiştirmek için kullanılabilir (örneğin, pikselden inç'e). Daha fazla bilgi için [Bkz. Koordinat Sistemleri ve Dönüşümler.](coordinate-systems-and-transformations.md)  
  
 Aşağıdaki örnek, bir <xref:System.Drawing.Graphics> nesnenin dünya ve sayfa dönüşümlerini ayarlar. Dünya dönüşümü 30 derecelik bir dönüşe ayarlandı. Sayfa dönüşümü, ikinciye <xref:System.Drawing.Graphics.DrawEllipse%2A> geçen koordinatların piksel yerine milimetre olarak kabul edilebis olması için ayarlanır. <xref:System.Drawing.Graphics.DrawEllipse%2A> Kod, yönteme iki özdeş arama yapar. Dünya dönüşümü ilk <xref:System.Drawing.Graphics.DrawEllipse%2A> çağrıya uygulanır, ikinci <xref:System.Drawing.Graphics.DrawEllipse%2A> çağrıya da dönüşümler (dünya ve sayfa) uygulanır.  
  
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
  
 Aşağıdaki resimde iki elips gösterilmektedir. 30 derecelik döndürmenin koordinat sisteminin (istemci alanının sol üst köşesi) kökeni yle ilgili olduğunu unutmayın, elipslerin merkezleri yle ilgili değil. Ayrıca, kalem genişliğinin ilk elips için 1 piksel ve ikinci elips için 1 milimetre anlamına geldiğini unutmayın.  
  
 ![İki elips gösteren çizim: döndürme ve kalem genişliği.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>Kırpma Bölgesi  
 Nesne, <xref:System.Drawing.Graphics> o <xref:System.Drawing.Graphics> nesne tarafından çizilen tüm öğeler için geçerli olan bir kırpma bölgesi tutar. Yöntemi arayarak kırpma bölgesini <xref:System.Drawing.Graphics.SetClip%2A> ayarlayabilirsiniz.  
  
 Aşağıdaki örnek, iki dikdörtgenin birleşimini oluşturarak artı şekilli bir bölge oluşturur. Bu bölge, bir <xref:System.Drawing.Graphics> nesnenin kırpma bölgesi olarak belirlenmiştir. Ardından kod, kırpma bölgesinin iç kısmıyla sınırlı iki satır çizer.  
  
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
  
 Aşağıdaki resimde kırpılalı çizgiler gösterilmektedir:  
  
 ![Sınırlı klip bölgesini gösteren diyagram.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [İç İçe Grafik Kapsayıcılarını Kullanma](using-nested-graphics-containers.md)
