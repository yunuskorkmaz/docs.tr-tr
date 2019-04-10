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
ms.openlocfilehash: 76a5a4f9b02a71616d247a1bb0f03cc0aec1d70d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224883"
---
# <a name="constituent-controls"></a><span data-ttu-id="29127-102">Bağlı Denetimler</span><span class="sxs-lookup"><span data-stu-id="29127-102">Constituent Controls</span></span>
<span data-ttu-id="29127-103">Bir kullanıcı denetimi oluşturan denetimleri veya *bağlı denetimler* özel grafik işleme için geldiğinde terimiyle gösterilen gibi göreceli olarak sabit olduğundan.</span><span class="sxs-lookup"><span data-stu-id="29127-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="29127-104">Tüm Windows Forms denetimleri aracılığıyla kendi kendi işleme işlemek <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="29127-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="29127-105">Bu yöntem korunduğundan, geliştiriciler için erişilebilir değil ve böylece denetimin boyandığında yürütülmesini önlenemeyen.</span><span class="sxs-lookup"><span data-stu-id="29127-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="29127-106">Bu, ancak bağlı denetimler görünümünü etkilemek için kod eklenemiyor anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="29127-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="29127-107">Ek işleme, olay işleyici ekleme tarafından gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="29127-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="29127-108">Örneğin, yazma varsayalım. bir <xref:System.Windows.Forms.UserControl> adlı bir düğme olan `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="29127-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="29127-109">Tarafından sağlanan ne ötesinde ek işleme sağlamak onlardan <xref:System.Web.UI.WebControls.Button>, aşağıdakine benzer şekilde kullanıcı denetiminize için kod eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="29127-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
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
>  <span data-ttu-id="29127-110">Bazı Windows Forms denetimleri, gibi <xref:System.Windows.Forms.TextBox>, doğrudan tarafından Windows boyanan.</span><span class="sxs-lookup"><span data-stu-id="29127-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="29127-111">Bu durumlarda, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi asla çağrılmaz ve bu nedenle yukarıdaki örnekte asla çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="29127-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="29127-112">Bu her zaman yürüten bir metot oluşturur `MyButton.Paint` olay yürütür, böylece ek grafik gösterimi denetiminize ekleme.</span><span class="sxs-lookup"><span data-stu-id="29127-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="29127-113">Bu yürütülmesini engellemez Not `MyButton.OnPaint`, ve bu nedenle tüm genellikle bir düğme tarafından gerçekleştirilen boyama yine de, özel boyama ek olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="29127-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="29127-114">GDI + teknoloji ve özel işleme hakkında daha fazla ayrıntı için bkz: [GDI + ile grafik görüntü oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="29127-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="29127-115">Benzersiz bir gösterimini denetiminizin olmasını istiyorsanız, en iyi eylem planını devralınan bir denetim oluşturmak için ve bunun için özel işleme kodu yazmak için ' dir.</span><span class="sxs-lookup"><span data-stu-id="29127-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="29127-116">Ayrıntılar için bkz [User-Drawn denetimleri](user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="29127-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29127-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29127-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="29127-118">Kullanıcı Çizimli Denetimler</span><span class="sxs-lookup"><span data-stu-id="29127-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="29127-119">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="29127-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="29127-120">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="29127-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
