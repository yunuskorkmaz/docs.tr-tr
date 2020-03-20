---
title: 'Nasıl Yapılsın: Titremeyi Azaltmak için Pikselleri Kopyala'
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
ms.openlocfilehash: a25295532d7123d92bcacc6828d3e8cfcc839d6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182581"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Nasıl yapılır: Windows Formlarında Titreşimi Azaltmak için Piksel Kopyalama
Basit bir grafiği animasyona aldığınızda, kullanıcılar bazen titreme veya diğer istenmeyen görsel efektlerle karşılaşabilir. Bu sorunu sınırlamanın bir yolu grafiküzerinde bir "bitblt" işlemi kullanmaktır. Bitblt, renk verilerinin piksellerin başlangıç dikdörtgeninden piksellerin hedef dikdörtgenine "bit bloğu aktarımı"dır.  
  
 Windows Forms ile bitblt <xref:System.Drawing.Graphics.CopyFromScreen%2A> <xref:System.Drawing.Graphics> sınıfın yöntemi kullanılarak gerçekleştirilir. Yöntemin parametrelerinde, kaynak ve hedef (nokta olarak), kopyalanacak alanın boyutunu ve yeni şekli çizmek için kullanılan grafik nesnesini belirtirsiniz.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.Paint> olay işleyicisindeki forma bir şekil çizilir. Daha sonra, <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntem şekli çoğaltmak için kullanılır.  
  
> [!NOTE]
> Formun <xref:System.Windows.Forms.Control.DoubleBuffered%2A> özelliğinin, `true` <xref:System.Windows.Forms.Control.Paint> grafik tabanlı kodun çift arabelleğe alınmasını sağlayacak şekilde ayarlanması. Bu, aşağıdaki kodu kullanırken herhangi bir fark performans kazanımları olmayacak olsa da, daha karmaşık grafik işleme kodu ile çalışırken akılda tutulması gereken bir şeydir.  
  
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
 Yukarıdaki kod, form <xref:System.Windows.Forms.Control.Paint> yeniden çizildiğinde grafiklerin devam edilebilmektedir. Bu nedenle, form yeniden boyutlandırılırveya <xref:System.Windows.Forms.Form.Load> başka bir form tarafından gizlenmişse, çizilen içerik yeniden çizilmeyecektir, çünkü olay işleyicisinde grafikle ilgili yöntemleri aramayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Windows Forms’da Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
- [Çizgiler ve Şekiller Çizmek için Kalem Kullanma](using-a-pen-to-draw-lines-and-shapes.md)
