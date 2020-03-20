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
ms.openlocfilehash: 2865a3d85bd56151038ee90c18d199d3a584b5d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182412"
---
# <a name="constituent-controls"></a><span data-ttu-id="04587-102">Bağlı Denetimler</span><span class="sxs-lookup"><span data-stu-id="04587-102">Constituent Controls</span></span>
<span data-ttu-id="04587-103">Bir kullanıcı denetimini oluşturan denetimler veya bunlar adi olarak *kurucu denetimler,* özel grafik işleme söz konusu olduğunda nispeten esnek değildir.</span><span class="sxs-lookup"><span data-stu-id="04587-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="04587-104">Tüm Windows Forms denetimleri kendi <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemleriyle kendi oluşturma işlemlerini işler.</span><span class="sxs-lookup"><span data-stu-id="04587-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="04587-105">Bu yöntem korunduğundan, geliştirici tarafından erişilemez ve bu nedenle denetim yapıldığında yürütülmesi engellenemez.</span><span class="sxs-lookup"><span data-stu-id="04587-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="04587-106">Ancak bu, kurucu denetimlerin görünümünü etkileyecek kod ekleyemeyeceğiniz anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="04587-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="04587-107">Bir olay işleyicisi eklenerek ek işleme gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="04587-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="04587-108">Örneğin, bir düğme yi <xref:System.Windows.Forms.UserControl> adlı `MyButton`bir düğme yle birlikte yazdığınızı varsayalım.</span><span class="sxs-lookup"><span data-stu-id="04587-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="04587-109">Kullanıcı <xref:System.Web.UI.WebControls.Button>denetiminize aşağıdakilere benzer kod eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="04587-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
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
> <span data-ttu-id="04587-110">Bazı Windows Forms denetimleri, örneğin, <xref:System.Windows.Forms.TextBox>doğrudan Windows tarafından boyanır.</span><span class="sxs-lookup"><span data-stu-id="04587-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="04587-111">Bu gibi durumlarda, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntem hiçbir zaman çağrılmaz ve bu nedenle yukarıdaki örnek asla çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="04587-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="04587-112">Bu, `MyButton.Paint` olay her yürütüldİğİnde çalıştıran bir yöntem oluşturur ve böylece denetiminize ek grafik gösterimi ekler.</span><span class="sxs-lookup"><span data-stu-id="04587-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="04587-113">Bunun yürütülmesini `MyButton.OnPaint`engellemediğini ve bu nedenle genellikle bir düğme yle gerçekleştirilen tüm resmin özel resminize ek olarak gerçekleştirileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="04587-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="04587-114">GDI+ teknolojisi ve özel görüntüleme hakkında ayrıntılı bilgi için [GDI+ ile Grafik Görüntüler Oluşturma'ya](../advanced/how-to-create-graphics-objects-for-drawing.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="04587-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="04587-115">Denetiminizin benzersiz bir temsiline sahip olmak istiyorsanız, en iyi eylem yolunuz kalıtsal bir denetim oluşturmak ve bunun için özel işleme kodu yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="04587-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="04587-116">Ayrıntılar için [Bkz. Kullanıcı Tarafından Çizilmiş Denetimler.](user-drawn-controls.md)</span><span class="sxs-lookup"><span data-stu-id="04587-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04587-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04587-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="04587-118">Kullanıcı Çizimli Denetimler</span><span class="sxs-lookup"><span data-stu-id="04587-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="04587-119">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="04587-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="04587-120">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="04587-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
