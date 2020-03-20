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
ms.openlocfilehash: c68c8c88376cfe7295962264c466030115f2f3db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182017"
---
# <a name="user-drawn-controls"></a>Kullanıcı Çizimli Denetimler
.NET Framework size kendi denetimlerinizi kolayca geliştirme olanağı sağlar. Kodla birbirine bağlı standart denetimler kümesi olan bir kullanıcı denetimi oluşturabilir veya kendi denetiminizi sıfırdan tasarlayabilirsiniz. Hatta varolan bir denetimden devralan bir denetim oluşturmak ve doğal işlevselliğini eklemek için devralma kullanabilirsiniz. Hangi yaklaşımı kullanırsanız kullanın, .NET Framework oluşturduğunuz herhangi bir denetim için özel bir grafik arabirimi çizmek için işlevsellik sağlar.  
  
 Denetimin boyanmasi, denetim <xref:System.Windows.Forms.Control.OnPaint%2A> yönteminde kodun yürütülmesi yle gerçekleştirilir. <xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemin tek bağımsız değişkeni, denetiminizi işlemek için gereken tüm bilgileri ve işlevselliği sağlayan bir <xref:System.Windows.Forms.PaintEventArgs> nesnedir. Özellikleri <xref:System.Windows.Forms.PaintEventArgs> olarak denetim oluşturma kullanılacak iki temel nesneleri sağlar:  
  
- <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>nesne - çizilecek denetimin bölümünü temsil eden dikdörtgen. Bu, denetimin nasıl çizildiğine bağlı olarak tüm denetim veya denetimin bir parçası olabilir.  
  
- <xref:System.Drawing.Graphics>nesne - denetiminizi çizmek için gerekli işlevselliği sağlayan birkaç grafik yönelimli nesne ve yöntem kapsüller.  
  
 <xref:System.Drawing.Graphics> Nesne ve nasıl kullanılacağı hakkında daha fazla bilgi için [bkz.](../advanced/how-to-create-graphics-objects-for-drawing.md)  
  
 Olay, <xref:System.Windows.Forms.Control.OnPaint%2A> denetim ekranda çizildiğinde veya yenilendiğinde ateşlenir ve <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesne boyamanın gerçekleşeceği dikdörtgeni temsil eder. Tüm denetimin yenilenmesi gerekiyorsa, tüm <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> denetimin boyutunu temsil edecektir. Ancak denetimin yalnızca bir kısmının yenilenmesi gerekiyorsa, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesne yalnızca yeniden çizilmesi gereken bölgeyi temsil eder. Böyle bir duruma örnek olarak, bir denetimin kullanıcı arabirimindeki başka bir denetim veya form tarafından kısmen gizlenmiş olması gerekir.  
  
 <xref:System.Windows.Forms.Control> Sınıftan devralma yaparken, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi geçersiz kılmanız ve içinde grafik oluşturma kodu sağlamanız gerekir. Kullanıcı denetimine veya devralınan denetime özel bir grafik arabirimi sağlamak istiyorsanız, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi geçersiz kılarak da yapabilirsiniz. Aşağıda bir örnek gösterilmiştir:  
  
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
  
 Önceki örnek, çok basit bir grafik gösterimi ile bir denetim nasıl işlenir gösterir. Taban sınıfın <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini çağırır, çizeceği <xref:System.Drawing.Pen> bir nesne oluşturur ve son olarak denetim tarafından <xref:System.Windows.Forms.Control.Location%2A> <xref:System.Windows.Forms.Control.Size%2A> belirlenen dikdörtgende bir elips çizer. Çoğu işleme kodu bundan önemli ölçüde daha karmaşık olsa da, <xref:System.Drawing.Graphics> bu örnek <xref:System.Windows.Forms.PaintEventArgs> nesnenin içinde bulunan nesnenin kullanımını gösterir. Zaten grafik gösterimi olan bir sınıftan devralma kalıyorsanız, <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>örneğin veya , bu temsili işlemenize dahil etmek istemiyorsanız, taban sınıfınızın <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini aramamalısınız.  
  
 Denetim yönteminizdeki <xref:System.Windows.Forms.Control.OnPaint%2A> kod, denetim ilk çizildiğinde ve yenilendiğinde yürütülür. Denetiminizin her yeniden boyutlandırılışında yeniden çizildiğinden emin olmak için denetiminizin oluşturucuya aşağıdaki satırı ekleyin:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> Dikdörtgen <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> olmayan bir denetim uygulamak için özelliği kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Bağlı Denetimler](constituent-controls.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
