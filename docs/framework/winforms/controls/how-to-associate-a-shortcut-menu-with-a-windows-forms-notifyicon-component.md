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
ms.openlocfilehash: c0371dfb30c70bd2c4d98362abc7dc06926a5e88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527888"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>Nasıl yapılır: Bir Kısayol Menüsünü Windows Forms NotifyIcon Bileşeniyle İlişkilendirme
> [!NOTE]
>  Ancak <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> önceki sürümlerinin denetimleri <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.  
  
 <xref:System.Windows.Forms.NotifyIcon> Bileşen durumu görev çubuğu bildirim alanında bir simge görüntüler. Yaygın olarak, uygulamaların komutları temsil ettiği uygulamaya göndermek için bu simgeyi sağ sağlar. İlişkilendirerek bir <xref:System.Windows.Forms.ContextMenu> ile bileşen <xref:System.Windows.Forms.NotifyIcon> bileşeni, bu işlev, uygulamalarınızı ekleyebilirsiniz.  
  
> [!NOTE]
>  Başlangıçta örneği görüntülenirken küçültülmesine uygulamanıza istiyorsanız <xref:System.Windows.Forms.NotifyIcon> bileşenini görev çubuğunda, ayarlar ana formun <xref:System.Windows.Forms.Form.WindowState%2A> özelliğine <xref:System.Windows.Forms.FormWindowState.Minimized> ve emin <xref:System.Windows.Forms.NotifyIcon> bileşenin <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliği ayarlanmış `true`.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>Bir kısayol menüsü tasarım zamanında Notifyıcon bileşeniyle ilişkilendirme  
  
1.  Ekleme bir <xref:System.Windows.Forms.NotifyIcon> formunuza, bileşen ve önemli özellikleri ayarlamak <xref:System.Windows.Forms.NotifyIcon.Icon%2A> ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özellikleri.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms Notifyıcon bileşeniyle görev uygulama simgeleri ekleme](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).  
  
2.  Ekleme bir <xref:System.Windows.Forms.ContextMenu> Windows formunuza bileşen.  
  
     Menü öğeleri, çalışma zamanında kullanılabilir hale getirmek istediğiniz komutları temsil eden kısayol menüsü ekleyin. Erişim tuşları gibi bu menü öğeleri menü geliştirmeleri eklemek için iyi bir zamandır de budur.  
  
3.  Ayarlama <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> özelliği <xref:System.Windows.Forms.NotifyIcon> eklediğiniz kısayol menüsünün bileşeni.  
  
     Görev çubuğunda simge tıklatıldığında bu özellik kümesiyle kısayol menüsü görüntülenir.  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>Bir kısayol menüsü Notifyıcon bileşeniyle programlı olarak ilişkilendirmek için  
  
1.  Bir örneğini oluşturmak <xref:System.Windows.Forms.NotifyIcon> sınıfı ve bir <xref:System.Windows.Forms.ContextMenu> ne olursa olsun özellik ayarları uygulama için gerekli olan sınıfı (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliklerini <xref:System.Windows.Forms.NotifyIcon> bileşeni, menü öğelerinin <xref:System.Windows.Forms.ContextMenu> Bileşen).  
  
2.  Ayarlama <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> özelliği <xref:System.Windows.Forms.NotifyIcon> eklediğiniz kısayol menüsünün bileşeni.  
  
     Görev çubuğunda simge tıklatıldığında bu özellik kümesiyle kısayol menüsü görüntülenir.  
  
    > [!NOTE]
    >  Aşağıdaki kod örneğinde bir temel menü yapısı oluşturur. Menü seçenekleri, geliştirmekte olduğunuz uygulama sığması için özelleştirme yapmanız gerekir. Ayrıca, işlemek için kod yazma isteyeceksiniz <xref:System.Windows.Forms.MenuItem.Click> bu menü öğeleri için olaylar.  
  
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
>  Başlatması gerekir `notifyIcon1` ve `contextMenu1,` formunuz oluşturucuda aşağıdaki ifadeleri ekleyerek yapabilirsiniz:  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [Nasıl yapılır: Windows Forms NotifyIcon Bileşeniyle TaskBar'a Uygulama Simgeleri Ekleme](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)  
 [NotifyIcon Bileşeni](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [NotifyIcon Bileşenine Genel Bakış](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
