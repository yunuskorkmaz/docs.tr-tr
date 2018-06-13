---
title: Bağlı Denetimler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 6fb708b81089b4fcd3678b35d1bcf7da2244c6d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525568"
---
# <a name="constituent-controls"></a><span data-ttu-id="9753d-102">Bağlı Denetimler</span><span class="sxs-lookup"><span data-stu-id="9753d-102">Constituent Controls</span></span>
<span data-ttu-id="9753d-103">Bir kullanıcı denetimini oluşturan denetimleri veya *bağlı denetimler* özel grafikler oluşturma geldiğinde olarak ifade edilmektedir gibi göreceli olarak sabit olduğundan.</span><span class="sxs-lookup"><span data-stu-id="9753d-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="9753d-104">Kendi işleme aracılığıyla kendi tüm Windows Forms denetimlerini işleme <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9753d-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="9753d-105">Bu yöntem korumalı olduğundan, geliştiriciler için erişilebilir değil ve böylece denetimi boyandığında yürütülmesini önlenemeyen.</span><span class="sxs-lookup"><span data-stu-id="9753d-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="9753d-106">Bu, ancak bağlı denetimler görünümünü etkilemek için kod ekleyemezsiniz anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="9753d-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="9753d-107">Ek işleme, olay işleyici ekleme tarafından gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9753d-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="9753d-108">Örneğin, yazma varsayalım bir <xref:System.Windows.Forms.UserControl> adlı bir düğme ile `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="9753d-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="9753d-109">Ne tarafından sağlanan ötesinde ek işleme sağlamak onlardan <xref:System.Web.UI.WebControls.Button>, kullanıcı denetiminiz aşağıdakine benzer kod ekleme:</span><span class="sxs-lookup"><span data-stu-id="9753d-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=   
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,   
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="9753d-110">Gibi bazı Windows Forms denetimleri <xref:System.Windows.Forms.TextBox>, doğrudan Windows tarafından boyanır.</span><span class="sxs-lookup"><span data-stu-id="9753d-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="9753d-111">Bu durumlarda, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi hiçbir zaman çağrılır ve bu nedenle yukarıdaki örnekte hiçbir zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9753d-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="9753d-112">Bu her zaman yürüten bir yöntem oluşturur `MyButton.Paint` olayını yürüten, böylelikle ek grafik gösterimi, denetimine ekleme.</span><span class="sxs-lookup"><span data-stu-id="9753d-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="9753d-113">Bu yürütülmesi engellemez Not `MyButton.OnPaint`, ve dolayısıyla tüm genellikle bir düğme tarafından gerçekleştirilen boyama hala, özel boyama ek olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9753d-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="9753d-114">GDI + teknoloji ve özel işleme hakkında daha fazla ayrıntı için bkz: [GDI + ile grafik görüntü oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="9753d-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="9753d-115">Denetiminizi benzersiz bir gösterimini olmasını istiyorsanız, iyi davranış biçimini devralınan bir denetim oluşturmak için için özel işleme kod yazmaya ise.</span><span class="sxs-lookup"><span data-stu-id="9753d-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="9753d-116">Ayrıntılar için bkz [User-Drawn denetimleri](../../../../docs/framework/winforms/controls/user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9753d-116">For details, see [User-Drawn Controls](../../../../docs/framework/winforms/controls/user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9753d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9753d-117">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="9753d-118">Kullanıcı Çizimli Denetimler</span><span class="sxs-lookup"><span data-stu-id="9753d-118">User-Drawn Controls</span></span>](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 [<span data-ttu-id="9753d-119">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9753d-119">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="9753d-120">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="9753d-120">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
