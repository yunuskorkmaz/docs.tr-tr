---
title: "Nasıl yapılır: Windows Forms NotifyIcon Bileşeniyle TaskBar'na Uygulama Simgeleri Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 97c31998885926e9a7372bcf3182d1c95f0b79d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="cc751-102">Nasıl yapılır: Windows Forms NotifyIcon Bileşeniyle TaskBar'na Uygulama Simgeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="cc751-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>
<span data-ttu-id="cc751-103">Windows Forms <xref:System.Windows.Forms.NotifyIcon> bileşen durumu görev çubuğu bildirim alanında tek bir simge görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cc751-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="cc751-104">Durum alanında birden çok simgeleri göstermek için birden çok sahip <xref:System.Windows.Forms.NotifyIcon> formunuzda bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="cc751-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="cc751-105">Bir denetim için görüntülenen simge ayarlamak için kullanın <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cc751-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="cc751-106">Ayrıca kod yazabilirsiniz <xref:System.Windows.Forms.NotifyIcon.DoubleClick> kullanıcı simgesine tıkladığında bu bir şey için olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="cc751-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="cc751-107">Örneğin, bir iletişim kutusu kullanıcının simgesi tarafından temsil edilen arka plan işlemi yapılandırmak görünür hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="cc751-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc751-108"><xref:System.Windows.Forms.NotifyIcon> Bileşeni bir eylem veya olay oluştu uyarı kullanıcılara yalnızca, bildirim amacıyla kullanılan veya bazı sıralama durumu değişikliği oluştu.</span><span class="sxs-lookup"><span data-stu-id="cc751-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="cc751-109">Menüleri, araç çubukları ve diğer kullanıcı arabirimi öğeleri uygulamalarla standart etkileşim için kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc751-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>  
  
### <a name="to-set-the-icon"></a><span data-ttu-id="cc751-110">Simge ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="cc751-110">To set the icon</span></span>  
  
1.  <span data-ttu-id="cc751-111">Bir değer atadığınız <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cc751-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="cc751-112">Değer türü olmalıdır `System.Drawing.Icon` ve bir .ico dosyadan yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="cc751-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="cc751-113">Simge dosyası kodunda ya da üç nokta düğmesini tıklatarak belirtebilirsiniz (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.NotifyIcon.Icon%2A> özelliğinde  **Özellikler** penceresi ve sonra dosyayı seçerek **açık** görüntülenen iletişim kutusunda.</span><span class="sxs-lookup"><span data-stu-id="cc751-113">You can specify the icon file in code or by clicking the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>  
  
2.  <span data-ttu-id="cc751-114">Ayarlama <xref:System.Windows.Forms.NotifyIcon.Visible%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="cc751-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="cc751-115">Ayarlama <xref:System.Windows.Forms.NotifyIcon.Text%2A> uygun bir araç ipucu dizesi özelliğine.</span><span class="sxs-lookup"><span data-stu-id="cc751-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>  
  
     <span data-ttu-id="cc751-116">Aşağıdaki kod örneğinde yolunu ayarlama simgenin konumunu için **Belgelerim** klasör.</span><span class="sxs-lookup"><span data-stu-id="cc751-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="cc751-117">Windows işletim sistemi çalıştıran bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü bu konumu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc751-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="cc751-118">Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri kullanıcılarla sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc751-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="cc751-119">Aşağıdaki örnek bir formla gerektiren bir <xref:System.Windows.Forms.NotifyIcon> denetimi zaten eklendi.</span><span class="sxs-lookup"><span data-stu-id="cc751-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="cc751-120">Adlı bir simge dosyası da gerektirir `Icon.ico`.</span><span class="sxs-lookup"><span data-stu-id="cc751-120">It also requires an icon file named `Icon.ico`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cc751-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc751-121">See Also</span></span>  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [<span data-ttu-id="cc751-122">Nasıl yapılır: bir kısayol menüsünü Windows Forms Notifyıcon bileşeniyle ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="cc751-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)  
 [<span data-ttu-id="cc751-123">Notifyıcon bileşeni</span><span class="sxs-lookup"><span data-stu-id="cc751-123">NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [<span data-ttu-id="cc751-124">Notifyıcon bileşenine genel bakış</span><span class="sxs-lookup"><span data-stu-id="cc751-124">NotifyIcon Component Overview</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
