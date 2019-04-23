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
ms.openlocfilehash: e3d1c2b681e98dc7c45467683924dd4022eb377e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094040"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Nasıl yapılır: Windows Forms’da Titreşimi Azaltmak için Piksel Kopyalama
Basit bir grafik animasyon eklediğinizde, kullanıcılar bazen titreşimini veya istenmeyen diğer görsel efektler karşılaşırsınız. Bu sorunu sınırlamanın yöntemlerinden biri, grafiğin üzerinde "bitblt" işlem kullanmaktır. BitBlt "bit bloğu aktarımı" renk verileri piksel bir kaynak dikdörtgenden hedef dikdörtgene piksel ' dir.  
  
 Windows Forms ile bitblt kullanılarak gerçekleştirilir <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı. Yöntem parametrelerinde, kaynak ve hedef (nokta) olarak kopyalanacak alanının boyutunu ve yeni şekil çizmek için kullanılan grafik nesnesi belirtin.  
  
 Aşağıdaki örnekte, bir şekil biçiminde çizilir kendi <xref:System.Windows.Forms.Control.Paint> olay işleyicisi. Ardından, <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntemi şekli çoğaltmak için kullanılır.  
  
> [!NOTE]
>  Formun ayarlama <xref:System.Windows.Forms.Control.DoubleBuffered%2A> özelliğini `true` grafik tabanlı kodda hale getirecek <xref:System.Windows.Forms.Control.Paint> olayı iki kez arabelleğe alınan. Bu tüm anlaşılabilir performans artışı aşağıdaki kodu kullanırken olmaz sırada, daha karmaşık grafik işleme kodu ile çalışırken göz önünde bulundurmanız bir şeydir.  
  
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
 Yukarıdaki kod formun çalıştırılan <xref:System.Windows.Forms.Control.Paint> olay işleyicisi, böylece form yeniden çizildiğinde grafik kalıcı. Bu nedenle, grafik ile ilgili yöntemleri çağırmayın <xref:System.Windows.Forms.Form.Load> olay işleyicisi, formu yeniden boyutlandırılabilir veya başka bir form tarafından engellediği çizilen içeriği yeniden değil çünkü.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
