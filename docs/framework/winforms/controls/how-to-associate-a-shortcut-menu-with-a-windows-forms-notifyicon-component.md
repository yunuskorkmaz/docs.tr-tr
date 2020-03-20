---
title: Kısayol Menüsünü NotifyIcon Bileşeni ile ilişkilendirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
ms.openlocfilehash: 15a4a06726de348745e5eef03217d693db496a42
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182259"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Nasıl yapılır: Bir Kısayol Menüsünü Windows Forms NotifyIcon Bileşeniyle İlişkilendirme
> [!NOTE]
> Her <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> ne kadar ve <xref:System.Windows.Forms.MainMenu> değiştirin ve önceki sürümlerin ve <xref:System.Windows.Forms.ContextMenu> denetimleri işlevsellik ekleyin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> isterseniz hem geriye dönük uyumluluk ve gelecekteki kullanım için korunur.  
  
 Bileşen, <xref:System.Windows.Forms.NotifyIcon> görev çubuğunun durum bildirim alanında bir simge görüntüler. Genellikle, uygulamalar temsil eder uygulamaya komutgöndermek için bu simgeyi sağ tıklatmanızı sağlar. Bir <xref:System.Windows.Forms.ContextMenu> bileşeni <xref:System.Windows.Forms.NotifyIcon> bileşenle ilişkilendirerek, bu işlevselliği uygulamalarınız için ekleyebilirsiniz.  
  
> [!NOTE]
> <xref:System.Windows.Forms.NotifyIcon> Görev çubuğunda bileşenin bir örneğini görüntülerken uygulamanızın başlangıçta en aza indirilmesini istiyorsanız, ana formun <xref:System.Windows.Forms.Form.WindowState%2A> özelliğini ayarla `true` <xref:System.Windows.Forms.FormWindowState.Minimized> ve bileşenin <xref:System.Windows.Forms.NotifyIcon> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğinin '' olarak ayarlandığınızdan emin olun.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Kısayol menüsünü tasarım zamanında NotifyIcon bileşeniyle ilişkilendirmek için  
  
1. Formunuza <xref:System.Windows.Forms.NotifyIcon> bir bileşen ekleyin ve bu ve <xref:System.Windows.Forms.NotifyIcon.Icon%2A> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özellikleri gibi önemli özellikleri ayarlayın.  
  
     Daha fazla bilgi için [bkz: Windows Forms NotifyIcon Bileşeni ile Görev Çubuğu'na Uygulama Simgeleri Ekleyin.](app-icons-to-the-taskbar-with-wf-notifyicon.md)  
  
2. Windows <xref:System.Windows.Forms.ContextMenu> Form'unuza bir bileşen ekleyin.  
  
     Çalışma zamanında kullanılabilir hale getirmek istediğiniz komutları temsil eden kısayol menüsüne menü öğeleri ekleyin. Bu, erişim tuşları gibi bu menü öğelerine menü geliştirmeleri eklemek için de iyi bir zamandır.  
  
3. Bileşenin <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> özelliğini <xref:System.Windows.Forms.NotifyIcon> eklediğiniz kısayol menüsüne ayarlayın.  
  
     Bu özellik kümesiyle, görev çubuğundaki simge tıklatıldığında kısayol menüsü görüntülenir.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Kısayol menüsünü NotifyIcon bileşeniyle programlı olarak ilişkilendirmek için  
  
1. Uygulama için gerekli <xref:System.Windows.Forms.NotifyIcon> olan <xref:System.Windows.Forms.ContextMenu> özellik ayarları<xref:System.Windows.Forms.NotifyIcon.Icon%2A> (ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A> <xref:System.Windows.Forms.NotifyIcon> bileşen için özellikler, bileşen için menü öğeleri) <xref:System.Windows.Forms.ContextMenu> ile sınıfın ve sınıfın bir örneğini oluşturun.  
  
2. Bileşenin <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> özelliğini <xref:System.Windows.Forms.NotifyIcon> eklediğiniz kısayol menüsüne ayarlayın.  
  
     Bu özellik kümesiyle, görev çubuğundaki simge tıklatıldığında kısayol menüsü görüntülenir.  
  
    > [!NOTE]
    > Aşağıdaki kod örneği temel bir menü yapısı oluşturur. Menü seçeneklerini, geliştirmekte olduğunuz uygulamaya uyan kişilere göre özelleştirmeniz gerekir. Ayrıca, bu menü öğeleri için <xref:System.Windows.Forms.MenuItem.Click> olayları işlemek için kod yazmak isteyeceksiniz.  
  
    ```vb  
    Public ContextMenu1 As New ContextMenu  
    Public NotifyIcon1 As New NotifyIcon  
  
    Public Sub CreateIconMenuStructure()  
       ' Add menu items to shortcut menu.  
       ContextMenu1.MenuItems.Add("&Open Application")  
       ContextMenu1.MenuItems.Add("S&uspend Application")  
       ContextMenu1.MenuItems.Add("E&xit")  
  
       ' Set properties of NotifyIcon component.  
       NotifyIcon1.Icon = New System.Drawing.Icon _
          (System.Environment.GetFolderPath _
          (System.Environment.SpecialFolder.Personal)  _
          & "\Icon.ico")  
       NotifyIcon1.Text = "Right-click me!"  
       NotifyIcon1.Visible = True  
       NotifyIcon1.ContextMenu = ContextMenu1  
    End Sub  
    ```  
  
```csharp  
public NotifyIcon notifyIcon1 = new NotifyIcon();  
public ContextMenu contextMenu1 = new ContextMenu();  
  
public void createIconMenuStructure()  
{  
   // Add menu items to shortcut menu.  
   contextMenu1.MenuItems.Add("&Open Application");  
   contextMenu1.MenuItems.Add("S&uspend Application");  
   contextMenu1.MenuItems.Add("E&xit");  
  
   // Set properties of NotifyIcon component.  
   notifyIcon1.Icon = new System.Drawing.Icon  
      (System.Environment.GetFolderPath  
      (System.Environment.SpecialFolder.Personal)  
      + @"\Icon.ico");  
   notifyIcon1.Visible = true;  
   notifyIcon1.Text = "Right-click me!";  
   notifyIcon1.Visible = true;  
   notifyIcon1.ContextMenu = contextMenu1;  
}  
```  
  
```cpp  
public:  
   System::Windows::Forms::NotifyIcon ^ notifyIcon1;  
   System::Windows::Forms::ContextMenu ^ contextMenu1;  
  
   void createIconMenuStructure()  
   {  
      // Add menu items to shortcut menu.  
      contextMenu1->MenuItems->Add("&Open Application");  
      contextMenu1->MenuItems->Add("S&uspend Application");  
      contextMenu1->MenuItems->Add("E&xit");  
  
      // Set properties of NotifyIcon component.  
      notifyIcon1->Icon = gcnew System::Drawing::Icon  
          (String::Concat(System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::Personal),  
          "\\Icon.ico"));  
      notifyIcon1->Text = "Right-click me!";  
      notifyIcon1->Visible = true;  
      notifyIcon1->ContextMenu = contextMenu1;  
   }  
```  
  
> [!NOTE]
> Formunuzun `notifyIcon1` oluşturucusuna aşağıdaki ifadeleri ekleyerek bunu yapabileceğiniz ve `contextMenu1,` başlatmanız gerekir:  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Nasıl yapılır: Windows Forms NotifyIcon Bileşeniyle TaskBar'a Uygulama Simgeleri Ekleme](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon Bileşeni](notifyicon-component-windows-forms.md)
- [NotifyIcon Bileşenine Genel Bakış](notifyicon-component-overview-windows-forms.md)
