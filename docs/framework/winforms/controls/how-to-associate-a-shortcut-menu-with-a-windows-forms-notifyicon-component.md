---
title: Bir kısayol menüsünü NotifyIcon bileşeniyle ilişkilendirme
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
ms.openlocfilehash: 392c04f73feaec201033ad76f9419a0e070bec70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742055"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Nasıl yapılır: Bir Kısayol Menüsünü Windows Forms NotifyIcon Bileşeniyle İlişkilendirme
> [!NOTE]
> <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> önceki sürümlerin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimlerine işlev ekleyip ekler ve bu, <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu>, hem geri uyumluluk hem de daha ileride kullanılmak üzere korunur.  
  
 <xref:System.Windows.Forms.NotifyIcon> bileşeni, görev çubuğunun durum bildirim alanında bir simge görüntüler. Uygulamalar genellikle bu simgeye sağ tıklayıp temsil ettiği uygulamaya komutları göndermenizi sağlar. <xref:System.Windows.Forms.ContextMenu> bileşenini <xref:System.Windows.Forms.NotifyIcon> bileşeniyle ilişkilendirerek uygulamalarınıza bu işlevselliği ekleyebilirsiniz.  
  
> [!NOTE]
> Görev çubuğunda <xref:System.Windows.Forms.NotifyIcon> bileşenin bir örneğini görüntülerken uygulamanızın başlangıçta simge durumuna küçültülmesini istiyorsanız, ana formun <xref:System.Windows.Forms.Form.WindowState%2A> özelliğini <xref:System.Windows.Forms.FormWindowState.Minimized> olarak ayarlayın ve <xref:System.Windows.Forms.NotifyIcon> bileşeninin <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğinin `true`olarak ayarlandığından emin olun.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Tasarım zamanında bir kısayol menüsünü NotifyIcon bileşeniyle ilişkilendirme  
  
1. Formunuza <xref:System.Windows.Forms.NotifyIcon> bileşen ekleyin ve <xref:System.Windows.Forms.NotifyIcon.Icon%2A> ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özellikleri gibi önemli özellikleri ayarlayın.  
  
     Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms NotifyIcon bileşeni Ile görev çubuğuna uygulama simgeleri ekleme](app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2. Windows formunuza bir <xref:System.Windows.Forms.ContextMenu> bileşeni ekleyin.  
  
     Çalışma zamanında kullanılabilir hale getirmek istediğiniz komutları temsil eden kısayol menüsüne menü öğeleri ekleyin. Bu, erişim tuşları gibi bu menü öğelerine menü geliştirmeleri eklemek için de iyi bir zamandır.  
  
3. <xref:System.Windows.Forms.NotifyIcon> bileşenin <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> özelliğini, eklediğiniz kısayol menüsü olarak ayarlayın.  
  
     Bu özellik ayarlandığında, görev çubuğundaki simgeye tıklandığında kısayol menüsü görüntülenir.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Kısayol menüsünü programlı bir şekilde NotifyIcon bileşeniyle ilişkilendirme  
  
1. <xref:System.Windows.Forms.NotifyIcon> sınıfının ve <xref:System.Windows.Forms.ContextMenu> sınıfının bir örneğini oluşturun (<xref:System.Windows.Forms.NotifyIcon> bileşeni için uygulama (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özellikleri, <xref:System.Windows.Forms.ContextMenu> bileşen için menü öğeleri).  
  
2. <xref:System.Windows.Forms.NotifyIcon> bileşenin <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> özelliğini, eklediğiniz kısayol menüsü olarak ayarlayın.  
  
     Bu özellik ayarlandığında, görev çubuğundaki simgeye tıklandığında kısayol menüsü görüntülenir.  
  
    > [!NOTE]
    > Aşağıdaki kod örneği, temel bir menü yapısı oluşturur. Menü seçimlerini, geliştirmekte olduğunuz uygulamaya uyacak şekilde özelleştirmeniz gerekir. Ayrıca, bu menü öğeleri için <xref:System.Windows.Forms.MenuItem.Click> olaylarını işlemek üzere kod yazmak isteyeceksiniz.  
  
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
> Aşağıdaki deyimlerini formunuzun oluşturucusuna ekleyerek yapabileceğiniz `notifyIcon1` ve `contextMenu1,` başlatmalısınız:  
  
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
