---
title: Kullanıcı Çizimli Denetimler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: 50036f5bef323368b4970a080ca7a70cf94252d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966481"
---
# <a name="user-drawn-controls"></a>Kullanıcı Çizimli Denetimler
.NET Framework kendi denetimlerinizi kolayca geliştirebilme olanağı sağlar. Kodla bir araya göre birbirine göre bağlantılı standart denetimler kümesi olan bir kullanıcı denetimi oluşturabilir veya kendi denetiminizi baştan sona tasarlayabilirsiniz. Devralma özelliğini, var olan bir denetimden devralan bir denetim oluşturmak ve onun kendi işlevselliğine eklemek için de kullanabilirsiniz. Kullandığınız yaklaşım ne olursa olsun, .NET Framework oluşturduğunuz her denetim için özel bir grafik arabirim çizme işlevlerini sağlar.  
  
 Denetimin boyanması <xref:System.Windows.Forms.Control.OnPaint%2A> , denetimin yöntemindeki kodun yürütülmesi tarafından gerçekleştirilir. <xref:System.Windows.Forms.Control.OnPaint%2A> Metodun tek bağımsız değişkeni, denetiminizi işlemek için <xref:System.Windows.Forms.PaintEventArgs> gereken tüm bilgileri ve işlevleri sağlayan bir nesnedir. , <xref:System.Windows.Forms.PaintEventArgs> Denetimin görüntülenmesinde kullanılacak iki ana nesne özellikleri olarak sunulur:  
  
- <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>nesne-çizilecektir denetimin bölümünü temsil eden dikdörtgen. Bu, denetimin nasıl çizildiğine bağlı olarak tüm denetim veya denetimin bir bölümü olabilir.  
  
- <xref:System.Drawing.Graphics>nesne-denetimi çizmek için gereken işlevselliği sağlayan grafik tabanlı birçok nesne ve yöntemi kapsüller.  
  
 <xref:System.Drawing.Graphics> Nesnesi ve nasıl kullanılacağı hakkında daha fazla bilgi için bkz [. nasıl yapılır: Çizim](../advanced/how-to-create-graphics-objects-for-drawing.md)için grafik nesneleri oluşturun.  
  
 Olay, ekranda Denetim çizildiğinde veya yenilendiğinde tetiklenir <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> ve nesne, boyama yapılacak dikdörtgeni temsil eder. <xref:System.Windows.Forms.Control.OnPaint%2A> Tüm denetimin yenilenmesi <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> gerekiyorsa, tüm denetimin boyutunu temsil eder. Ancak denetimin yalnızca bir kısmının yenilenmesi gerekiyorsa, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesne yalnızca yeniden çizilmesi gereken bölgeyi temsil eder. Bu tür bir örnek, bir denetimin kullanıcı arabirimindeki başka bir denetim veya form tarafından kısmen gizlenmesidir.  
  
 <xref:System.Windows.Forms.Control> Sınıfından devralırken, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılmanız ve içinde grafik işleme kodu sağlamanız gerekir. Kullanıcı denetimine veya devralınmış bir denetime özel bir grafik arabirimi sağlamak istiyorsanız, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi geçersiz kılarak da bunu yapabilirsiniz. Aşağıda bir örnek gösterilmektedir:  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,   
         this.Size));  
   }
}  
```  
  
 Yukarıdaki örnekte, çok basit bir grafik gösterimiyle bir denetimin nasıl işlenmesi gösterilmektedir. Taban sınıfının <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini çağırır, çizim yapılacak bir <xref:System.Drawing.Pen> nesne oluşturur ve son olarak denetimin <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Size%2A> ile belirlenen dikdörtgende bir elips çizer. Çoğu işleme kodu bundan çok daha karmaşık olsa da, bu örnek <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.PaintEventArgs> nesnenin içinde içerilen nesnenin kullanımını gösterir. <xref:System.Windows.Forms.UserControl> Veya <xref:System.Windows.Forms.Control.OnPaint%2A> gibi bir grafik temsili zaten olan bir sınıftan devralırsanız ve bu gösterimi işleme eklemek istemiyorsanız, taban sınıfınızın ' u çağırmamalıdır <xref:System.Windows.Forms.Button> yöntemidir.  
  
 Denetiminizin <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemindeki kod, denetim ilk kez çizildiğinde ve her yenilendiğinde yürütülür. Denetiminizin yeniden boyutlandırıldığı her seferinde yeniden çizilmesini sağlamak için, denetiminizin oluşturucusuna aşağıdaki satırı ekleyin:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> Dikdörtgen olmayan bir denetim uygulamak için özelliğinikullanın.<xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Nasıl yapılır: Çizim için grafik nesneleri oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Bağlı Denetimler](constituent-controls.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
