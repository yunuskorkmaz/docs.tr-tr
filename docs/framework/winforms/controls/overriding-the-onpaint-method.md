---
title: OnPaint Yöntemini Geçersiz Kılma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
ms.openlocfilehash: fbc0a82f82afcc59384246b58437d521d56d708b
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46005615"
---
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="1aea6-102">OnPaint Yöntemini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="1aea6-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="1aea6-103">Tanımlanan herhangi bir olayı geçersiz kılmak için temel adımlar [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aynıdır ve aşağıda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1aea6-103">The basic steps for overriding any event defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="1aea6-104">Devralınan bir olayı geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="1aea6-104">To override an inherited event</span></span>  
  
1.  <span data-ttu-id="1aea6-105">Geçersiz kılma korumalı `On` *EventName* yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1aea6-105">Override the protected `On`*EventName* method.</span></span>  
  
2.  <span data-ttu-id="1aea6-106">Çağrı `On` *EventName* yöntemi geçersiz kılınan taban sınıfından `On` *EventName* yöntemi, temsilcileri kayıtlı için olay alırsınız.</span><span class="sxs-lookup"><span data-stu-id="1aea6-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="1aea6-107"><xref:System.Windows.Forms.Control.Paint> Olay her Windows Forms denetimi geçersiz kılmanız gerekir çünkü burada ayrıntılı olarak ele <xref:System.Windows.Forms.Control.Paint> devraldığı olay <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="1aea6-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="1aea6-108">Temel <xref:System.Windows.Forms.Control> sınıfı türetilmiş bir denetimi nasıl çizilmesi gerektiğinde bilmeyen ve bir boyama mantığında sağlamaz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1aea6-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="1aea6-109"><xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemi <xref:System.Windows.Forms.Control> yalnızca gönderir <xref:System.Windows.Forms.Control.Paint> kayıtlı olay alıcıları için olay.</span><span class="sxs-lookup"><span data-stu-id="1aea6-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="1aea6-110">Örnekte aracılığıyla yaradıysa [nasıl yapılır: basit bir Windows Forms denetimi geliştirme](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), geçersiz kılma örneği gördünüz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1aea6-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="1aea6-111">Aşağıdaki kod parçası bu örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="1aea6-111">The following code fragment is taken from that sample.</span></span>  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class   
```  
  
```csharp  
public class FirstControl : Control {  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <span data-ttu-id="1aea6-112"><xref:System.Windows.Forms.PaintEventArgs> Sınıfı içeren verileri <xref:System.Windows.Forms.Control.Paint> olay.</span><span class="sxs-lookup"><span data-stu-id="1aea6-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="1aea6-113">Aşağıdaki kodda gösterildiği gibi iki özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1aea6-113">It has two properties, as shown in the following code.</span></span>  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property   
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <span data-ttu-id="1aea6-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> boyanacak, dikdörtgen ve <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> özelliği başvurduğu bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="1aea6-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="1aea6-115">Sınıflarda <xref:System.Drawing?displayProperty=nameWithType> ad alanı yönetilen işlevselliğini erişimi sağlayan sınıflar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], yeni bir Windows grafik kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="1aea6-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], the new Windows graphics library.</span></span> <span data-ttu-id="1aea6-116"><xref:System.Drawing.Graphics> Nesne noktaları, dizeler, çizgiler, yaylar, üç nokta ve birçok diğer şekiller çizmek için yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="1aea6-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="1aea6-117">Bir denetim çağırır, <xref:System.Windows.Forms.Control.OnPaint%2A> görsel görünümünü değiştirmek gerektiğinde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1aea6-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="1aea6-118">Bu yöntem sırayla başlatır <xref:System.Windows.Forms.Control.Paint> olay.</span><span class="sxs-lookup"><span data-stu-id="1aea6-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aea6-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1aea6-119">See Also</span></span>  
 [<span data-ttu-id="1aea6-120">Olaylar</span><span class="sxs-lookup"><span data-stu-id="1aea6-120">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="1aea6-121">Windows Forms Denetimini İşleme</span><span class="sxs-lookup"><span data-stu-id="1aea6-121">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [<span data-ttu-id="1aea6-122">Olay Tanımlama</span><span class="sxs-lookup"><span data-stu-id="1aea6-122">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
