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
ms.openlocfilehash: 522a1012fc7bdd54860b0538064ee073f7a761f7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918422"
---
# <a name="constituent-controls"></a><span data-ttu-id="e5c9e-102">Bağlı Denetimler</span><span class="sxs-lookup"><span data-stu-id="e5c9e-102">Constituent Controls</span></span>
<span data-ttu-id="e5c9e-103">Bir kullanıcı denetimini oluşturan denetimler veya bir ekip *denetimleri* , özel grafik işleme geldiğinde görece güvenilir bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e5c9e-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="e5c9e-104">Tüm Windows Forms denetimleri kendi kendi <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemleri aracılığıyla kendi işlemesini işler.</span><span class="sxs-lookup"><span data-stu-id="e5c9e-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="e5c9e-105">Bu yöntem korunduğundan, geliştirici tarafından erişilebilir değildir ve bu nedenle denetim boyandığında yürütülmesi önlenemez.</span><span class="sxs-lookup"><span data-stu-id="e5c9e-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="e5c9e-106">Ancak bu, bileşen denetimlerinin görünümünü etkilemek için kod ekleyemayacağınız anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="e5c9e-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="e5c9e-107">Ek işleme, bir olay işleyicisi eklenerek gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e5c9e-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="e5c9e-108">Örneğin, adlı <xref:System.Windows.Forms.UserControl> `MyButton`bir düğmeyle bir yazdığınızı varsayalım.</span><span class="sxs-lookup"><span data-stu-id="e5c9e-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="e5c9e-109">Tarafından sağlananlar dışında ek işleme sağlamak istiyorsanız <xref:System.Web.UI.WebControls.Button>, Kullanıcı denetiminin aşağıdakine benzer şekilde kod eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="e5c9e-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
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
> <span data-ttu-id="e5c9e-110">Gibi bazı Windows Forms denetimleri <xref:System.Windows.Forms.TextBox>, doğrudan Windows tarafından boyanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e5c9e-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="e5c9e-111">Bu örneklerde, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi hiçbir şekilde çağrılmaz ve bu nedenle yukarıdaki örnek hiçbir şekilde çağrılmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="e5c9e-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="e5c9e-112">Bu, `MyButton.Paint` olay her çalıştırıldığında çalıştırılan bir yöntem oluşturur ve bu sayede denetimenizde ek grafik gösterimi ekler.</span><span class="sxs-lookup"><span data-stu-id="e5c9e-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="e5c9e-113">Bunun yürütülmesini `MyButton.OnPaint`engellemez ve bu nedenle genellikle bir düğme tarafından gerçekleştirilen tüm boyama, özel boyamaya ek olarak yine de gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e5c9e-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="e5c9e-114">GDI+ teknolojisi ve özel işleme hakkında daha fazla bilgi için bkz. [GDI+ Ile grafik görüntüleri oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="e5c9e-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="e5c9e-115">Denetiminizin benzersiz bir gösterimini kullanmak istiyorsanız, en iyi eylem, devralınan bir denetim oluşturmaktır ve bunun için özel işleme kodu yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="e5c9e-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="e5c9e-116">Ayrıntılar için bkz. [Kullanıcı çizimli denetimler](user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e5c9e-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c9e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5c9e-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="e5c9e-118">Kullanıcı Çizimli Denetimler</span><span class="sxs-lookup"><span data-stu-id="e5c9e-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="e5c9e-119">Nasıl yapılır: Çizim için grafik nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5c9e-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="e5c9e-120">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="e5c9e-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
