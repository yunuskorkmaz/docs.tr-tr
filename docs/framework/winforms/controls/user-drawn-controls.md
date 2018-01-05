---
title: "Kullanıcı Çizimli Denetimler"
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
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9e486058850616c2304ce0032c35baa855fdf2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="user-drawn-controls"></a><span data-ttu-id="a6cca-102">Kullanıcı Çizimli Denetimler</span><span class="sxs-lookup"><span data-stu-id="a6cca-102">User-Drawn Controls</span></span>
<span data-ttu-id="a6cca-103">.NET Framework kolayca kendi denetimleri geliştirme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6cca-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="a6cca-104">Standart denetimler birbirine bağlı kod kümesidir, bir kullanıcı denetimi oluşturabilirsiniz veya yukarı sıfırdan denetiminizi tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6cca-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="a6cca-105">Devralma bile varolan denetimden devralan bir denetim oluşturmak ve devralınan işlevselliğini eklemek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6cca-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="a6cca-106">Hangi yaklaşımın kullanın, .NET Framework oluşturduğunuz herhangi bir denetim için özel bir grafik arabirim çizmek için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6cca-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="a6cca-107">Bir denetimin boyama denetimin kodda yürütülmesi tarafından gerçekleştirilir <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a6cca-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="a6cca-108">Tek bağımsız değişkeni <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi bir <xref:System.Windows.Forms.PaintEventArgs> tüm bilgi ve denetim işlemek için gerekli işlevselliği sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="a6cca-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="a6cca-109"><xref:System.Windows.Forms.PaintEventArgs> Denetiminizi işlemede kullanılan iki asıl nesneler özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="a6cca-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
-   <span data-ttu-id="a6cca-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>Nesne - dikdörtgenin çizileceğini denetim bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a6cca-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="a6cca-111">Bu tüm olabilir denetim ya da Denetim nasıl çizilir bağlı olarak denetim parçası.</span><span class="sxs-lookup"><span data-stu-id="a6cca-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
-   <span data-ttu-id="a6cca-112"><xref:System.Drawing.Graphics>Object - çeşitli grafik odaklı nesneleri ve denetiminizin çizmek gerekli işlevselliği sağlamak yöntemleri yalıtır.</span><span class="sxs-lookup"><span data-stu-id="a6cca-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="a6cca-113">Daha fazla bilgi için <xref:System.Drawing.Graphics> nesne ve kullanmak için bkz: nasıl [nasıl yapılır: çizim için grafik nesneleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="a6cca-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="a6cca-114"><xref:System.Windows.Forms.Control.OnPaint%2A> Her denetim çizilmiş veya ekranda yenilenir olay tetiklenir ve <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesnesi boyama yer alacak dikdörtgen temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a6cca-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="a6cca-115">Tüm denetim yenilenmesi, gerekiyorsa <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> tüm denetim boyutunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a6cca-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="a6cca-116">Denetim bir parçası, yenilenmesi ancak gerekiyor yalnızca <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesnesini temsil eden yalnızca çizilmesi gerektiğinde bölgesi.</span><span class="sxs-lookup"><span data-stu-id="a6cca-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="a6cca-117">Başka bir denetim veya formun kullanıcı arabiriminde bir denetim kısmen getirilmemeli zaman böyle bir durumda bir örnek olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a6cca-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="a6cca-118">İçinden devralma zaman <xref:System.Windows.Forms.Control> sınıfı, kılmanız gerekir <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi ve grafik işleme kod içinde sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a6cca-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="a6cca-119">Bir kullanıcı denetimi veya devralınan bir denetim için özel bir grafik arabirim sağlamak istiyorsanız, ayrıca geçersiz kılarak bunu yapabilirsiniz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a6cca-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="a6cca-120">Bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a6cca-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="a6cca-121">Önceki örnekte çok basit bir grafik gösterimi ile denetimi oluşturmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6cca-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="a6cca-122">Çağırır <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi temel sınıfın oluşturduğu bir <xref:System.Drawing.Pen> nesne hangi çizmek ve son olarak çizer Dikdörtgen elips bir belirlediği <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Size%2A> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a6cca-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="a6cca-123">Çoğu işleme kod bu değerden büyük ölçüde daha karmaşık olsa da, bu örnek kullanımını gösteren <xref:System.Drawing.Graphics> kapsamında yer alan nesne <xref:System.Windows.Forms.PaintEventArgs> nesne.</span><span class="sxs-lookup"><span data-stu-id="a6cca-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="a6cca-124">Bir grafik gösterimi gibi zaten bir sınıfından devralan gerçekleştiriyorsanız <xref:System.Windows.Forms.UserControl> veya <xref:System.Windows.Forms.Button>ve bu gösterimi işlemeniz içine dahil etmek istiyor musunuz, temel sınıfın çağırmalıdır değil <xref:System.Windows.Forms.Control.OnPaint%2A> yöntem.</span><span class="sxs-lookup"><span data-stu-id="a6cca-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="a6cca-125">Kodda <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi denetiminizin denetimi ilk çizildiğinde ve yenileniyor her yürütülecek.</span><span class="sxs-lookup"><span data-stu-id="a6cca-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="a6cca-126">Yeniden boyutlandırılmış her zaman denetiminiz çizilme emin olmak için Denetim oluşturucuya aşağıdaki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a6cca-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  <span data-ttu-id="a6cca-127">Kullanım <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> dikdörtgen olmayan denetimi için özellik.</span><span class="sxs-lookup"><span data-stu-id="a6cca-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6cca-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6cca-128">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Region%2A>  
 <xref:System.Windows.Forms.ControlStyles>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Windows.Forms.PaintEventArgs>  
 [<span data-ttu-id="a6cca-129">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a6cca-129">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="a6cca-130">Bağlı Denetimler</span><span class="sxs-lookup"><span data-stu-id="a6cca-130">Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 [<span data-ttu-id="a6cca-131">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="a6cca-131">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
