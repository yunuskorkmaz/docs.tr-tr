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
ms.openlocfilehash: 863726a6264f01de9f00296b4a64b9fd1bb96765
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182044"
---
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="01b66-102">OnPaint Yöntemini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="01b66-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="01b66-103">.NET Framework'de tanımlanan herhangi bir olayı geçersiz kılmak için temel adımlar aynıdır ve aşağıdaki listede özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="01b66-103">The basic steps for overriding any event defined in the .NET Framework are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="01b66-104">Devralınan bir olayı geçersiz kılmak için</span><span class="sxs-lookup"><span data-stu-id="01b66-104">To override an inherited event</span></span>  
  
1. <span data-ttu-id="01b66-105">Korumalı `On` *EventName* yöntemini geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="01b66-105">Override the protected `On`*EventName* method.</span></span>  
  
2. <span data-ttu-id="01b66-106">Kayıtlı temsilcilerin olayı alması için taban sınıfın `On` *EventName* yöntemini geçersiz kılın *EventName* yönteminden arayın. `On`</span><span class="sxs-lookup"><span data-stu-id="01b66-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="01b66-107">Her <xref:System.Windows.Forms.Control.Paint> Windows Forms denetimi devraldığı <xref:System.Windows.Forms.Control.Paint> olayı geçersiz kılmak zorundadır, çünkü olay <xref:System.Windows.Forms.Control>burada ayrıntılı olarak tartışılır.</span><span class="sxs-lookup"><span data-stu-id="01b66-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="01b66-108">Taban <xref:System.Windows.Forms.Control> sınıf, türemiş denetimin nasıl çizilmesi gerektiğini bilmez ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemde herhangi bir boyama mantığı sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="01b66-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="01b66-109"><xref:System.Windows.Forms.Control> Yöntem, <xref:System.Windows.Forms.Control.OnPaint%2A> <xref:System.Windows.Forms.Control.Paint> olayı kayıtlı olay alıcılarına gönderir.</span><span class="sxs-lookup"><span data-stu-id="01b66-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="01b66-110">Örnek üzerinde [çalıştıysanız Nasıl Yapılır: Basit Bir Windows Formlar Denetimi](how-to-develop-a-simple-windows-forms-control.md)Geliştirin, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemin geçersiz kılınması için bir örnek gördünüz.</span><span class="sxs-lookup"><span data-stu-id="01b66-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="01b66-111">Aşağıdaki kod parçası bu örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="01b66-111">The following code fragment is taken from that sample.</span></span>  
  
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
  
 <span data-ttu-id="01b66-112">Sınıf <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olay için veri içerir.</span><span class="sxs-lookup"><span data-stu-id="01b66-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="01b66-113">Aşağıdaki kodda gösterildiği gibi iki özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="01b66-113">It has two properties, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="01b66-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>boyanacak dikdörtgendir ve <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> özellik bir <xref:System.Drawing.Graphics> nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="01b66-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="01b66-115"><xref:System.Drawing?displayProperty=nameWithType> Ad alanındaki sınıflar, yeni Windows grafik kitaplığı olan GDI+'nın işlevselliğine erişim sağlayan yönetilen sınıflardır.</span><span class="sxs-lookup"><span data-stu-id="01b66-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of GDI+, the new Windows graphics library.</span></span> <span data-ttu-id="01b66-116">Nesnenin <xref:System.Drawing.Graphics> noktaları, dizeleri, çizgileri, yayları, elipsleri ve diğer birçok şekli çizme yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="01b66-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="01b66-117">Denetim, görsel <xref:System.Windows.Forms.Control.OnPaint%2A> ekranını değiştirmesi gerektiğinde yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="01b66-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="01b66-118">Bu yöntem sırayla <xref:System.Windows.Forms.Control.Paint> olayı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="01b66-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b66-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01b66-119">See also</span></span>

- [<span data-ttu-id="01b66-120">Olaylar</span><span class="sxs-lookup"><span data-stu-id="01b66-120">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="01b66-121">Windows Forms Denetimini İşleme</span><span class="sxs-lookup"><span data-stu-id="01b66-121">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)
- [<span data-ttu-id="01b66-122">Olay Tanımlama</span><span class="sxs-lookup"><span data-stu-id="01b66-122">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
