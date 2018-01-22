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
ms.workload: dotnet
ms.openlocfilehash: 46b80ee0c74da7371ac8f7a16d3430b5b753059d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a><span data-ttu-id="6d7b9-102">İzlenecek yol: Tasarım Zamanında Barındırılan bir WPF Öğesinin Özelliklerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="6d7b9-102">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>
<span data-ttu-id="6d7b9-103">Bu kılavuz, bir Windows formunda barındırılan bir Windows Presentation Foundation (WPF) denetiminin özellik değerlerini değiştirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-103">This walkthrough shows you how to change property values of a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="6d7b9-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="6d7b9-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="6d7b9-105">Projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-105">Create the project.</span></span>  
  
-   <span data-ttu-id="6d7b9-106">WPF denetimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="6d7b9-107">Bir Windows formunda WPF denetimleri barındırır.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-107">Host the WPF controls on a Windows Form.</span></span>  
  
-   <span data-ttu-id="6d7b9-108">Visual Studio için WPF Tasarımcısı özellik değerlerini değiştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-108">Use the WPF Designer for Visual Studio to change property values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d7b9-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6d7b9-110">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6d7b9-111">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="6d7b9-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6d7b9-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="6d7b9-112">Prerequisites</span></span>  
 <span data-ttu-id="6d7b9-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="6d7b9-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="6d7b9-114">.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="6d7b9-115">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d7b9-115">Creating the Project</span></span>  
 <span data-ttu-id="6d7b9-116">Windows Forms projesi oluşturmak için ilk adımdır bakın.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d7b9-117">WPF içeriği barındırma, yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="6d7b9-118">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6d7b9-118">To create the project</span></span>  
  
-   <span data-ttu-id="6d7b9-119">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `WpfHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="6d7b9-120">WPF denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d7b9-120">Creating the WPF Control</span></span>  
 <span data-ttu-id="6d7b9-121">Projeye bir WPF denetimi ekledikten sonra formdaki düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-121">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="6d7b9-122">WPF denetimleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6d7b9-122">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="6d7b9-123">Yeni bir WPF eklemek <xref:System.Windows.Controls.UserControl> projeye.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-123">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="6d7b9-124">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="6d7b9-125">Daha fazla bilgi için bkz: [izlenecek yol: oluşturma yeni WPF içeriği Windows formlarında tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="6d7b9-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="6d7b9-126">İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Controls.Control.Background%2A> özelliğine `Blue`.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-126">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
3.  <span data-ttu-id="6d7b9-127">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-127">Build the project.</span></span>  
  
## <a name="changing-property-values-on-the-wpf-control"></a><span data-ttu-id="6d7b9-128">WPF denetimi özellik değerlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="6d7b9-128">Changing Property Values on the WPF Control</span></span>  
 <span data-ttu-id="6d7b9-129"><xref:System.Windows.Forms.Integration.ElementHost> Akıllı etiket kolaylaştırır barındırılan WPF özelliklerini değiştirmek içerik WPF Tasarımcısı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-129">The <xref:System.Windows.Forms.Integration.ElementHost> smart tag makes it easy to change properties of hosted WPF content by using the WPF Designer.</span></span>  
  
#### <a name="to-host-a-wpf-control"></a><span data-ttu-id="6d7b9-130">WPF denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="6d7b9-130">To host a WPF control</span></span>  
  
1.  <span data-ttu-id="6d7b9-131">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-131">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="6d7b9-132">İçinde **araç**, **WPF kullanıcı denetimi** sekmesinde, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-132">In the **Toolbox**, in the **WPF User Controls** tab, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="6d7b9-133">Örneğinin `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="6d7b9-134">İçinde **ElementHost görevleri** akıllı etiket paneli, select **barındırılan içeriği Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-134">In the **ElementHost Tasks** smart tag panel, select **Edit Hosted Content**.</span></span>  
  
     <span data-ttu-id="6d7b9-135">WPF Tasarımcısı'nda da UserControl1.XAML'i açar.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-135">UserControl1.xaml opens in the WPF Designer.</span></span>  
  
4.  <span data-ttu-id="6d7b9-136">İçinde **özellikleri** penceresindeki değerini ayarlayın <xref:System.Windows.Controls.Control.Background%2A> özelliğine `Red`.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-136">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Red`.</span></span>  
  
5.  <span data-ttu-id="6d7b9-137">Projeyi yeniden oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-137">Rebuild the project.</span></span>  
  
6.  <span data-ttu-id="6d7b9-138">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-138">Open `Form1` in the Windows Forms Designer.</span></span>  
  
     <span data-ttu-id="6d7b9-139">Örneğinin `UserControl1` kırmızı bir arka plana sahip.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-139">The instance of `UserControl1` has a red background.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d7b9-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d7b9-140">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="6d7b9-141">Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="6d7b9-141">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="6d7b9-142">Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama</span><span class="sxs-lookup"><span data-stu-id="6d7b9-142">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="6d7b9-143">İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="6d7b9-143">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="6d7b9-144">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="6d7b9-144">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="6d7b9-145">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="6d7b9-145">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="6d7b9-146">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="6d7b9-146">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
