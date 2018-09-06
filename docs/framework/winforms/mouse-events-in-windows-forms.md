---
title: Windows Forms'ta Fare Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- MouseLeave event [Windows Forms]
- events [Windows Forms], mouse
- Click event [Windows Forms], raising order
- Windows Forms controls, click events
- MouseDoubleClick event [Windows Forms]
- MouseEnter event [Windows Forms]
- MouseHover event [Windows Forms]
- MouseDown event [Windows Forms]
- MouseClick event [Windows Forms]
- MouseMove event [Windows Forms]
- mouse [Windows Forms], events
- MouseUp event
ms.assetid: 8cf0070d-793b-4876-b09e-d20d28280fab
ms.openlocfilehash: 6f457756d2266a84c4f241a1cea167af194d8b81
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864514"
---
# <a name="mouse-events-in-windows-forms"></a>Windows Forms'ta Fare Olayları
Fare girişi işlediğinizde, genellikle işaretçi ve farenin düğme durumunu fare konumunu bilmek ister. Bu konu, fare olayları bu bilgiler edinme hakkında ayrıntılı bilgi sağlar ve Windows Forms denetimlerinde tetiklenen hangi fare tıklatın olayları siparişi açıklar. Bir listesi ve açıklamaları tüm fare olayları için bkz. [nasıl Windows Forms'ta fare girdisi çalışır](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).  Ayrıca bkz: [olay işleyicilerine genel bakış (Windows Forms)](https://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [olaylara genel bakış (Windows Forms)](https://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))  
  
## <a name="mouse-information"></a>Fare bilgileri  
 A <xref:System.Windows.Forms.MouseEventArgs> fare etkinliklerinin bir fare düğmesine tıklamak ve fare hareketlerini izleme ile ilgili işleyicileri gönderilir. <xref:System.Windows.Forms.MouseEventArgs> Fare işaretçisi konumunu fare düğmesini basılı ve fare tekerleğini olup kaydırılan istemci koordinatlarında dahil olmak üzere fareyi geçerli durumu hakkında bilgi sağlar. Birkaç fare olayları, yalnızca bildir olanlar gibi fare işaretçisi girilen veya denetimin sınırları sol, gönderme bir <xref:System.EventArgs> olay işleyicisi ile daha fazla bilgi için.  
  
 Geçerli durumunu fare düğmesini veya fare işaretçisi konumunu bilmek istiyorsunuz ve bir fare olayına işleme önlemek istiyorsanız, ayrıca <xref:System.Windows.Forms.Control.MouseButtons%2A> ve <xref:System.Windows.Forms.Control.MousePosition%2A> özelliklerini <xref:System.Windows.Forms.Control> sınıfı. <xref:System.Windows.Forms.Control.MouseButtons%2A> hangi şu anda fare düğmelere basıldığında bilgileri döndürür. <xref:System.Windows.Forms.Control.MousePosition%2A> Fare işaretçisi ekran koordinatlarını döndürür ve tarafından döndürülen değere eşdeğer bir gruba <xref:System.Windows.Forms.Cursor.Position%2A>.  
  
## <a name="converting-between-screen-and-client-coordinates"></a>Ekran ve istemci arasında dönüştürme koordinatları  
 Bazı fare konum bilgilerini istemci koordinatlarını ve bazı ekran koordinatlarında olduğundan, bir nokta bir koordinat sistemini dönüştürmek gerekebilir. Kolayca kullanarak bunu yapabilirsiniz <xref:System.Windows.Forms.Control.PointToClient%2A> ve <xref:System.Windows.Forms.Control.PointToScreen%2A> yöntemleri üzerinde kullanılabilir <xref:System.Windows.Forms.Control> sınıfı.  
  
## <a name="standard-click-event-behavior"></a>Standart tıklatma olay davranışı  
 Kullanmak istediğiniz fare tıklatın doğru sırada olayları, Windows Forms denetimlerinde tetiklenen hangi tıklama olayları sırasını bilmeniz gerekir. Bir fare düğmesi basılı olduğunda ve tek tek denetimler için aşağıdaki listede belirtilmedikçe (hangi fare düğmesi bağımsız olarak), yayımlanan olayların aynı sırayla tüm Windows Formları denetimleri Yükselt'e tıklayın. Aşağıdaki liste için tek fare düğmesini tıklatın yükseltilmiş olayların sırası gösterir:  
  
1.  <xref:System.Windows.Forms.Control.MouseDown> olay.  
  
2.  <xref:System.Windows.Forms.Control.Click> olay.  
  
3.  <xref:System.Windows.Forms.Control.MouseClick> olay.  
  
4.  <xref:System.Windows.Forms.Control.MouseUp> olay.  
  
 İçin bir fare düğmesine çift tıklayın yükseltilmiş olayların sırası aşağıda verilmiştir:  
  
1.  <xref:System.Windows.Forms.Control.MouseDown> olay.  
  
2.  <xref:System.Windows.Forms.Control.Click> olay.  
  
3.  <xref:System.Windows.Forms.Control.MouseClick> olay.  
  
4.  <xref:System.Windows.Forms.Control.MouseUp> olay.  
  
5.  <xref:System.Windows.Forms.Control.MouseDown> olay.  
  
6.  <xref:System.Windows.Forms.Control.DoubleClick> olay. (Bu, söz konusu denetim olup bağlı olarak değişebilir <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> stili biti ayarlanmış `true`. Nasıl ayarlanacağı hakkında daha fazla bilgi için bir <xref:System.Windows.Forms.ControlStyles> bit için bkz: <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi.)  
  
7.  <xref:System.Windows.Forms.Control.MouseDoubleClick> olay.  
  
8.  <xref:System.Windows.Forms.Control.MouseUp> olay.  
  
 Tıklama olayları fare düzenini gösteren bir kod örneği için bkz: [nasıl yapılır: Windows Forms denetimlerinde kullanıcı giriş olaylarını işlemek](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md).  
  
### <a name="individual-controls"></a>Tek denetimleri  
 Aşağıdaki denetimler için standart fare uymayan olay davranışı:  
  
-   <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, ve <xref:System.Windows.Forms.RadioButton> denetimleri  
  
    > [!NOTE]
    >  İçin <xref:System.Windows.Forms.ComboBox> denetim daha sonra ayrıntılı olay davranış oluşur kullanıcı düzenleme alanı, düğmeyi veya bir öğe listede tıklarsa.  
  
    -   Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sağ tıklayın: yükseltilmiş click olayı yok  
  
    -   Sol çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sağa çift: yükseltilmiş click olayı yok  
  
-   <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, ve <xref:System.Windows.Forms.CheckedListBox> denetimleri  
  
    > [!NOTE]
    >  Daha sonra ayrıntılı olay davranışı, kullanıcı bu denetimleri içinde herhangi bir yere tıkladığında gerçekleşir.  
  
    -   Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sağ tıklayın: yükseltilmiş click olayı yok  
  
    -   Sol çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Sağa çift: yükseltilmiş click olayı yok  
  
-   <xref:System.Windows.Forms.ListView> Denetimi  
  
    > [!NOTE]
    >  Daha sonra ayrıntılı olay yalnızca kullanıcı öğelerde tıkladığında davranış <xref:System.Windows.Forms.ListView> denetimi. Tıklama denetimi başka bir yerde için hiçbir olay harekete geçirilir. Daha sonra açıklanan olaylarına ilaveten vardır <xref:System.Windows.Forms.ListView.BeforeLabelEdit> ve <xref:System.Windows.Forms.ListView.AfterLabelEdit> ile doğrulama kullanmak istiyorsanız, ilginizi çekebilecek olayları <xref:System.Windows.Forms.ListView> denetimi.  
  
    -   Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sağ tıklayın: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sol çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Sağa çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
-   <xref:System.Windows.Forms.TreeView> Denetimi  
  
    > [!NOTE]
    >  Daha sonra ayrıntılı olay yalnızca kullanıcı öğeleri veya öğeleri sağındaki tıkladığında davranış <xref:System.Windows.Forms.TreeView> denetimi. Tıklama denetimi başka bir yerde için hiçbir olay harekete geçirilir. Açıklanana yanı sıra daha sonra vardır <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, ve <xref:System.Windows.Forms.TreeView.AfterLabelEdit> ile doğrulama kullanmak istiyorsanız, ilginizi çekebilecek olayları <xref:System.Windows.Forms.TreeView> denetimi .  
  
    -   Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sağ tıklayın: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sol çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Sağa çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
### <a name="painting-behavior-of-toggle-controls"></a>İki durumlu denetimleri davranışını boyama  
 Geçiş türetme denetimleri gibi denetimleri <xref:System.Windows.Forms.ButtonBase> sınıfı, tıklama olayları aşağıdaki farklı boyama davranış fare ile birlikte sahiptir:  
  
1.  Kullanıcı fare düğmesine bastığında.  
  
2.  Basılan durumda denetimi boyar.  
  
3.  <xref:System.Windows.Forms.Control.MouseDown> Olayı oluşturulur.  
  
4.  Kullanıcı, fare düğmesini serbest bırakır.  
  
5.  Yükseltilmiş durumunda denetimi boyar.  
  
6.  <xref:System.Windows.Forms.Control.Click> Olayı oluşturulur.  
  
7.  <xref:System.Windows.Forms.Control.MouseClick> Olayı oluşturulur.  
  
8.  <xref:System.Windows.Forms.Control.MouseUp> Olayı oluşturulur.  
  
    > [!NOTE]
    >  Kullanıcı fare düğmesini basılı durumdayken işaretçiyi iki durumlu denetimin dışına taşınırsa (fareyi hareket gibi <xref:System.Windows.Forms.Button> , basılı durumdayken denetim), iki durumlu denetimin yükseltilmiş boyama durum ve yalnızca <xref:System.Windows.Forms.Control.MouseUp> olayı oluşur. <xref:System.Windows.Forms.Control.Click> Veya <xref:System.Windows.Forms.Control.MouseClick> olayları, bu durumda gerçekleşmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Windows Forms Uygulamasında Fare Girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
