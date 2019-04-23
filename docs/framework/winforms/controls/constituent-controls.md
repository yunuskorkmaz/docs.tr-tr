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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224883"
---
# <a name="constituent-controls"></a>Bağlı Denetimler
Bir kullanıcı denetimi oluşturan denetimleri veya *bağlı denetimler* özel grafik işleme için geldiğinde terimiyle gösterilen gibi göreceli olarak sabit olduğundan. Tüm Windows Forms denetimleri aracılığıyla kendi kendi işleme işlemek <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. Bu yöntem korunduğundan, geliştiriciler için erişilebilir değil ve böylece denetimin boyandığında yürütülmesini önlenemeyen. Bu, ancak bağlı denetimler görünümünü etkilemek için kod eklenemiyor anlamına gelmez. Ek işleme, olay işleyici ekleme tarafından gerçekleştirilebilir. Örneğin, yazma varsayalım. bir <xref:System.Windows.Forms.UserControl> adlı bir düğme olan `MyButton`. Tarafından sağlanan ne ötesinde ek işleme sağlamak onlardan <xref:System.Web.UI.WebControls.Button>, aşağıdakine benzer şekilde kullanıcı denetiminize için kod eklersiniz:  
  
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
>  Bazı Windows Forms denetimleri, gibi <xref:System.Windows.Forms.TextBox>, doğrudan tarafından Windows boyanan. Bu durumlarda, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi asla çağrılmaz ve bu nedenle yukarıdaki örnekte asla çağrılmaz.  
  
 Bu her zaman yürüten bir metot oluşturur `MyButton.Paint` olay yürütür, böylece ek grafik gösterimi denetiminize ekleme. Bu yürütülmesini engellemez Not `MyButton.OnPaint`, ve bu nedenle tüm genellikle bir düğme tarafından gerçekleştirilen boyama yine de, özel boyama ek olarak gerçekleştirilir. GDI + teknoloji ve özel işleme hakkında daha fazla ayrıntı için bkz: [GDI + ile grafik görüntü oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md). Benzersiz bir gösterimini denetiminizin olmasını istiyorsanız, en iyi eylem planını devralınan bir denetim oluşturmak için ve bunun için özel işleme kodu yazmak için ' dir. Ayrıntılar için bkz [User-Drawn denetimleri](user-drawn-controls.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Kullanıcı Çizimli Denetimler](user-drawn-controls.md)
- [Nasıl yapılır: Çizim için grafik nesneleri oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
