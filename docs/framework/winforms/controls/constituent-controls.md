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
# <a name="constituent-controls"></a>Bağlı Denetimler
Bir kullanıcı denetimini oluşturan denetimler veya bir ekip *denetimleri* , özel grafik işleme geldiğinde görece güvenilir bir şekilde çalışır. Tüm Windows Forms denetimleri kendi kendi <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemleri aracılığıyla kendi işlemesini işler. Bu yöntem korunduğundan, geliştirici tarafından erişilebilir değildir ve bu nedenle denetim boyandığında yürütülmesi önlenemez. Ancak bu, bileşen denetimlerinin görünümünü etkilemek için kod ekleyemayacağınız anlamına gelmez. Ek işleme, bir olay işleyicisi eklenerek gerçekleştirilebilir. Örneğin, adlı <xref:System.Windows.Forms.UserControl> `MyButton`bir düğmeyle bir yazdığınızı varsayalım. Tarafından sağlananlar dışında ek işleme sağlamak istiyorsanız <xref:System.Web.UI.WebControls.Button>, Kullanıcı denetiminin aşağıdakine benzer şekilde kod eklersiniz:  
  
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
> Gibi bazı Windows Forms denetimleri <xref:System.Windows.Forms.TextBox>, doğrudan Windows tarafından boyanmıştır. Bu örneklerde, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi hiçbir şekilde çağrılmaz ve bu nedenle yukarıdaki örnek hiçbir şekilde çağrılmayacaktır.  
  
 Bu, `MyButton.Paint` olay her çalıştırıldığında çalıştırılan bir yöntem oluşturur ve bu sayede denetimenizde ek grafik gösterimi ekler. Bunun yürütülmesini `MyButton.OnPaint`engellemez ve bu nedenle genellikle bir düğme tarafından gerçekleştirilen tüm boyama, özel boyamaya ek olarak yine de gerçekleştirilir. GDI+ teknolojisi ve özel işleme hakkında daha fazla bilgi için bkz. [GDI+ Ile grafik görüntüleri oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md). Denetiminizin benzersiz bir gösterimini kullanmak istiyorsanız, en iyi eylem, devralınan bir denetim oluşturmaktır ve bunun için özel işleme kodu yazmaktır. Ayrıntılar için bkz. [Kullanıcı çizimli denetimler](user-drawn-controls.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Kullanıcı Çizimli Denetimler](user-drawn-controls.md)
- [Nasıl yapılır: Çizim için grafik nesneleri oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
