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
ms.openlocfilehash: 1529d4d62004becca4495d96fa893da20caa3954
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709686"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="affc2-102">Kullanıcı Çizimli Denetimler</span><span class="sxs-lookup"><span data-stu-id="affc2-102">User-Drawn Controls</span></span>
<span data-ttu-id="affc2-103">.NET Framework kolayca kendi denetimleri geliştirme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="affc2-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="affc2-104">Standart denetimler kodla birlikte ilişkili bir dizi olan bir kullanıcı denetimi oluşturabilir veya sıfırdan kendi denetiminizi yukarı tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="affc2-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="affc2-105">Devralma, varolan bir denetimden devralan bir denetim oluşturma ve doğal işlevselliği eklemek için bile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="affc2-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="affc2-106">Hangi yaklaşımı kullanın, .NET Framework özel bir grafik arabirim için oluşturduğunuz herhangi bir denetimi çizmek için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="affc2-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="affc2-107">Boyama bir denetimin, denetimin içindeki kod yürütmeyi tarafından gerçekleştirilir <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="affc2-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="affc2-108">Tek bağımsız değişkeni <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi bir <xref:System.Windows.Forms.PaintEventArgs> tüm bilgi ve denetim oluşturmak için gereken işlevselliği sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="affc2-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="affc2-109"><xref:System.Windows.Forms.PaintEventArgs> Denetiminizin işlemede kullanılan iki asıl nesneler özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="affc2-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
-   <span data-ttu-id="affc2-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Nesne - dikdörtgenin çizileceğini denetim bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="affc2-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="affc2-111">Bu, tüm olabilir denetimi veya denetim, denetimin nasıl çizilmeden bağlı olarak bir parçası.</span><span class="sxs-lookup"><span data-stu-id="affc2-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
-   <span data-ttu-id="affc2-112"><xref:System.Drawing.Graphics> Object - çeşitli grafik odaklı nesneleri ve denetiminizi çizmek için gereken işlevselliği sağlayan yöntemler kapsüller.</span><span class="sxs-lookup"><span data-stu-id="affc2-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="affc2-113">Daha fazla bilgi için <xref:System.Drawing.Graphics> nesne ve onu kullanmak üzere nasıl [nasıl yapılır: Çizim için grafik nesneleri oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="affc2-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="affc2-114"><xref:System.Windows.Forms.Control.OnPaint%2A> Her denetimin çizilmiş veya ekranda yenilenir olay tetiklenir ve <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesneyi temsil ediyor dikdörtgenin boyama yer alır.</span><span class="sxs-lookup"><span data-stu-id="affc2-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="affc2-115">Tüm denetim yenilenmesi, gerekiyorsa <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> tüm denetiminin boyutunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="affc2-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="affc2-116">Yalnızca denetim parçası yenilenmesi, ancak gereken <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesnesini temsil eden çizilmesini gerektiren bölge.</span><span class="sxs-lookup"><span data-stu-id="affc2-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="affc2-117">Bir denetimi başka bir denetim veya form kullanıcı arabiriminde kısmen engellediği zaman örneği böyle bir durumda olacaktır.</span><span class="sxs-lookup"><span data-stu-id="affc2-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="affc2-118">Gelen devralınırken <xref:System.Windows.Forms.Control> sınıfı kılmanız gerekir <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi ve içindeki grafik işleme kodunu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="affc2-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="affc2-119">Bir kullanıcı denetimi veya devralınan bir denetim için özel bir grafik arabirim sağlamak istiyorsanız, bunu da geçersiz kılarak yapabilirsiniz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="affc2-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="affc2-120">Bir örnek aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="affc2-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="affc2-121">Önceki örnek çok basit bir grafik gösterimi denetimiyle nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="affc2-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="affc2-122">Çağrı <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi temel sınıfın oluşturduğu bir <xref:System.Drawing.Pen> çizmek, nesne ve son olarak bir dikdörtgenin içindeki bir elips çizer belirlenir <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Size%2A> denetimi.</span><span class="sxs-lookup"><span data-stu-id="affc2-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="affc2-123">Çoğu işleme kodunu bundan çok daha karmaşık olsa da, bu örnek, kullanımını gösterir. <xref:System.Drawing.Graphics> nesne içinde yer alan <xref:System.Windows.Forms.PaintEventArgs> nesne.</span><span class="sxs-lookup"><span data-stu-id="affc2-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="affc2-124">Bir grafik gösterimi gibi zaten bir sınıfından devralan gerçekleştiriyorsanız <xref:System.Windows.Forms.UserControl> veya <xref:System.Windows.Forms.Button>ve bu gösterimi, işleme halinde birleştirmek istemiyorsanız, temel sınıfın çağırmalıdır değil <xref:System.Windows.Forms.Control.OnPaint%2A> yöntem.</span><span class="sxs-lookup"><span data-stu-id="affc2-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="affc2-125">Kodda <xref:System.Windows.Forms.Control.OnPaint%2A> denetiminizin yöntemi denetim çizildiğinde ve onu yenilendiğinde yürütülecek.</span><span class="sxs-lookup"><span data-stu-id="affc2-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="affc2-126">Denetim yeniden boyutlandırılmış her zaman yeniden çizilir emin olmak için oluşturucuya denetiminizin aşağıdaki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="affc2-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  <span data-ttu-id="affc2-127">Kullanım <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> dikdörtgen olmayan denetimi uygulamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="affc2-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="affc2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="affc2-128">See also</span></span>
- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="affc2-129">Nasıl yapılır: Çizim için grafik nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="affc2-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="affc2-130">Bağlı Denetimler</span><span class="sxs-lookup"><span data-stu-id="affc2-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="affc2-131">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="affc2-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
