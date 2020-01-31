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
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="06670-102">Nasıl yapılır: Bir Kısayol Menüsünü Windows Forms NotifyIcon Bileşeniyle İlişkilendirme</span><span class="sxs-lookup"><span data-stu-id="06670-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
> <span data-ttu-id="06670-103"><xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> önceki sürümlerin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimlerine işlev ekleyip ekler ve bu, <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu>, hem geri uyumluluk hem de daha ileride kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="06670-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="06670-104"><xref:System.Windows.Forms.NotifyIcon> bileşeni, görev çubuğunun durum bildirim alanında bir simge görüntüler.</span><span class="sxs-lookup"><span data-stu-id="06670-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="06670-105">Uygulamalar genellikle bu simgeye sağ tıklayıp temsil ettiği uygulamaya komutları göndermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="06670-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="06670-106"><xref:System.Windows.Forms.ContextMenu> bileşenini <xref:System.Windows.Forms.NotifyIcon> bileşeniyle ilişkilendirerek uygulamalarınıza bu işlevselliği ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06670-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06670-107">Görev çubuğunda <xref:System.Windows.Forms.NotifyIcon> bileşenin bir örneğini görüntülerken uygulamanızın başlangıçta simge durumuna küçültülmesini istiyorsanız, ana formun <xref:System.Windows.Forms.Form.WindowState%2A> özelliğini <xref:System.Windows.Forms.FormWindowState.Minimized> olarak ayarlayın ve <xref:System.Windows.Forms.NotifyIcon> bileşeninin <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğinin `true`olarak ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="06670-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="06670-108">Tasarım zamanında bir kısayol menüsünü NotifyIcon bileşeniyle ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="06670-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1. <span data-ttu-id="06670-109">Formunuza <xref:System.Windows.Forms.NotifyIcon> bileşen ekleyin ve <xref:System.Windows.Forms.NotifyIcon.Icon%2A> ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özellikleri gibi önemli özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="06670-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="06670-110">Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms NotifyIcon bileşeni Ile görev çubuğuna uygulama simgeleri ekleme](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="06670-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2. <span data-ttu-id="06670-111">Windows formunuza bir <xref:System.Windows.Forms.ContextMenu> bileşeni ekleyin.</span><span class="sxs-lookup"><span data-stu-id="06670-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="06670-112">Çalışma zamanında kullanılabilir hale getirmek istediğiniz komutları temsil eden kısayol menüsüne menü öğeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="06670-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="06670-113">Bu, erişim tuşları gibi bu menü öğelerine menü geliştirmeleri eklemek için de iyi bir zamandır.</span><span class="sxs-lookup"><span data-stu-id="06670-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3. <span data-ttu-id="06670-114"><xref:System.Windows.Forms.NotifyIcon> bileşenin <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> özelliğini, eklediğiniz kısayol menüsü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="06670-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="06670-115">Bu özellik ayarlandığında, görev çubuğundaki simgeye tıklandığında kısayol menüsü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="06670-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="06670-116">Kısayol menüsünü programlı bir şekilde NotifyIcon bileşeniyle ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="06670-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1. <span data-ttu-id="06670-117"><xref:System.Windows.Forms.NotifyIcon> sınıfının ve <xref:System.Windows.Forms.ContextMenu> sınıfının bir örneğini oluşturun (<xref:System.Windows.Forms.NotifyIcon> bileşeni için uygulama (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özellikleri, <xref:System.Windows.Forms.ContextMenu> bileşen için menü öğeleri).</span><span class="sxs-lookup"><span data-stu-id="06670-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2. <span data-ttu-id="06670-118"><xref:System.Windows.Forms.NotifyIcon> bileşenin <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> özelliğini, eklediğiniz kısayol menüsü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="06670-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="06670-119">Bu özellik ayarlandığında, görev çubuğundaki simgeye tıklandığında kısayol menüsü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="06670-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="06670-120">Aşağıdaki kod örneği, temel bir menü yapısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06670-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="06670-121">Menü seçimlerini, geliştirmekte olduğunuz uygulamaya uyacak şekilde özelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="06670-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="06670-122">Ayrıca, bu menü öğeleri için <xref:System.Windows.Forms.MenuItem.Click> olaylarını işlemek üzere kod yazmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="06670-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
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
> <span data-ttu-id="06670-123">Aşağıdaki deyimlerini formunuzun oluşturucusuna ekleyerek yapabileceğiniz `notifyIcon1` ve `contextMenu1,` başlatmalısınız:</span><span class="sxs-lookup"><span data-stu-id="06670-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="06670-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06670-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="06670-125">Nasıl yapılır: Windows Forms NotifyIcon Bileşeniyle TaskBar'a Uygulama Simgeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="06670-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="06670-126">NotifyIcon Bileşeni</span><span class="sxs-lookup"><span data-stu-id="06670-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="06670-127">NotifyIcon Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="06670-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
