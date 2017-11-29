---
title: "Nasıl yapılır: Windows Formlarında Titreşimi Azaltmak için Piksel Kopyalama"
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
- bitblt
- graphics [Windows Forms], copying
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing flicker
- pixels [Windows Forms], copying
- flicker
- bit-block transfer
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ed463b41d3c2a51b0f9be3d4ddabfd2d54a3c07
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Grafikler ve Windows Forms'ta çizme](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Çizgiler ve şekiller çizmek için kalem kullanma](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
