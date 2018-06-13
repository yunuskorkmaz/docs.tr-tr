---
title: 'Nasıl yapılır: Windows Formlarında Titreşimi Azaltmak için Piksel Kopyalama'
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
ms.openlocfilehash: 65428132c885191b62c3b4a76c8937bf8f3f6732
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522050"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Nasıl yapılır: Windows Formlarında Titreşimi Azaltmak için Piksel Kopyalama
Basit bir grafik animasyon yapıldığında, kullanıcılar bazen titreşimi veya istenmeyen diğer görsel efektler karşılaşırsınız. Bu sorunu sınırlamak için bir yolu, grafiğin üzerinde bir "bitblt" işlem kullanmaktır. BitBlt "bit bloğu aktarımı" renk verilerin kaynak dikdörtgen piksel hedef dikdörtgene piksel ' dir.  
  
 Windows Forms ile bitblt kullanılarak gerçekleştirilir <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı. Yöntem parametreleri kaynak ve hedef (olarak noktaları), kopyalanacak alanının boyutunu ve yeni Şekli çizmek için kullanılan grafik nesnesi belirtin.  
  
 Aşağıdaki örnekte, bir şekli formunda çizilir kendi <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Ardından, <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntemi şekli çoğaltmak için kullanılır.  
  
> [!NOTE]
>  Formun ayarlama <xref:System.Windows.Forms.Control.DoubleBuffered%2A> özelliğine `true` grafik tabanlı kodda yapar <xref:System.Windows.Forms.Control.Paint> olay çift arabelleğe alındı. Bu herhangi discernable performans artışı aşağıdaki kodu kullanırken olmaz olsa da, daha karmaşık grafik işleme kodu ile çalışırken göz önünde bulundurmanız bir şey durumdur.  
  
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
 Yukarıdaki kod formun Çalıştır <xref:System.Windows.Forms.Control.Paint> olay işleyicisi böylece form yeniden başlatıldığında grafik devam. Bu nedenle, grafik ilgili yöntemleri çağırmayın <xref:System.Windows.Forms.Form.Load> olay işleyicisi, formu yeniden boyutlandırılmış veya başka bir form tarafından getirilmemeli çizilmiş içeriği yeniden değil çünkü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.CopyPixelOperation>  
 <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
