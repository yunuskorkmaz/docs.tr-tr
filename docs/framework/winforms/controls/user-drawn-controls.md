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
ms.openlocfilehash: 06513fc44782c78d2d69b82130542949519c0107
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158450"
---
# <a name="user-drawn-controls"></a>Kullanıcı Çizimli Denetimler
.NET Framework kolayca kendi denetimleri geliştirme olanağı sağlar. Standart denetimler kodla birlikte ilişkili bir dizi olan bir kullanıcı denetimi oluşturabilir veya sıfırdan kendi denetiminizi yukarı tasarlayabilirsiniz. Devralma, varolan bir denetimden devralan bir denetim oluşturma ve doğal işlevselliği eklemek için bile kullanabilirsiniz. Hangi yaklaşımı kullanın, .NET Framework özel bir grafik arabirim için oluşturduğunuz herhangi bir denetimi çizmek için işlevsellik sağlar.  
  
 Boyama bir denetimin, denetimin içindeki kod yürütmeyi tarafından gerçekleştirilir <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. Tek bağımsız değişkeni <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi bir <xref:System.Windows.Forms.PaintEventArgs> tüm bilgi ve denetim oluşturmak için gereken işlevselliği sağlayan nesne. <xref:System.Windows.Forms.PaintEventArgs> Denetiminizin işlemede kullanılan iki asıl nesneler özellikleri sağlar:  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Nesne - dikdörtgenin çizileceğini denetim bölümünü temsil eder. Bu, tüm olabilir denetimi veya denetim, denetimin nasıl çizilmeden bağlı olarak bir parçası.  
  
-   <xref:System.Drawing.Graphics> Object - çeşitli grafik odaklı nesneleri ve denetiminizi çizmek için gereken işlevselliği sağlayan yöntemler kapsüller.  
  
 Daha fazla bilgi için <xref:System.Drawing.Graphics> nesne ve onu kullanmak üzere nasıl [nasıl yapılır: Çizim için grafik nesneleri oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> Her denetimin çizilmiş veya ekranda yenilenir olay tetiklenir ve <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesneyi temsil ediyor dikdörtgenin boyama yer alır. Tüm denetim yenilenmesi, gerekiyorsa <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> tüm denetiminin boyutunu temsil eder. Yalnızca denetim parçası yenilenmesi, ancak gereken <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesnesini temsil eden çizilmesini gerektiren bölge. Bir denetimi başka bir denetim veya form kullanıcı arabiriminde kısmen engellediği zaman örneği böyle bir durumda olacaktır.  
  
 Gelen devralınırken <xref:System.Windows.Forms.Control> sınıfı kılmanız gerekir <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi ve içindeki grafik işleme kodunu sağlayın. Bir kullanıcı denetimi veya devralınan bir denetim için özel bir grafik arabirim sağlamak istiyorsanız, bunu da geçersiz kılarak yapabilirsiniz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. Bir örnek aşağıda gösterilmiştir:  
  
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
  
 Önceki örnek çok basit bir grafik gösterimi denetimiyle nasıl oluşturulacağını gösterir. Çağrı <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi temel sınıfın oluşturduğu bir <xref:System.Drawing.Pen> çizmek, nesne ve son olarak bir dikdörtgenin içindeki bir elips çizer belirlenir <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Size%2A> denetimi. Çoğu işleme kodunu bundan çok daha karmaşık olsa da, bu örnek, kullanımını gösterir. <xref:System.Drawing.Graphics> nesne içinde yer alan <xref:System.Windows.Forms.PaintEventArgs> nesne. Bir grafik gösterimi gibi zaten bir sınıfından devralan gerçekleştiriyorsanız <xref:System.Windows.Forms.UserControl> veya <xref:System.Windows.Forms.Button>ve bu gösterimi, işleme halinde birleştirmek istemiyorsanız, temel sınıfın çağırmalıdır değil <xref:System.Windows.Forms.Control.OnPaint%2A> yöntem.  
  
 Kodda <xref:System.Windows.Forms.Control.OnPaint%2A> denetiminizin yöntemi denetim çizildiğinde ve onu yenilendiğinde yürütülecek. Denetim yeniden boyutlandırılmış her zaman yeniden çizilir emin olmak için oluşturucuya denetiminizin aşağıdaki satırı ekleyin:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  Kullanım <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> dikdörtgen olmayan denetimi uygulamak için özellik.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Nasıl yapılır: Çizim için grafik nesneleri oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Bağlı Denetimler](constituent-controls.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
