---
title: Uygulama simgelerini NotifyIcon bileşeniyle birlikte görev çubuğuna ekleme
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
ms.openlocfilehash: 46b50ecaabe75dba08fea922d7b5639031692269
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746252"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="38a0f-102">Nasıl yapılır: Windows Forms NotifyIcon Bileşeniyle TaskBar'na Uygulama Simgeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="38a0f-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>

<span data-ttu-id="38a0f-103">Windows Forms <xref:System.Windows.Forms.NotifyIcon> bileşeni, görev çubuğunun durum bildirimi alanında tek bir simge görüntüler.</span><span class="sxs-lookup"><span data-stu-id="38a0f-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="38a0f-104">Durum alanında birden çok simge göstermek için, formunuzda birden çok <xref:System.Windows.Forms.NotifyIcon> bileşeni olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="38a0f-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="38a0f-105">Bir denetim için görüntülenecek simgeyi ayarlamak için <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="38a0f-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="38a0f-106">Ayrıca, Kullanıcı simgeye çift tıkladığında bir şeyin olması için <xref:System.Windows.Forms.NotifyIcon.DoubleClick> olay işleyicisine kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38a0f-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="38a0f-107">Örneğin, kullanıcının simgesiyle gösterilen arka plan sürecini yapılandırması için bir iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="38a0f-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>

> [!NOTE]
> <span data-ttu-id="38a0f-108"><xref:System.Windows.Forms.NotifyIcon> bileşeni, yalnızca bir eylem veya olayın oluştuğunu veya bazı bir sıralama durumunda değişiklik olduğunu uyarmak için bildirim amaçları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38a0f-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="38a0f-109">Uygulamalarla standart etkileşim için menüleri, araç çubuklarını ve diğer kullanıcı arabirimi öğelerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="38a0f-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>

### <a name="to-set-the-icon"></a><span data-ttu-id="38a0f-110">Simgeyi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="38a0f-110">To set the icon</span></span>

1. <span data-ttu-id="38a0f-111"><xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliğine bir değer atayın.</span><span class="sxs-lookup"><span data-stu-id="38a0f-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="38a0f-112">Değer `System.Drawing.Icon` türünde olmalı ve bir. ico dosyasından yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="38a0f-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="38a0f-113">Koddaki simge dosyasını veya üç nokta düğmesini (...), **Özellikler** penceresindeki <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliğinin yanındaki (... Özellikler penceresi) ve ardından görüntülenen **Aç** iletişim kutusunda dosyayı seçerek belirtebilirsiniz (![)](./media/visual-studio-ellipsis-button.png).</span><span class="sxs-lookup"><span data-stu-id="38a0f-113">You can specify the icon file in code or by clicking the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>

2. <span data-ttu-id="38a0f-114">Ayarlama <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="38a0f-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>

3. <span data-ttu-id="38a0f-115"><xref:System.Windows.Forms.NotifyIcon.Text%2A> özelliğini uygun bir araç Ipucu dizesine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="38a0f-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>

     <span data-ttu-id="38a0f-116">Aşağıdaki kod örneğinde, simgenin konumu için ayarlanan yol **Belgelerim klasörüdür.**</span><span class="sxs-lookup"><span data-stu-id="38a0f-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="38a0f-117">Bu konum, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içerdiğini varsaydığı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38a0f-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="38a0f-118">Bu konumun seçilmesi, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="38a0f-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="38a0f-119">Aşağıdaki örnek, zaten eklenmiş <xref:System.Windows.Forms.NotifyIcon> denetimi olan bir form gerektirir.</span><span class="sxs-lookup"><span data-stu-id="38a0f-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="38a0f-120">Ayrıca, `Icon.ico`adlı bir simge dosyası da gerektirir.</span><span class="sxs-lookup"><span data-stu-id="38a0f-120">It also requires an icon file named `Icon.ico`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="38a0f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38a0f-121">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="38a0f-122">Nasıl yapılır: Bir Kısayol Menüsünü Windows Forms NotifyIcon Bileşeniyle İlişkilendirme</span><span class="sxs-lookup"><span data-stu-id="38a0f-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [<span data-ttu-id="38a0f-123">NotifyIcon Bileşeni</span><span class="sxs-lookup"><span data-stu-id="38a0f-123">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="38a0f-124">NotifyIcon Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="38a0f-124">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
