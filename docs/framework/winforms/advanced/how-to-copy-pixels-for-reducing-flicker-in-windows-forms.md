---
title: 'Nasıl yapılır: titreşimi azaltmak için piksel kopyalama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitblt
- graphics [Windows Forms], copying
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing flicker
- pixels [Windows Forms], copying
- flicker
- bit-block transfer
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
ms.openlocfilehash: 299041e7038d5bd5b9824d668b3f47d842030ac7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746479"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Nasıl yapılır: Windows Formlarında Titreşimi Azaltmak için Piksel Kopyalama
Basit bir grafiğe animasyon uyguladığınızda, kullanıcılar bazen titreşmeye veya diğer istenmeyen görsel efektlere de karşılaşabilir. Bu sorunu sınırlamanın bir yolu, grafikte bir "BitBlt" işlemi kullanmaktır. BitBlt, piksellerin kaynak dikdörtgenindeki renk verisinin "bit bloktan blok aktarımı", piksellerin hedef dikdörtgenine kadar olur.  
  
 Windows Forms ile BitBlt, <xref:System.Drawing.Graphics> sınıfının <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntemi kullanılarak gerçekleştirilir. Yönteminin parametrelerinde, kaynak ve hedef (as noktaları), kopyalanacak alanın boyutu ve yeni şekli çizmek için kullanılan grafik nesnesi belirtirsiniz.  
  
 Aşağıdaki örnekte, bir şekil <xref:System.Windows.Forms.Control.Paint> olay işleyicisindeki formda çizilir. Sonra, şekli yinelemek için <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntemi kullanılır.  
  
> [!NOTE]
> Formun <xref:System.Windows.Forms.Control.DoubleBuffered%2A> özelliğinin `true` olarak ayarlanması <xref:System.Windows.Forms.Control.Paint> olaydaki grafik tabanlı kodun çift arabelleğe alınmayacak hale getirir. Bu, aşağıdaki kodu kullanırken herhangi bir ayrılabilir performans kazancı olmasa da, daha karmaşık grafik işleme kodu ile çalışırken göz önünde bulundurmanız gereken bir şeydir.  
  
## <a name="example"></a>Örnek  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),   
            new Size(70, 70));  
}  
```  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Yukarıdaki kod, form yeniden çizilene kadar grafiklerin kalıcı olması için formun <xref:System.Windows.Forms.Control.Paint> olay işleyicisinde çalıştırılır. Bu nedenle, form başka bir form tarafından yeniden boyutlandırılmışsa veya gizlendiyse çizilen içerik yeniden çizilmediği için <xref:System.Windows.Forms.Form.Load> olay işleyicisinde grafik ile ilgili yöntemleri çağırmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
