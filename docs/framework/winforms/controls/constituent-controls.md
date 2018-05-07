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
---
# <a name="constituent-controls"></a>Bağlı Denetimler
Bir kullanıcı denetimini oluşturan denetimleri veya *bağlı denetimler* özel grafikler oluşturma geldiğinde olarak ifade edilmektedir gibi göreceli olarak sabit olduğundan. Kendi işleme aracılığıyla kendi tüm Windows Forms denetimlerini işleme <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. Bu yöntem korumalı olduğundan, geliştiriciler için erişilebilir değil ve böylece denetimi boyandığında yürütülmesini önlenemeyen. Bu, ancak bağlı denetimler görünümünü etkilemek için kod ekleyemezsiniz anlamına gelmez. Ek işleme, olay işleyici ekleme tarafından gerçekleştirilebilir. Örneğin, yazma varsayalım bir <xref:System.Windows.Forms.UserControl> adlı bir düğme ile `MyButton`. Ne tarafından sağlanan ötesinde ek işleme sağlamak onlardan <xref:System.Web.UI.WebControls.Button>, kullanıcı denetiminiz aşağıdakine benzer kod ekleme:  
  
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
>  Gibi bazı Windows Forms denetimleri <xref:System.Windows.Forms.TextBox>, doğrudan Windows tarafından boyanır. Bu durumlarda, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi hiçbir zaman çağrılır ve bu nedenle yukarıdaki örnekte hiçbir zaman çağrılır.  
  
 Bu her zaman yürüten bir yöntem oluşturur `MyButton.Paint` olayını yürüten, böylelikle ek grafik gösterimi, denetimine ekleme. Bu yürütülmesi engellemez Not `MyButton.OnPaint`, ve dolayısıyla tüm genellikle bir düğme tarafından gerçekleştirilen boyama hala, özel boyama ek olarak gerçekleştirilir. GDI + teknoloji ve özel işleme hakkında daha fazla ayrıntı için bkz: [GDI + ile grafik görüntü oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md). Denetiminizi benzersiz bir gösterimini olmasını istiyorsanız, iyi davranış biçimini devralınan bir denetim oluşturmak için için özel işleme kod yazmaya ise. Ayrıntılar için bkz [User-Drawn denetimleri](../../../../docs/framework/winforms/controls/user-drawn-controls.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [Kullanıcı Çizimli Denetimler](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
