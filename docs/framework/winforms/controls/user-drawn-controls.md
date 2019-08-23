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
# <a name="user-drawn-controls"></a><span data-ttu-id="9e56e-102">Kullanıcı Çizimli Denetimler</span><span class="sxs-lookup"><span data-stu-id="9e56e-102">User-Drawn Controls</span></span>
<span data-ttu-id="9e56e-103">.NET Framework kendi denetimlerinizi kolayca geliştirebilme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e56e-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="9e56e-104">Kodla bir araya göre birbirine göre bağlantılı standart denetimler kümesi olan bir kullanıcı denetimi oluşturabilir veya kendi denetiminizi baştan sona tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e56e-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="9e56e-105">Devralma özelliğini, var olan bir denetimden devralan bir denetim oluşturmak ve onun kendi işlevselliğine eklemek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e56e-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="9e56e-106">Kullandığınız yaklaşım ne olursa olsun, .NET Framework oluşturduğunuz her denetim için özel bir grafik arabirim çizme işlevlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e56e-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="9e56e-107">Denetimin boyanması <xref:System.Windows.Forms.Control.OnPaint%2A> , denetimin yöntemindeki kodun yürütülmesi tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9e56e-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="9e56e-108"><xref:System.Windows.Forms.Control.OnPaint%2A> Metodun tek bağımsız değişkeni, denetiminizi işlemek için <xref:System.Windows.Forms.PaintEventArgs> gereken tüm bilgileri ve işlevleri sağlayan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="9e56e-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="9e56e-109">, <xref:System.Windows.Forms.PaintEventArgs> Denetimin görüntülenmesinde kullanılacak iki ana nesne özellikleri olarak sunulur:</span><span class="sxs-lookup"><span data-stu-id="9e56e-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
- <span data-ttu-id="9e56e-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>nesne-çizilecektir denetimin bölümünü temsil eden dikdörtgen.</span><span class="sxs-lookup"><span data-stu-id="9e56e-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="9e56e-111">Bu, denetimin nasıl çizildiğine bağlı olarak tüm denetim veya denetimin bir bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9e56e-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
- <span data-ttu-id="9e56e-112"><xref:System.Drawing.Graphics>nesne-denetimi çizmek için gereken işlevselliği sağlayan grafik tabanlı birçok nesne ve yöntemi kapsüller.</span><span class="sxs-lookup"><span data-stu-id="9e56e-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="9e56e-113"><xref:System.Drawing.Graphics> Nesnesi ve nasıl kullanılacağı hakkında daha fazla bilgi için bkz [. nasıl yapılır: Çizim](../advanced/how-to-create-graphics-objects-for-drawing.md)için grafik nesneleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e56e-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="9e56e-114">Olay, ekranda Denetim çizildiğinde veya yenilendiğinde tetiklenir <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> ve nesne, boyama yapılacak dikdörtgeni temsil eder. <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="9e56e-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="9e56e-115">Tüm denetimin yenilenmesi <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> gerekiyorsa, tüm denetimin boyutunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9e56e-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="9e56e-116">Ancak denetimin yalnızca bir kısmının yenilenmesi gerekiyorsa, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesne yalnızca yeniden çizilmesi gereken bölgeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9e56e-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="9e56e-117">Bu tür bir örnek, bir denetimin kullanıcı arabirimindeki başka bir denetim veya form tarafından kısmen gizlenmesidir.</span><span class="sxs-lookup"><span data-stu-id="9e56e-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="9e56e-118"><xref:System.Windows.Forms.Control> Sınıfından devralırken, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini geçersiz kılmanız ve içinde grafik işleme kodu sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e56e-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="9e56e-119">Kullanıcı denetimine veya devralınmış bir denetime özel bir grafik arabirimi sağlamak istiyorsanız, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi geçersiz kılarak da bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e56e-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="9e56e-120">Aşağıda bir örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9e56e-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="9e56e-121">Yukarıdaki örnekte, çok basit bir grafik gösterimiyle bir denetimin nasıl işlenmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e56e-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="9e56e-122">Taban sınıfının <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini çağırır, çizim yapılacak bir <xref:System.Drawing.Pen> nesne oluşturur ve son olarak denetimin <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Size%2A> ile belirlenen dikdörtgende bir elips çizer.</span><span class="sxs-lookup"><span data-stu-id="9e56e-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="9e56e-123">Çoğu işleme kodu bundan çok daha karmaşık olsa da, bu örnek <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.PaintEventArgs> nesnenin içinde içerilen nesnenin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e56e-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="9e56e-124"><xref:System.Windows.Forms.UserControl> Veya <xref:System.Windows.Forms.Control.OnPaint%2A> gibi bir grafik temsili zaten olan bir sınıftan devralırsanız ve bu gösterimi işleme eklemek istemiyorsanız, taban sınıfınızın ' u çağırmamalıdır <xref:System.Windows.Forms.Button> yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="9e56e-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="9e56e-125">Denetiminizin <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemindeki kod, denetim ilk kez çizildiğinde ve her yenilendiğinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9e56e-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="9e56e-126">Denetiminizin yeniden boyutlandırıldığı her seferinde yeniden çizilmesini sağlamak için, denetiminizin oluşturucusuna aşağıdaki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9e56e-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> <span data-ttu-id="9e56e-127">Dikdörtgen olmayan bir denetim uygulamak için özelliğinikullanın.<xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9e56e-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e56e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e56e-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="9e56e-129">Nasıl yapılır: Çizim için grafik nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e56e-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="9e56e-130">Bağlı Denetimler</span><span class="sxs-lookup"><span data-stu-id="9e56e-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="9e56e-131">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="9e56e-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
