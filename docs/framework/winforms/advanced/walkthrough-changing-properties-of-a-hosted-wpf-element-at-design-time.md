---
title: "İzlenecek yol: Tasarım Zamanında Barındırılan bir WPF Öğesinin Özelliklerini Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 522c47865294b7313b0b5e745d40726996230c49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a><span data-ttu-id="6fca7-102">İzlenecek yol: Tasarım Zamanında Barındırılan bir WPF Öğesinin Özelliklerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="6fca7-102">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>
<span data-ttu-id="6fca7-103">Bu kılavuz, bir Windows formunda barındırılan bir Windows Presentation Foundation (WPF) denetiminin özellik değerlerini değiştirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="6fca7-103">This walkthrough shows you how to change property values of a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="6fca7-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="6fca7-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="6fca7-105">Projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6fca7-105">Create the project.</span></span>  
  
-   <span data-ttu-id="6fca7-106">WPF denetimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6fca7-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="6fca7-107">Bir Windows formunda WPF denetimleri barındırır.</span><span class="sxs-lookup"><span data-stu-id="6fca7-107">Host the WPF controls on a Windows Form.</span></span>  
  
-   <span data-ttu-id="6fca7-108">Visual Studio için WPF Tasarımcısı özellik değerlerini değiştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fca7-108">Use the WPF Designer for Visual Studio to change property values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fca7-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="6fca7-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6fca7-110">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="6fca7-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6fca7-111">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="6fca7-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6fca7-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="6fca7-112">Prerequisites</span></span>  
 <span data-ttu-id="6fca7-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="6fca7-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="6fca7-114">.</span><span class="sxs-lookup"><span data-stu-id="6fca7-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="6fca7-115">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6fca7-115">Creating the Project</span></span>  
 <span data-ttu-id="6fca7-116">Windows Forms projesi oluşturmak için ilk adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="6fca7-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fca7-117">WPF içeriği barındırma, yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6fca7-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="6fca7-118">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6fca7-118">To create the project</span></span>  
  
-   <span data-ttu-id="6fca7-119">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="6fca7-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `WpfHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="6fca7-120">WPF denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6fca7-120">Creating the WPF Control</span></span>  
 <span data-ttu-id="6fca7-121">Projeye bir WPF denetimi ekledikten sonra formdaki düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fca7-121">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="6fca7-122">WPF denetimleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6fca7-122">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="6fca7-123">Yeni bir WPF eklemek <xref:System.Windows.Controls.UserControl> projeye.</span><span class="sxs-lookup"><span data-stu-id="6fca7-123">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="6fca7-124">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="6fca7-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="6fca7-125">Daha fazla bilgi için bkz: [izlenecek yol: oluşturma yeni WPF içeriği Windows formlarında tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="6fca7-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="6fca7-126">İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Controls.Control.Background%2A> özelliğine `Blue`.</span><span class="sxs-lookup"><span data-stu-id="6fca7-126">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
3.  <span data-ttu-id="6fca7-127">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6fca7-127">Build the project.</span></span>  
  
## <a name="changing-property-values-on-the-wpf-control"></a><span data-ttu-id="6fca7-128">WPF denetimi özellik değerlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="6fca7-128">Changing Property Values on the WPF Control</span></span>  
 <span data-ttu-id="6fca7-129"><xref:System.Windows.Forms.Integration.ElementHost> Akıllı etiket kolaylaştırır barındırılan WPF özelliklerini değiştirmek içerik WPF Tasarımcısı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6fca7-129">The <xref:System.Windows.Forms.Integration.ElementHost> smart tag makes it easy to change properties of hosted WPF content by using the WPF Designer.</span></span>  
  
#### <a name="to-host-a-wpf-control"></a><span data-ttu-id="6fca7-130">WPF denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="6fca7-130">To host a WPF control</span></span>  
  
1.  <span data-ttu-id="6fca7-131">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="6fca7-131">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="6fca7-132">İçinde **araç**, **WPF kullanıcı denetimi** sekmesinde, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.</span><span class="sxs-lookup"><span data-stu-id="6fca7-132">In the **Toolbox**, in the **WPF User Controls** tab, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="6fca7-133">Örneğinin `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="6fca7-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="6fca7-134">İçinde **ElementHost görevleri** akıllı etiket paneli, select **barındırılan içeriği Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="6fca7-134">In the **ElementHost Tasks** smart tag panel, select **Edit Hosted Content**.</span></span>  
  
     <span data-ttu-id="6fca7-135">WPF Tasarımcısı'nda da UserControl1.XAML'i açar.</span><span class="sxs-lookup"><span data-stu-id="6fca7-135">UserControl1.xaml opens in the WPF Designer.</span></span>  
  
4.  <span data-ttu-id="6fca7-136">İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Controls.Control.Background%2A> özelliğine `Red`.</span><span class="sxs-lookup"><span data-stu-id="6fca7-136">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Red`.</span></span>  
  
5.  <span data-ttu-id="6fca7-137">Projeyi yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6fca7-137">Rebuild the project.</span></span>  
  
6.  <span data-ttu-id="6fca7-138">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="6fca7-138">Open `Form1` in the Windows Forms Designer.</span></span>  
  
     <span data-ttu-id="6fca7-139">Örneğinin `UserControl1` kırmızı bir arka plana sahip.</span><span class="sxs-lookup"><span data-stu-id="6fca7-139">The instance of `UserControl1` has a red background.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fca7-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6fca7-140">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="6fca7-141">Nasıl yapılır: TableLayoutPanel denetiminde alt denetimleri sabitleme ve yerleştirme</span><span class="sxs-lookup"><span data-stu-id="6fca7-141">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="6fca7-142">Nasıl yapılır: tasarım zamanında denetimi formların kenarlarına hizalama</span><span class="sxs-lookup"><span data-stu-id="6fca7-142">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="6fca7-143">İzlenecek yol: Dayama çizgileri kullanarak Windows Forms'ta denetimleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="6fca7-143">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="6fca7-144">Geçiş ve birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="6fca7-144">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="6fca7-145">WPF denetimlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="6fca7-145">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="6fca7-146">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="6fca7-146">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
