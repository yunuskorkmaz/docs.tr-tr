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
ms.openlocfilehash: 26b4f062c120bf543a5e597fc8c734e8cc336bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="user-drawn-controls"></a>Kullanıcı Çizimli Denetimler
.NET Framework kolayca kendi denetimleri geliştirme olanağı sağlar. Standart denetimler birbirine bağlı kod kümesidir, bir kullanıcı denetimi oluşturabilirsiniz veya yukarı sıfırdan denetiminizi tasarlayabilirsiniz. Devralma bile varolan denetimden devralan bir denetim oluşturmak ve devralınan işlevselliğini eklemek için de kullanabilirsiniz. Hangi yaklaşımın kullanın, .NET Framework oluşturduğunuz herhangi bir denetim için özel bir grafik arabirim çizmek için işlevsellik sağlar.  
  
 Bir denetimin boyama denetimin kodda yürütülmesi tarafından gerçekleştirilir <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. Tek bağımsız değişkeni <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi bir <xref:System.Windows.Forms.PaintEventArgs> tüm bilgi ve denetim işlemek için gerekli işlevselliği sağlayan nesne. <xref:System.Windows.Forms.PaintEventArgs> Denetiminizi işlemede kullanılan iki asıl nesneler özellikleri sağlar:  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Nesne - dikdörtgenin çizileceğini denetim bölümünü temsil eder. Bu tüm olabilir denetim ya da Denetim nasıl çizilir bağlı olarak denetim parçası.  
  
-   <xref:System.Drawing.Graphics> Object - çeşitli grafik odaklı nesneleri ve denetiminizin çizmek gerekli işlevselliği sağlamak yöntemleri yalıtır.  
  
 Daha fazla bilgi için <xref:System.Drawing.Graphics> nesne ve kullanmak için bkz: nasıl [nasıl yapılır: çizim için grafik nesneleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> Her denetim çizilmiş veya ekranda yenilenir olay tetiklenir ve <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesnesi boyama yer alacak dikdörtgen temsil eder. Tüm denetim yenilenmesi, gerekiyorsa <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> tüm denetim boyutunu temsil eder. Denetim bir parçası, yenilenmesi ancak gerekiyor yalnızca <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesnesini temsil eden yalnızca çizilmesi gerektiğinde bölgesi. Başka bir denetim veya formun kullanıcı arabiriminde bir denetim kısmen getirilmemeli zaman böyle bir durumda bir örnek olacaktır.  
  
 İçinden devralma zaman <xref:System.Windows.Forms.Control> sınıfı, kılmanız gerekir <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi ve grafik işleme kod içinde sağlayın. Bir kullanıcı denetimi veya devralınan bir denetim için özel bir grafik arabirim sağlamak istiyorsanız, ayrıca geçersiz kılarak bunu yapabilirsiniz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. Bir örnek aşağıda verilmiştir:  
  
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
  
 Önceki örnekte çok basit bir grafik gösterimi ile denetimi oluşturmak nasıl gösterir. Çağırır <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi temel sınıfın oluşturduğu bir <xref:System.Drawing.Pen> nesne hangi çizmek ve son olarak çizer Dikdörtgen elips bir belirlediği <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Size%2A> denetimi. Çoğu işleme kod bu değerden büyük ölçüde daha karmaşık olsa da, bu örnek kullanımını gösteren <xref:System.Drawing.Graphics> kapsamında yer alan nesne <xref:System.Windows.Forms.PaintEventArgs> nesne. Bir grafik gösterimi gibi zaten bir sınıfından devralan gerçekleştiriyorsanız <xref:System.Windows.Forms.UserControl> veya <xref:System.Windows.Forms.Button>ve bu gösterimi işlemeniz içine dahil etmek istiyor musunuz, temel sınıfın çağırmalıdır değil <xref:System.Windows.Forms.Control.OnPaint%2A> yöntem.  
  
 Kodda <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi denetiminizin denetimi ilk çizildiğinde ve yenileniyor her yürütülecek. Yeniden boyutlandırılmış her zaman denetiminiz çizilme emin olmak için Denetim oluşturucuya aşağıdaki satırı ekleyin:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  Kullanım <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> dikdörtgen olmayan denetimi için özellik.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Control.Region%2A>  
 <xref:System.Windows.Forms.ControlStyles>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Windows.Forms.PaintEventArgs>  
 [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Bağlı Denetimler](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
