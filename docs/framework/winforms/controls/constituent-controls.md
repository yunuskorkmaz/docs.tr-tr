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
# <a name="constituent-controls"></a>Bağlı Denetimler
Bir kullanıcı denetimini oluşturan denetimler veya bunlar adi olarak *kurucu denetimler,* özel grafik işleme söz konusu olduğunda nispeten esnek değildir. Tüm Windows Forms denetimleri kendi <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemleriyle kendi oluşturma işlemlerini işler. Bu yöntem korunduğundan, geliştirici tarafından erişilemez ve bu nedenle denetim yapıldığında yürütülmesi engellenemez. Ancak bu, kurucu denetimlerin görünümünü etkileyecek kod ekleyemeyeceğiniz anlamına gelmez. Bir olay işleyicisi eklenerek ek işleme gerçekleştirilebilir. Örneğin, bir düğme yi <xref:System.Windows.Forms.UserControl> adlı `MyButton`bir düğme yle birlikte yazdığınızı varsayalım. Kullanıcı <xref:System.Web.UI.WebControls.Button>denetiminize aşağıdakilere benzer kod eklersiniz:  
  
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
> Bazı Windows Forms denetimleri, örneğin, <xref:System.Windows.Forms.TextBox>doğrudan Windows tarafından boyanır. Bu gibi durumlarda, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntem hiçbir zaman çağrılmaz ve bu nedenle yukarıdaki örnek asla çağrılmaz.  
  
 Bu, `MyButton.Paint` olay her yürütüldİğİnde çalıştıran bir yöntem oluşturur ve böylece denetiminize ek grafik gösterimi ekler. Bunun yürütülmesini `MyButton.OnPaint`engellemediğini ve bu nedenle genellikle bir düğme yle gerçekleştirilen tüm resmin özel resminize ek olarak gerçekleştirileceğini unutmayın. GDI+ teknolojisi ve özel görüntüleme hakkında ayrıntılı bilgi için [GDI+ ile Grafik Görüntüler Oluşturma'ya](../advanced/how-to-create-graphics-objects-for-drawing.md)bakın. Denetiminizin benzersiz bir temsiline sahip olmak istiyorsanız, en iyi eylem yolunuz kalıtsal bir denetim oluşturmak ve bunun için özel işleme kodu yazmaktır. Ayrıntılar için [Bkz. Kullanıcı Tarafından Çizilmiş Denetimler.](user-drawn-controls.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [Kullanıcı Çizimli Denetimler](user-drawn-controls.md)
- [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
