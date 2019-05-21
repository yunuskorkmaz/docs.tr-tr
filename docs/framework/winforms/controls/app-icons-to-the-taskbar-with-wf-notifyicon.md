---
title: "Nasıl yapılır: Windows Forms NotifyIcon Bileşeniyle TaskBar'a Uygulama Simgeleri Ekleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
ms.openlocfilehash: 05b6f300afea4671c1a847b116b378514ecb8b56
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959510"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="327ba-102">Nasıl yapılır: Windows Forms NotifyIcon Bileşeniyle TaskBar'a Uygulama Simgeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="327ba-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>

<span data-ttu-id="327ba-103">Windows Forms <xref:System.Windows.Forms.NotifyIcon> bileşen durumu görev çubuğu bildirim alanında tek bir simge görüntüler.</span><span class="sxs-lookup"><span data-stu-id="327ba-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="327ba-104">Durum alanında birden fazla simgeleri göstermek için birden çok sahip <xref:System.Windows.Forms.NotifyIcon> formunuzdaki bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="327ba-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="327ba-105">Bir denetim için görüntülenen simgenin ayarlamak için kullanın <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="327ba-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="327ba-106">Ayrıca kod yazabileceğiniz <xref:System.Windows.Forms.NotifyIcon.DoubleClick> kullanıcı simgesine tıkladığında bu şey için olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="327ba-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="327ba-107">Örneğin, bir iletişim kutusu kullanıcının simgesiyle gösterilen arka plan işlemi yapılandırmak görünür yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="327ba-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>

> [!NOTE]
> <span data-ttu-id="327ba-108"><xref:System.Windows.Forms.NotifyIcon> Çeşit durumundaki bir değişiklik veya bileşen yalnızca, bildirim amacıyla bir eylem veya olayın oluştuğunu kullanıcıları uyarmak üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="327ba-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="327ba-109">Menüleri, araç çubukları ve diğer kullanıcı arabirimi öğeleri uygulamalarla standart etkileşim için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="327ba-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>

### <a name="to-set-the-icon"></a><span data-ttu-id="327ba-110">Simge ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="327ba-110">To set the icon</span></span>

1. <span data-ttu-id="327ba-111">Bir değer atayın <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="327ba-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="327ba-112">Değer türü olmalıdır `System.Drawing.Icon` ve bir .ico dosyasını yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="327ba-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="327ba-113">Simge dosyası üç nokta düğmesine tıklayarak ya da kod belirtebilirsiniz (![Visual Studio Özellikler penceresinde üç nokta düğmesini (…)](./media/visual-studio-ellipsis-button.png)) yanındaki <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliğinde **özellikleri** Pencere seçip ardından dosyasında **açık** görüntülenen iletişim kutusunda.</span><span class="sxs-lookup"><span data-stu-id="327ba-113">You can specify the icon file in code or by clicking the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>

2. <span data-ttu-id="327ba-114">Ayarlama <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="327ba-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>

3. <span data-ttu-id="327ba-115">Ayarlama <xref:System.Windows.Forms.NotifyIcon.Text%2A> uygun bir araç ipucu dize özelliği.</span><span class="sxs-lookup"><span data-stu-id="327ba-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>

     <span data-ttu-id="327ba-116">Aşağıdaki kod örneğinde yolunu ayarlamak için simgenin konumunu **Belgelerim** klasör.</span><span class="sxs-lookup"><span data-stu-id="327ba-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="327ba-117">Bu konum, Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="327ba-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="327ba-118">Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeylerine sahip kullanıcılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="327ba-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="327ba-119">Aşağıdaki örnek bir formla gerektiren bir <xref:System.Windows.Forms.NotifyIcon> denetim zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="327ba-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="327ba-120">Adlı bir simge dosyası aynı zamanda gerektirir `Icon.ico`.</span><span class="sxs-lookup"><span data-stu-id="327ba-120">It also requires an icon file named `Icon.ico`.</span></span>

    ```vb
    ' You should replace the bold icon in the sample below
    ' with an icon of your own choosing.
    NotifyIcon1.Icon = New _
       System.Drawing.Icon(System.Environment.GetFolderPath _
       (System.Environment.SpecialFolder.Personal) _
       & "\Icon.ico")
    NotifyIcon1.Visible = True
    NotifyIcon1.Text = "Antivirus program"
    ```

    ```csharp
    // You should replace the bold icon in the sample below
    // with an icon of your own choosing.
    // Note the escape character used (@) when specifying the path.
    notifyIcon1.Icon =
       new System.Drawing.Icon (System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.Personal)
       + @"\Icon.ico");
    notifyIcon1.Visible = true;
    notifyIcon1.Text = "Antivirus program";
    ```

    ```cpp
    // You should replace the bold icon in the sample below
    // with an icon of your own choosing.
    notifyIcon1->Icon = gcnew
       System::Drawing::Icon(String::Concat
       (System::Environment::GetFolderPath
       (System::Environment::SpecialFolder::Personal),
       "\\Icon.ico"));
    notifyIcon1->Visible = true;
    notifyIcon1->Text = "Antivirus program";
    ```

## <a name="see-also"></a><span data-ttu-id="327ba-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="327ba-121">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="327ba-122">Nasıl yapılır: Bir kısayol menüsünü Windows Forms Notifyıcon bileşeniyle ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="327ba-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [<span data-ttu-id="327ba-123">NotifyIcon Bileşeni</span><span class="sxs-lookup"><span data-stu-id="327ba-123">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="327ba-124">NotifyIcon Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="327ba-124">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
