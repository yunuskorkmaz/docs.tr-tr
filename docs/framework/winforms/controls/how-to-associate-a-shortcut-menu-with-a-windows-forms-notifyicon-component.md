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
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="cc75e-102">Nasıl yapılır: Bir Kısayol Menüsünü Windows Forms NotifyIcon Bileşeniyle İlişkilendirme</span><span class="sxs-lookup"><span data-stu-id="cc75e-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
> <span data-ttu-id="cc75e-103">Her <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip> ne kadar ve <xref:System.Windows.Forms.MainMenu> değiştirin ve önceki sürümlerin ve <xref:System.Windows.Forms.ContextMenu> denetimleri işlevsellik ekleyin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> isterseniz hem geriye dönük uyumluluk ve gelecekteki kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="cc75e-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="cc75e-104">Bileşen, <xref:System.Windows.Forms.NotifyIcon> görev çubuğunun durum bildirim alanında bir simge görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cc75e-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="cc75e-105">Genellikle, uygulamalar temsil eder uygulamaya komutgöndermek için bu simgeyi sağ tıklatmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc75e-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="cc75e-106">Bir <xref:System.Windows.Forms.ContextMenu> bileşeni <xref:System.Windows.Forms.NotifyIcon> bileşenle ilişkilendirerek, bu işlevselliği uygulamalarınız için ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc75e-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc75e-107"><xref:System.Windows.Forms.NotifyIcon> Görev çubuğunda bileşenin bir örneğini görüntülerken uygulamanızın başlangıçta en aza indirilmesini istiyorsanız, ana formun <xref:System.Windows.Forms.Form.WindowState%2A> özelliğini ayarla `true` <xref:System.Windows.Forms.FormWindowState.Minimized> ve bileşenin <xref:System.Windows.Forms.NotifyIcon> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğinin '' olarak ayarlandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cc75e-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="cc75e-108">Kısayol menüsünü tasarım zamanında NotifyIcon bileşeniyle ilişkilendirmek için</span><span class="sxs-lookup"><span data-stu-id="cc75e-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1. <span data-ttu-id="cc75e-109">Formunuza <xref:System.Windows.Forms.NotifyIcon> bir bileşen ekleyin ve bu ve <xref:System.Windows.Forms.NotifyIcon.Icon%2A> <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özellikleri gibi önemli özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cc75e-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="cc75e-110">Daha fazla bilgi için [bkz: Windows Forms NotifyIcon Bileşeni ile Görev Çubuğu'na Uygulama Simgeleri Ekleyin.](app-icons-to-the-taskbar-with-wf-notifyicon.md)</span><span class="sxs-lookup"><span data-stu-id="cc75e-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2. <span data-ttu-id="cc75e-111">Windows <xref:System.Windows.Forms.ContextMenu> Form'unuza bir bileşen ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cc75e-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="cc75e-112">Çalışma zamanında kullanılabilir hale getirmek istediğiniz komutları temsil eden kısayol menüsüne menü öğeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cc75e-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="cc75e-113">Bu, erişim tuşları gibi bu menü öğelerine menü geliştirmeleri eklemek için de iyi bir zamandır.</span><span class="sxs-lookup"><span data-stu-id="cc75e-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3. <span data-ttu-id="cc75e-114">Bileşenin <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> özelliğini <xref:System.Windows.Forms.NotifyIcon> eklediğiniz kısayol menüsüne ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cc75e-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="cc75e-115">Bu özellik kümesiyle, görev çubuğundaki simge tıklatıldığında kısayol menüsü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cc75e-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="cc75e-116">Kısayol menüsünü NotifyIcon bileşeniyle programlı olarak ilişkilendirmek için</span><span class="sxs-lookup"><span data-stu-id="cc75e-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1. <span data-ttu-id="cc75e-117">Uygulama için gerekli <xref:System.Windows.Forms.NotifyIcon> olan <xref:System.Windows.Forms.ContextMenu> özellik ayarları<xref:System.Windows.Forms.NotifyIcon.Icon%2A> (ve <xref:System.Windows.Forms.NotifyIcon.Visible%2A> <xref:System.Windows.Forms.NotifyIcon> bileşen için özellikler, bileşen için menü öğeleri) <xref:System.Windows.Forms.ContextMenu> ile sınıfın ve sınıfın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cc75e-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2. <span data-ttu-id="cc75e-118">Bileşenin <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> özelliğini <xref:System.Windows.Forms.NotifyIcon> eklediğiniz kısayol menüsüne ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cc75e-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="cc75e-119">Bu özellik kümesiyle, görev çubuğundaki simge tıklatıldığında kısayol menüsü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cc75e-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cc75e-120">Aşağıdaki kod örneği temel bir menü yapısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cc75e-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="cc75e-121">Menü seçeneklerini, geliştirmekte olduğunuz uygulamaya uyan kişilere göre özelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc75e-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="cc75e-122">Ayrıca, bu menü öğeleri için <xref:System.Windows.Forms.MenuItem.Click> olayları işlemek için kod yazmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="cc75e-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
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
> <span data-ttu-id="cc75e-123">Formunuzun `notifyIcon1` oluşturucusuna aşağıdaki ifadeleri ekleyerek bunu yapabileceğiniz ve `contextMenu1,` başlatmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="cc75e-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc75e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc75e-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="cc75e-125">Nasıl yapılır: Windows Forms NotifyIcon Bileşeniyle TaskBar'a Uygulama Simgeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="cc75e-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="cc75e-126">NotifyIcon Bileşeni</span><span class="sxs-lookup"><span data-stu-id="cc75e-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="cc75e-127">NotifyIcon Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cc75e-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
