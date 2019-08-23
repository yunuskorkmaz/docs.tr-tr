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
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="a4df1-102">Nasıl yapılır: Bir Kısayol Menüsünü Windows Forms NotifyIcon Bileşeniyle İlişkilendirme</span><span class="sxs-lookup"><span data-stu-id="a4df1-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
> <span data-ttu-id="a4df1-103"><xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> , Ve '<xref:System.Windows.Forms.ContextMenuStrip> i önceki sürümlerin ve denetimlerine değiştirebilir ve bunları değiştirip, ve ' ı seçerseniz hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="a4df1-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="a4df1-104"><xref:System.Windows.Forms.NotifyIcon> Bileşen, görev çubuğunun durum bildirim alanında bir simge görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4df1-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="a4df1-105">Uygulamalar genellikle bu simgeye sağ tıklayıp temsil ettiği uygulamaya komutları göndermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4df1-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="a4df1-106">Bileşeni bileşeniyle ilişkilendirerek <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.NotifyIcon> , uygulamalarınıza bu işlevselliği ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4df1-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4df1-107">Görev <xref:System.Windows.Forms.NotifyIcon> çubuğunda bileşenin bir örneğini görüntülerken uygulamanızın başlangıçta simge durumuna küçültülmesini istiyorsanız, ana <xref:System.Windows.Forms.Form.WindowState%2A> formun özelliğini <xref:System.Windows.Forms.NotifyIcon> olarak <xref:System.Windows.Forms.FormWindowState.Minimized> ayarlayın ve bileşenin <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğinin olduğundan emin olun , olarak `true`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a4df1-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="a4df1-108">Tasarım zamanında bir kısayol menüsünü NotifyIcon bileşeniyle ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="a4df1-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1. <span data-ttu-id="a4df1-109">Formunuza bir <xref:System.Windows.Forms.NotifyIcon> bileşen ekleyin ve <xref:System.Windows.Forms.NotifyIcon.Icon%2A> ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özellikleri gibi önemli özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a4df1-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="a4df1-110">Daha fazla bilgi için [nasıl yapılır: Windows Forms NotifyIcon bileşeni](app-icons-to-the-taskbar-with-wf-notifyicon.md)Ile görev çubuğuna uygulama simgeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a4df1-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2. <span data-ttu-id="a4df1-111">Windows formunuza <xref:System.Windows.Forms.ContextMenu> bir bileşen ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a4df1-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="a4df1-112">Çalışma zamanında kullanılabilir hale getirmek istediğiniz komutları temsil eden kısayol menüsüne menü öğeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a4df1-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="a4df1-113">Bu, erişim tuşları gibi bu menü öğelerine menü geliştirmeleri eklemek için de iyi bir zamandır.</span><span class="sxs-lookup"><span data-stu-id="a4df1-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3. <span data-ttu-id="a4df1-114">Bileşenin<xref:System.Windows.Forms.NotifyIcon> özelliğini <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> , eklediğiniz kısayol menüsü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a4df1-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="a4df1-115">Bu özellik ayarlandığında, görev çubuğundaki simgeye tıklandığında kısayol menüsü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a4df1-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="a4df1-116">Kısayol menüsünü programlı bir şekilde NotifyIcon bileşeniyle ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="a4df1-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1. <span data-ttu-id="a4df1-117"><xref:System.Windows.Forms.NotifyIcon> <xref:System.Windows.Forms.ContextMenu> Uygulama <xref:System.Windows.Forms.ContextMenu> ( ve<xref:System.Windows.Forms.NotifyIcon.Visible%2A>Bileşenözellikleri , için menü öğeleri için gereklidir) sınıfının ve sınıfın bir örneğini oluşturun. <xref:System.Windows.Forms.NotifyIcon> <xref:System.Windows.Forms.NotifyIcon.Icon%2A> Bileşen).</span><span class="sxs-lookup"><span data-stu-id="a4df1-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2. <span data-ttu-id="a4df1-118">Bileşenin<xref:System.Windows.Forms.NotifyIcon> özelliğini <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> , eklediğiniz kısayol menüsü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a4df1-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="a4df1-119">Bu özellik ayarlandığında, görev çubuğundaki simgeye tıklandığında kısayol menüsü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a4df1-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a4df1-120">Aşağıdaki kod örneği, temel bir menü yapısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a4df1-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="a4df1-121">Menü seçimlerini, geliştirmekte olduğunuz uygulamaya uyacak şekilde özelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4df1-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="a4df1-122">Ayrıca, bu menü öğelerinin <xref:System.Windows.Forms.MenuItem.Click> olaylarını işlemek için kod yazmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a4df1-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
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
> <span data-ttu-id="a4df1-123">Aşağıdaki deyimlerini formunuzun oluşturucusuna `contextMenu1,` ekleyerek 'ibaşlatmalısınızveşunlarıyapabilirsiniz:`notifyIcon1`</span><span class="sxs-lookup"><span data-stu-id="a4df1-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4df1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4df1-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="a4df1-125">Nasıl yapılır: Windows Forms NotifyIcon bileşeni ile görev çubuğuna uygulama simgeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="a4df1-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="a4df1-126">NotifyIcon Bileşeni</span><span class="sxs-lookup"><span data-stu-id="a4df1-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="a4df1-127">NotifyIcon Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a4df1-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
