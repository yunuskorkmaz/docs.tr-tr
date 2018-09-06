---
title: 'İzlenecek yol: Tasarım Zamanında Barındırılan bir WPF Öğesinin Özelliklerini Değiştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
ms.openlocfilehash: 15cab9266af5840aa4b37a62b71bd5010b7a859a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741026"
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a><span data-ttu-id="658e3-102">İzlenecek yol: Tasarım Zamanında Barındırılan bir WPF Öğesinin Özelliklerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="658e3-102">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>
<span data-ttu-id="658e3-103">Bu izlenecek yol, bir Windows Form üzerinde barındırılan bir Windows Presentation Foundation (WPF) denetimin özellik değerlerini değiştirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="658e3-103">This walkthrough shows you how to change property values of a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="658e3-104">Bu kılavuzda, aşağıdaki görevleri gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="658e3-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="658e3-105">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="658e3-105">Create the project.</span></span>  
  
-   <span data-ttu-id="658e3-106">WPF denetimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="658e3-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="658e3-107">WPF denetimlerini bir Windows Form üzerinde barındırın.</span><span class="sxs-lookup"><span data-stu-id="658e3-107">Host the WPF controls on a Windows Form.</span></span>  
  
-   <span data-ttu-id="658e3-108">Özellik değerlerini değiştirmek için Visual Studio için WPF Tasarımcısı'nı kullanın.</span><span class="sxs-lookup"><span data-stu-id="658e3-108">Use the WPF Designer for Visual Studio to change property values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="658e3-109">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="658e3-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="658e3-110">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="658e3-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="658e3-111">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="658e3-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="658e3-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="658e3-112">Prerequisites</span></span>  
 <span data-ttu-id="658e3-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="658e3-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="658e3-114">.</span><span class="sxs-lookup"><span data-stu-id="658e3-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="658e3-115">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="658e3-115">Creating the Project</span></span>  
 <span data-ttu-id="658e3-116">İlk adım Windows Forms projesi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="658e3-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="658e3-117">WPF içeriği barındırma, yalnızca C# ve Visual Basic projelerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="658e3-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="658e3-118">Proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="658e3-118">To create the project</span></span>  
  
-   <span data-ttu-id="658e3-119">Visual Basic veya Visual C# adlı yeni bir Windows Forms uygulaması projesi oluşturma `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="658e3-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `WpfHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="658e3-120">WPF denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="658e3-120">Creating the WPF Control</span></span>  
 <span data-ttu-id="658e3-121">Bir WPF denetiminde projeye ekledikten sonra form üzerinde düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="658e3-121">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="658e3-122">WPF denetimleri oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="658e3-122">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="658e3-123">Yeni bir WPF ekleme <xref:System.Windows.Controls.UserControl> projeye.</span><span class="sxs-lookup"><span data-stu-id="658e3-123">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="658e3-124">Denetim türü için varsayılan adı kullanacak `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="658e3-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="658e3-125">Daha fazla bilgi için [izlenecek yol: oluşturma yeni WPF içeriği Windows Forms'ta tasarım zamanında](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="658e3-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="658e3-126">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Controls.Control.Background%2A> özelliğini `Blue`.</span><span class="sxs-lookup"><span data-stu-id="658e3-126">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
3.  <span data-ttu-id="658e3-127">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="658e3-127">Build the project.</span></span>  
  
## <a name="changing-property-values-on-the-wpf-control"></a><span data-ttu-id="658e3-128">WPF denetimin özellik değerlerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="658e3-128">Changing Property Values on the WPF Control</span></span>  
 <span data-ttu-id="658e3-129"><xref:System.Windows.Forms.Integration.ElementHost> Akıllı etiket kolaylaştırır barındırılan WPF özelliklerini değiştirmek içerik WPF Tasarımcısı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="658e3-129">The <xref:System.Windows.Forms.Integration.ElementHost> smart tag makes it easy to change properties of hosted WPF content by using the WPF Designer.</span></span>  
  
#### <a name="to-host-a-wpf-control"></a><span data-ttu-id="658e3-130">WPF denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="658e3-130">To host a WPF control</span></span>  
  
1.  <span data-ttu-id="658e3-131">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="658e3-131">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="658e3-132">İçinde **araç kutusu**, **WPF kullanıcı denetimleri** sekmesinde, çift `UserControl1` bir örneğini oluşturmak için `UserControl1` form üzerinde.</span><span class="sxs-lookup"><span data-stu-id="658e3-132">In the **Toolbox**, in the **WPF User Controls** tab, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="658e3-133">Örneğini `UserControl1` yeni bir barındırılan <xref:System.Windows.Forms.Integration.ElementHost> adlı Denetim `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="658e3-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="658e3-134">İçinde **ElementHost görevleri** akıllı etiket paneli, select **barındırılan içerik Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="658e3-134">In the **ElementHost Tasks** smart tag panel, select **Edit Hosted Content**.</span></span>  
  
     <span data-ttu-id="658e3-135">UserControl1.xaml WPF Tasarımcısı'nda açılır.</span><span class="sxs-lookup"><span data-stu-id="658e3-135">UserControl1.xaml opens in the WPF Designer.</span></span>  
  
4.  <span data-ttu-id="658e3-136">İçinde **özellikleri** penceresinde değerini ayarlayın <xref:System.Windows.Controls.Control.Background%2A> özelliğini `Red`.</span><span class="sxs-lookup"><span data-stu-id="658e3-136">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Red`.</span></span>  
  
5.  <span data-ttu-id="658e3-137">Projeyi yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="658e3-137">Rebuild the project.</span></span>  
  
6.  <span data-ttu-id="658e3-138">Açık `Form1` Windows Forms Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="658e3-138">Open `Form1` in the Windows Forms Designer.</span></span>  
  
     <span data-ttu-id="658e3-139">Örneğini `UserControl1` kırmızı bir arka plana sahip.</span><span class="sxs-lookup"><span data-stu-id="658e3-139">The instance of `UserControl1` has a red background.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="658e3-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="658e3-140">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="658e3-141">Nasıl yapılır: TableLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="658e3-141">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="658e3-142">Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama</span><span class="sxs-lookup"><span data-stu-id="658e3-142">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="658e3-143">İzlenecek yol: Dayama Çizgileri Kullanarak Windows Forms'da Denetimleri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="658e3-143">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="658e3-144">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="658e3-144">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="658e3-145">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="658e3-145">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="658e3-146">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="658e3-146">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
