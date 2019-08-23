---
title: 'Nasıl yapılır: Windows Forms’da Titreşimi Azaltmak için Piksel Kopyalama'
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
ms.openlocfilehash: 5a18539153c64a5059d8079f6e245115b026bb91
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950143"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Nasıl yapılır: Windows Forms’da Titreşimi Azaltmak için Piksel Kopyalama
Basit bir grafiğe animasyon uyguladığınızda, kullanıcılar bazen titreşmeye veya diğer istenmeyen görsel efektlere de karşılaşabilir. Bu sorunu sınırlamanın bir yolu, grafikte bir "BitBlt" işlemi kullanmaktır. BitBlt, piksellerin kaynak dikdörtgenindeki renk verisinin "bit bloktan blok aktarımı", piksellerin hedef dikdörtgenine kadar olur.  
  
 Windows Forms ile BitBlt, <xref:System.Drawing.Graphics.CopyFromScreen%2A> <xref:System.Drawing.Graphics> sınıfının yöntemi kullanılarak gerçekleştirilir. Yönteminin parametrelerinde, kaynak ve hedef (as noktaları), kopyalanacak alanın boyutu ve yeni şekli çizmek için kullanılan grafik nesnesi belirtirsiniz.  
  
 Aşağıdaki örnekte, bir şekil <xref:System.Windows.Forms.Control.Paint> olay işleyicisindeki formda çizilir. Sonra, <xref:System.Drawing.Graphics.CopyFromScreen%2A> şekli yinelemek için yöntemi kullanılır.  
  
> [!NOTE]
> Formun <xref:System.Windows.Forms.Control.DoubleBuffered%2A> özelliğinin özelliği olarak `true` ayarlanması, <xref:System.Windows.Forms.Control.Paint> olaydaki grafik tabanlı kodun çift arabellekli olmasını sağlar. Bu, aşağıdaki kodu kullanırken herhangi bir ayrılabilir performans kazancı olmasa da, daha karmaşık grafik işleme kodu ile çalışırken göz önünde bulundurmanız gereken bir şeydir.  
  
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
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki kod formun <xref:System.Windows.Forms.Control.Paint> olay işleyicisinde çalıştırılır, böylece grafik form yeniden çizilene kadar devam eder. Bu nedenle, form başka bir form tarafından yeniden boyutlandırılmışsa veya <xref:System.Windows.Forms.Form.Load> gizlendiyse çizilen içerik yeniden çizilmez olduğundan, olay işleyicisinde grafik ile ilgili yöntemleri çağırmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
