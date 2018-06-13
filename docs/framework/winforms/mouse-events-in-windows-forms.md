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
ms.openlocfilehash: cd5f87b1c1e2d32a6e7fa94dfce977c7432f7f86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541216"
---
# <a name="mouse-events-in-windows-forms"></a>Windows Forms'ta Fare Olayları
Fare girişi uyguluyorsanız, genellikle fare konumunu işaretçi ve fare düğmelerinin durumunu bilmek ister. Bu konuda ayrıntıları fare olayları bu bilgilerin nasıl alınacağını sağlar ve hangi fare tıklatma Windows Forms denetimlerindeki olaylar oluşturulur sipariş açıklanmaktadır. Liste ve tüm fare olayları açıklaması için bkz: [nasıl fare giriş çalışır Windows Forms'ta](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).  Ayrıca bkz. [olay işleyicilerine genel bakış (Windows Forms)](http://msdn.microsoft.com/library/be6fx1bb\(v=vs.110\)), [olaylara genel bakış (Windows Forms)](http://msdn.microsoft.com/library/1h12f09z\(v=vs.110\))  
  
## <a name="mouse-information"></a>Fare bilgileri  
 A <xref:System.Windows.Forms.MouseEventArgs> fare düğmesini tıklatarak ve fare hareketleri izleme ile ilgili fare olayları işleyicileri gönderilir. <xref:System.Windows.Forms.MouseEventArgs> Fare işaretçisini konumunu fare düğmelere basıldığında ve fare tekerleği olup kaydırılan istemci koordinatlarında dahil olmak üzere fareyi geçerli durumu hakkında bilgi sağlar. Birkaç fare olayları, yalnızca bildir olanlar gibi fare işaretçisini girilen veya bir denetim sınırlarının sol, gönderme bir <xref:System.EventArgs> olay işleyici ile daha fazla bilgi için.  
  
 Fare düğmeleri veya fare işaretçisini konumunu geçerli durumunu bilmek ister ve fare olayı işleme önlemek istiyorsanız, de kullanabilirsiniz, <xref:System.Windows.Forms.Control.MouseButtons%2A> ve <xref:System.Windows.Forms.Control.MousePosition%2A> özelliklerini <xref:System.Windows.Forms.Control> sınıfı. <xref:System.Windows.Forms.Control.MouseButtons%2A> hakkında şu anda fare düğmelere basıldığında bilgileri döndürür. <xref:System.Windows.Forms.Control.MousePosition%2A> Fare işaretçisini ekran koordinatları döndürür ve tarafından döndürülen değer eşdeğerdir <xref:System.Windows.Forms.Cursor.Position%2A>.  
  
## <a name="converting-between-screen-and-client-coordinates"></a>Ekran ve istemci arasında dönüştürme koordinatları  
 Bazı fare konum bilgileri istemci koordinatlarında ve bazı ekran koordinatları olarak olduğundan, bir noktayı bir koordinat sistemi dönüştürmek gerekebilir. Kolayca kullanarak bunu yapabilirsiniz <xref:System.Windows.Forms.Control.PointToClient%2A> ve <xref:System.Windows.Forms.Control.PointToScreen%2A> yöntemleri kullanılabilir <xref:System.Windows.Forms.Control> sınıfı.  
  
## <a name="standard-click-event-behavior"></a>Standart tıklatma olay davranışı  
 İşlemek istiyorsanız, fare tıklatma olayları doğru sırayla, hangi tıklatın Windows Forms denetimlerindeki olaylar oluşturulur sipariş bilmeniz gerekir. Fare düğmesini basılı ve ayrı ayrı denetimler için aşağıdaki listedeki belirtilmedikçe (hangi fare düğmesini bağımsız olarak), yayımlanan tüm Windows Forms denetimleri Yükselt olayların aynı sırayla'yi tıklatın. Aşağıdaki liste için tek fare düğmesini tıklatın başlatılan olayları sırasını göstermektedir:  
  
1.  <xref:System.Windows.Forms.Control.MouseDown> olay.  
  
2.  <xref:System.Windows.Forms.Control.Click> olay.  
  
3.  <xref:System.Windows.Forms.Control.MouseClick> olay.  
  
4.  <xref:System.Windows.Forms.Control.MouseUp> olay.  
  
 İçin bir çift fare düğmesini tıklatın başlatılan olayları sırasını aşağıdadır:  
  
1.  <xref:System.Windows.Forms.Control.MouseDown> olay.  
  
2.  <xref:System.Windows.Forms.Control.Click> olay.  
  
3.  <xref:System.Windows.Forms.Control.MouseClick> olay.  
  
4.  <xref:System.Windows.Forms.Control.MouseUp> olay.  
  
5.  <xref:System.Windows.Forms.Control.MouseDown> olay.  
  
6.  <xref:System.Windows.Forms.Control.DoubleClick> olay. (Bu, söz konusu denetim olup bağlı olarak değişebilir <xref:System.Windows.Forms.ControlStyles.StandardDoubleClick> stili biti ayarlanmış `true`. Nasıl oluşturulacağı hakkında daha fazla bilgi için bir <xref:System.Windows.Forms.ControlStyles> bit bkz <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi.)  
  
7.  <xref:System.Windows.Forms.Control.MouseDoubleClick> olay.  
  
8.  <xref:System.Windows.Forms.Control.MouseUp> olay.  
  
 Tıklama fare sırasını gösteren bir kod örneği için olayları, bkz: [nasıl yapılır: Windows Forms denetimlerindeki kullanıcı girdi olaylarını işlemek](../../../docs/framework/winforms/how-to-handle-user-input-events-in-windows-forms-controls.md).  
  
### <a name="individual-controls"></a>Tek denetimleri  
 Aşağıdaki denetimleri standart fare uymayan olay davranışını tıklatın:  
  
-   <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.ComboBox>, ve <xref:System.Windows.Forms.RadioButton> denetimleri  
  
    > [!NOTE]
    >  İçin <xref:System.Windows.Forms.ComboBox> denetim, daha sonra ayrıntılı olay davranış oluşursa düğmesi düzenleme alanı ya da bir öğe listesi içindeki kullanıcı.  
  
    -   Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sağ tıklayın: hiçbir tıklama olaylarını gerçekleşti  
  
    -   Sol çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sağ çift: hiçbir tıklama olaylarını gerçekleşti  
  
-   <xref:System.Windows.Forms.TextBox>, <xref:System.Windows.Forms.RichTextBox>, <xref:System.Windows.Forms.ListBox>, <xref:System.Windows.Forms.MaskedTextBox>, ve <xref:System.Windows.Forms.CheckedListBox> denetimleri  
  
    > [!NOTE]
    >  Kullanıcı bu denetimleri içinde herhangi bir yere tıklattığında daha sonra ayrıntılı olay davranış oluşur.  
  
    -   Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sağ tıklayın: hiçbir tıklama olaylarını gerçekleşti  
  
    -   Sol çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>, <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Sağ çift: hiçbir tıklama olaylarını gerçekleşti  
  
-   <xref:System.Windows.Forms.ListView> denetimi  
  
    > [!NOTE]
    >  Daha sonra ayrıntılı olay yalnızca kullanıcı öğelerde tıkladığında davranış <xref:System.Windows.Forms.ListView> denetim. Hiçbir olaylar tıklama denetimi başka bir yerde için oluşturulur. Daha sonra açıklanan olaylar ek olarak, var olan <xref:System.Windows.Forms.ListView.BeforeLabelEdit> ve <xref:System.Windows.Forms.ListView.AfterLabelEdit> doğrulama ile kullanmak istiyorsanız, size ilgilendirebilecek olayları <xref:System.Windows.Forms.ListView> denetim.  
  
    -   Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sağ tıklayın: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sol çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Sağ çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
-   <xref:System.Windows.Forms.TreeView> denetimi  
  
    > [!NOTE]
    >  Daha sonra ayrıntılı olay yalnızca kullanıcı öğeleri kendilerini veya öğeleri sağındaki tıkladığında davranış <xref:System.Windows.Forms.TreeView> denetim. Hiçbir olaylar tıklama denetimi başka bir yerde için oluşturulur. Bu ek olarak daha sonra açıklanan, vardır <xref:System.Windows.Forms.TreeView.BeforeCheck>, <xref:System.Windows.Forms.TreeView.BeforeSelect>, <xref:System.Windows.Forms.TreeView.BeforeLabelEdit>, <xref:System.Windows.Forms.TreeView.AfterSelect>, <xref:System.Windows.Forms.TreeView.AfterCheck>, ve <xref:System.Windows.Forms.TreeView.AfterLabelEdit> doğrulama ile kullanmak istiyorsanız, size ilgilendirebilecek olayları <xref:System.Windows.Forms.TreeView> denetimi .  
  
    -   Sol tıklama: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sağ tıklayın: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>  
  
    -   Sol çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
    -   Sağ çift: <xref:System.Windows.Forms.Control.Click>, <xref:System.Windows.Forms.Control.MouseClick>; <xref:System.Windows.Forms.Control.DoubleClick>, <xref:System.Windows.Forms.Control.MouseDoubleClick>  
  
### <a name="painting-behavior-of-toggle-controls"></a>İki durumlu denetimleri davranışını boyama  
 Geçiş denetimleri türetme denetimleri gibi <xref:System.Windows.Forms.ButtonBase> sınıfı, tıklama olayları aşağıdaki ayırıcı boyama davranış fare birlikte sahiptir:  
  
1.  Kullanıcının fare düğmesini basar.  
  
2.  Denetim basılı durumda boyar.  
  
3.  <xref:System.Windows.Forms.Control.MouseDown> Olayı oluşturulur.  
  
4.  Kullanıcının fare düğmesini serbest bırakır.  
  
5.  Denetim gerçekleştiği durumda boyar.  
  
6.  <xref:System.Windows.Forms.Control.Click> Olayı oluşturulur.  
  
7.  <xref:System.Windows.Forms.Control.MouseClick> Olayı oluşturulur.  
  
8.  <xref:System.Windows.Forms.Control.MouseUp> Olayı oluşturulur.  
  
    > [!NOTE]
    >  Kullanıcının fare düğmesini basılı olsa işaretçiyi iki durumlu düğme denetim dışında taşınırsa (fareyi hareket gibi <xref:System.Windows.Forms.Button> , basıldığında kontrol), iki durumlu düğme denetim gerçekleştiği yer boyamak durum ve yalnızca <xref:System.Windows.Forms.Control.MouseUp> olayı oluşur. <xref:System.Windows.Forms.Control.Click> Veya <xref:System.Windows.Forms.Control.MouseClick> olayları, bu durumda gerçekleşmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Windows Forms Uygulamasında Fare Girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
