---
title: 'Nasıl yapılır: Bir Kısayol Menüsünü Windows Forms NotifyIcon Bileşeniyle İlişkilendirme'
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
ms.openlocfilehash: bf5602d0526fdd97f0cc14382339095a793f13c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922763"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Nasıl yapılır: Bir Kısayol Menüsünü Windows Forms NotifyIcon Bileşeniyle İlişkilendirme
> [!NOTE]
> <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> , Ve '<xref:System.Windows.Forms.ContextMenuStrip> i önceki sürümlerin ve denetimlerine değiştirebilir ve bunları değiştirip, ve ' ı seçerseniz hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. <xref:System.Windows.Forms.MenuStrip>  
  
 <xref:System.Windows.Forms.NotifyIcon> Bileşen, görev çubuğunun durum bildirim alanında bir simge görüntüler. Uygulamalar genellikle bu simgeye sağ tıklayıp temsil ettiği uygulamaya komutları göndermenizi sağlar. Bileşeni bileşeniyle ilişkilendirerek <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.NotifyIcon> , uygulamalarınıza bu işlevselliği ekleyebilirsiniz.  
  
> [!NOTE]
> Görev <xref:System.Windows.Forms.NotifyIcon> çubuğunda bileşenin bir örneğini görüntülerken uygulamanızın başlangıçta simge durumuna küçültülmesini istiyorsanız, ana <xref:System.Windows.Forms.Form.WindowState%2A> formun özelliğini <xref:System.Windows.Forms.NotifyIcon> olarak <xref:System.Windows.Forms.FormWindowState.Minimized> ayarlayın ve bileşenin <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğinin olduğundan emin olun , olarak `true`ayarlanır.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Tasarım zamanında bir kısayol menüsünü NotifyIcon bileşeniyle ilişkilendirme  
  
1. Formunuza bir <xref:System.Windows.Forms.NotifyIcon> bileşen ekleyin ve <xref:System.Windows.Forms.NotifyIcon.Icon%2A> ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özellikleri gibi önemli özellikleri ayarlayın.  
  
     Daha fazla bilgi için [nasıl yapılır: Windows Forms NotifyIcon bileşeni](app-icons-to-the-taskbar-with-wf-notifyicon.md)Ile görev çubuğuna uygulama simgeleri ekleyin.  
  
2. Windows formunuza <xref:System.Windows.Forms.ContextMenu> bir bileşen ekleyin.  
  
     Çalışma zamanında kullanılabilir hale getirmek istediğiniz komutları temsil eden kısayol menüsüne menü öğeleri ekleyin. Bu, erişim tuşları gibi bu menü öğelerine menü geliştirmeleri eklemek için de iyi bir zamandır.  
  
3. Bileşenin<xref:System.Windows.Forms.NotifyIcon> özelliğini <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> , eklediğiniz kısayol menüsü olarak ayarlayın.  
  
     Bu özellik ayarlandığında, görev çubuğundaki simgeye tıklandığında kısayol menüsü görüntülenir.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Kısayol menüsünü programlı bir şekilde NotifyIcon bileşeniyle ilişkilendirme  
  
1. <xref:System.Windows.Forms.NotifyIcon> <xref:System.Windows.Forms.ContextMenu> Uygulama <xref:System.Windows.Forms.ContextMenu> ( ve<xref:System.Windows.Forms.NotifyIcon.Visible%2A>Bileşenözellikleri , için menü öğeleri için gereklidir) sınıfının ve sınıfın bir örneğini oluşturun. <xref:System.Windows.Forms.NotifyIcon> <xref:System.Windows.Forms.NotifyIcon.Icon%2A> Bileşen).  
  
2. Bileşenin<xref:System.Windows.Forms.NotifyIcon> özelliğini <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> , eklediğiniz kısayol menüsü olarak ayarlayın.  
  
     Bu özellik ayarlandığında, görev çubuğundaki simgeye tıklandığında kısayol menüsü görüntülenir.  
  
    > [!NOTE]
    > Aşağıdaki kod örneği, temel bir menü yapısı oluşturur. Menü seçimlerini, geliştirmekte olduğunuz uygulamaya uyacak şekilde özelleştirmeniz gerekir. Ayrıca, bu menü öğelerinin <xref:System.Windows.Forms.MenuItem.Click> olaylarını işlemek için kod yazmak isteyeceksiniz.  
  
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
> Aşağıdaki deyimlerini formunuzun oluşturucusuna `contextMenu1,` ekleyerek 'ibaşlatmalısınızveşunlarıyapabilirsiniz:`notifyIcon1`  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [Nasıl yapılır: Windows Forms NotifyIcon bileşeni ile görev çubuğuna uygulama simgeleri ekleme](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon Bileşeni](notifyicon-component-windows-forms.md)
- [NotifyIcon Bileşenine Genel Bakış](notifyicon-component-overview-windows-forms.md)
