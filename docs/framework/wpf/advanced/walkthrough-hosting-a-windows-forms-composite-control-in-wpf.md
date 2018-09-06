---
title: "İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 22bfcf63fa42e72b3b971b18b5e68aec1e57c649
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43859416"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="edd1a-102">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="edd1a-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="edd1a-103"> uygulamaları oluşturmak için zengin bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="edd1a-103"> provides a rich environment for creating applications.</span></span> <span data-ttu-id="edd1a-104">Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu olabilir en az yeniden daha etkili kodda bazıları, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama yerine baştan yeniden.</span><span class="sxs-lookup"><span data-stu-id="edd1a-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="edd1a-105">Mevcut Windows Forms denetimleri olduğunda en yaygın senaryodur.</span><span class="sxs-lookup"><span data-stu-id="edd1a-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="edd1a-106">Bazı durumlarda, bile bu denetimleri için kaynak koduna erişim olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="edd1a-107"> gibi denetimleri barındırma için basit bir yordam sağlar bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="edd1a-107"> provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="edd1a-108">Örneğin, kullanabileceğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çoğu barındırırken, programlama için <xref:System.Windows.Forms.DataGridView> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="edd1a-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="edd1a-109">Bu izlenecek yolda veri girişi gerçekleştirmek için bir Windows Forms bileşik denetimini barındıran bir uygulama aracılığıyla adımları bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="edd1a-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="edd1a-110">Bileşik Denetim DLL içinde paketlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="edd1a-111">Bu genel yordam, daha karmaşık uygulamalar ve denetimler için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="edd1a-112">Bu izlenecek yol Görünüm ve işlevselliği için neredeyse aynı olacak şekilde tasarlanan [izlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="edd1a-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="edd1a-113">Barındırma senaryo tersine, birincil farktır.</span><span class="sxs-lookup"><span data-stu-id="edd1a-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="edd1a-114">İzlenecek yol, iki bölüme ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="edd1a-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="edd1a-115">İlk bölüm, Windows Forms bileşik denetimini uygulamasını kısaca açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="edd1a-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="edd1a-116">İkinci bölüm içinde bileşik denetimini barındırmak nasıl ayrıntılı olarak ele alınmaktadır bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama denetim olaylarını almak ve denetim özelliklerini bazılarına erişmek.</span><span class="sxs-lookup"><span data-stu-id="edd1a-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="edd1a-117">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="edd1a-117">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="edd1a-118">Windows Forms bileşik denetimini uygulama.</span><span class="sxs-lookup"><span data-stu-id="edd1a-118">Implementing the Windows Forms composite control.</span></span>  
  
-   <span data-ttu-id="edd1a-119">WPF ana bilgisayar uygulaması oluşturma.</span><span class="sxs-lookup"><span data-stu-id="edd1a-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="edd1a-120">Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [bir WPF Örneği'nde Windows Forms bileşik denetimini barındırma](https://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="edd1a-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="edd1a-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="edd1a-121">Prerequisites</span></span>  
 <span data-ttu-id="edd1a-122">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="edd1a-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="edd1a-123">.</span><span class="sxs-lookup"><span data-stu-id="edd1a-123">.</span></span>  
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="edd1a-124">Windows Forms bileşik denetimini uygulama</span><span class="sxs-lookup"><span data-stu-id="edd1a-124">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="edd1a-125">Bu örnekte kullanılan Windows Forms bileşik denetimini basit veri girişi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-125">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="edd1a-126">Bu form kullanıcının adı ve adresi alır ve ana bilgisayar için bu bilgileri döndürmek için bir özel olay kullanır.</span><span class="sxs-lookup"><span data-stu-id="edd1a-126">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="edd1a-127">İşlenen denetimi aşağıda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-127">The following illustration shows the rendered control.</span></span>  
  
 <span data-ttu-id="edd1a-128">![Basit bir Windows Forms denetimi](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")</span><span class="sxs-lookup"><span data-stu-id="edd1a-128">![Simple Windows Forms control](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")</span></span>  
<span data-ttu-id="edd1a-129">Windows Forms bileşik denetimini</span><span class="sxs-lookup"><span data-stu-id="edd1a-129">Windows Forms composite control</span></span>  
  
### <a name="creating-the-project"></a><span data-ttu-id="edd1a-130">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="edd1a-130">Creating the Project</span></span>  
 <span data-ttu-id="edd1a-131">Proje başlatmak için:</span><span class="sxs-lookup"><span data-stu-id="edd1a-131">To start the project:</span></span>  
  
1.  <span data-ttu-id="edd1a-132">Başlatma [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]açın **yeni proje** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="edd1a-132">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="edd1a-133">Pencere kategorisinde seçin **Windows Forms Denetim Kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="edd1a-133">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3.  <span data-ttu-id="edd1a-134">Yeni proje adını `MyControls`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-134">Name the new project `MyControls`.</span></span>  
  
4.  <span data-ttu-id="edd1a-135">Konum için bir kolayca adlandırılmış üst düzey klasör gibi belirtin `WpfHostingWindowsFormsControl`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-135">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="edd1a-136">Daha sonra ana bilgisayar uygulaması bu klasöre koyacaktır.</span><span class="sxs-lookup"><span data-stu-id="edd1a-136">Later, you will put the host application in this folder.</span></span>  
  
5.  <span data-ttu-id="edd1a-137">Tıklayın **Tamam** projeyi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="edd1a-137">Click **OK** to create the project.</span></span> <span data-ttu-id="edd1a-138">Varsayılan proje adlı tek bir denetim içeren `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-138">The default project contains a single control named `UserControl1`.</span></span>  
  
6.  <span data-ttu-id="edd1a-139">Çözüm Gezgini'nde, yeniden adlandırma `UserControl1` için `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-139">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="edd1a-140">Projenize aşağıdaki sistem DLL'lerini başvuruları olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-140">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="edd1a-141">Bu DLL'leri birini varsayılan olarak dahil edilmez, bunları projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="edd1a-141">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
-   <span data-ttu-id="edd1a-142">Sistem</span><span class="sxs-lookup"><span data-stu-id="edd1a-142">System</span></span>  
  
-   <span data-ttu-id="edd1a-143">System.Data</span><span class="sxs-lookup"><span data-stu-id="edd1a-143">System.Data</span></span>  
  
-   <span data-ttu-id="edd1a-144">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="edd1a-144">System.Drawing</span></span>  
  
-   <span data-ttu-id="edd1a-145">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="edd1a-145">System.Windows.Forms</span></span>  
  
-   <span data-ttu-id="edd1a-146">System.Xml</span><span class="sxs-lookup"><span data-stu-id="edd1a-146">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="edd1a-147">Formu için denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="edd1a-147">Adding Controls to the Form</span></span>  
 <span data-ttu-id="edd1a-148">Formu için denetimler eklemek için:</span><span class="sxs-lookup"><span data-stu-id="edd1a-148">To add controls to the form:</span></span>  
  
-   <span data-ttu-id="edd1a-149">Açık `MyControl1` Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="edd1a-149">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="edd1a-150">Beş ekleme <xref:System.Windows.Forms.Label> denetimleri ve bunlara karşılık gelen <xref:System.Windows.Forms.TextBox> denetimleri, boyutu ve formdaki yukarıdaki çizimin olduğu gibi düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-150">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="edd1a-151">Örnekte, <xref:System.Windows.Forms.TextBox> denetimleri adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="edd1a-151">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 <span data-ttu-id="edd1a-152">İki ekleme <xref:System.Windows.Forms.Button> etiketli denetimler **Tamam** ve **iptal**.</span><span class="sxs-lookup"><span data-stu-id="edd1a-152">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="edd1a-153">Bu örnekte düğme adlarıdır `btnOK` ve `btnCancel`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="edd1a-153">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="edd1a-154">Destek kodu uygulama</span><span class="sxs-lookup"><span data-stu-id="edd1a-154">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="edd1a-155">Formun kod Görünümü'nde açın.</span><span class="sxs-lookup"><span data-stu-id="edd1a-155">Open the form in code view.</span></span> <span data-ttu-id="edd1a-156">Ana bilgisayar için toplanan verileri özel yükselterek denetimini döndürür `OnButtonClick` olay.</span><span class="sxs-lookup"><span data-stu-id="edd1a-156">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="edd1a-157">Verileri olay bağımsız değişkeni nesnesinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="edd1a-157">The data is contained in the event argument object.</span></span> <span data-ttu-id="edd1a-158">Aşağıdaki kod, olay ve temsilci bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-158">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="edd1a-159">Aşağıdaki kodu ekleyin `MyControl1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="edd1a-159">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 <span data-ttu-id="edd1a-160">`MyControlEventArgs` Sınıfı konağa döndürülmesi gereken bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-160">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>  
  
 <span data-ttu-id="edd1a-161">Aşağıdaki sınıf formuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="edd1a-161">Add the following class to the form.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 <span data-ttu-id="edd1a-162">Kullanıcı tıkladığında **Tamam** veya **iptal** düğmesi <xref:System.Windows.Forms.Control.Click> olay işleyicileri oluşturma bir `MyControlEventArgs` veri içeren nesne ve başlatır `OnButtonClick` olay.</span><span class="sxs-lookup"><span data-stu-id="edd1a-162">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="edd1a-163">Olay bağımsız değişkenin iki işleyiciler arasındaki tek fark, `IsOK` özelliği.</span><span class="sxs-lookup"><span data-stu-id="edd1a-163">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="edd1a-164">Bu özellik ana bilgisayarın hangi düğmesine tıklandığını belirleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="edd1a-164">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="edd1a-165">Ayarlanmış `true` için **Tamam** düğmesi ve `false` için **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="edd1a-165">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="edd1a-166">Aşağıdaki kod, iki düğmesi işleyicileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-166">The following code shows the two button handlers.</span></span>  
  
 <span data-ttu-id="edd1a-167">Aşağıdaki kodu ekleyin `MyControl1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="edd1a-167">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="edd1a-168">Derlemeyi güçlü bir isim verilmesi ve bütünleştirilmiş kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="edd1a-168">Giving the Assembly a Strong Name and Building the Assembly</span></span>  
 <span data-ttu-id="edd1a-169">Tarafından başvurulabilmesi derlemenin bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, sağlam bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="edd1a-169">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="edd1a-170">Güçlü bir ad oluşturmak için bir anahtar dosyası ile Sn.exe oluşturun ve projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="edd1a-170">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>  
  
1.  <span data-ttu-id="edd1a-171">Açık bir [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="edd1a-171">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="edd1a-172">Bunu yapmak için tıklatın **Başlat** menüsüne ve ardından **tüm programlar/Microsoft Visual Studio 2010/Visual Studio Araçları/Visual Studio komut istemi**.</span><span class="sxs-lookup"><span data-stu-id="edd1a-172">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="edd1a-173">Bu, özel ortam değişkenleriyle bir konsol penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="edd1a-173">This launches a console window with customized environment variables.</span></span>  
  
2.  <span data-ttu-id="edd1a-174">Komut isteminde kullanmak `cd` proje klasörünüzün Git komutu.</span><span class="sxs-lookup"><span data-stu-id="edd1a-174">At the command prompt, use the `cd` command to go to your project folder.</span></span>  
  
3.  <span data-ttu-id="edd1a-175">Aşağıdaki komutu çalıştırarak MyControls.snk adlı bir anahtar dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="edd1a-175">Generate a key file named MyControls.snk by running the following command.</span></span>  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  <span data-ttu-id="edd1a-176">Anahtar dosyası projenize eklemek için Çözüm Gezgini'nde proje adına sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="edd1a-176">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="edd1a-177">Proje Tasarımcısı'nda tıklatın **imzalama** sekmesinde **derlemeyi imzalamayı** onay kutusunu işaretleyin ve ardından, anahtar dosyasına gidin.</span><span class="sxs-lookup"><span data-stu-id="edd1a-177">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>  
  
5.  <span data-ttu-id="edd1a-178">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="edd1a-178">Build the solution.</span></span> <span data-ttu-id="edd1a-179">Derleme MyControls.dll adlı bir DLL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="edd1a-179">The build will produce a DLL named MyControls.dll.</span></span>  
  
## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="edd1a-180">WPF ana bilgisayar uygulaması uygulama</span><span class="sxs-lookup"><span data-stu-id="edd1a-180">Implementing the WPF Host Application</span></span>  
 <span data-ttu-id="edd1a-181">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uygulamanız tarafından kullanılan ana <xref:System.Windows.Forms.Integration.WindowsFormsHost> barındırmak için `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-181">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="edd1a-182">Uygulama işleyen `OnButtonClick` denetimden verileri almak için olay.</span><span class="sxs-lookup"><span data-stu-id="edd1a-182">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="edd1a-183">Ayrıca denetimin özelliklerinden bazıları değiştirebilmek için seçenek düğmeleri koleksiyonu vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="edd1a-183">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="edd1a-184">Aşağıdaki resimde tamamlanmış uygulama gösterilir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-184">The following illustration shows the finished application.</span></span>  
  
 <span data-ttu-id="edd1a-185">![Bir denetim katıştırılmış bir WPF sayfasında](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")</span><span class="sxs-lookup"><span data-stu-id="edd1a-185">![A control embedded in a WPF page](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")</span></span>  
<span data-ttu-id="edd1a-186">WPF uygulamasında denetimi gösteren tüm uygulamanın katıştırılmış</span><span class="sxs-lookup"><span data-stu-id="edd1a-186">The complete application, showing the control embedded in the WPF application</span></span>  
  
### <a name="creating-the-project"></a><span data-ttu-id="edd1a-187">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="edd1a-187">Creating the Project</span></span>  
 <span data-ttu-id="edd1a-188">Proje başlatmak için:</span><span class="sxs-lookup"><span data-stu-id="edd1a-188">To start the project:</span></span>  
  
1.  <span data-ttu-id="edd1a-189">Açık [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]seçip **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="edd1a-189">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>  
  
2.  <span data-ttu-id="edd1a-190">Pencere kategorisinde seçin **WPF uygulaması** şablonu.</span><span class="sxs-lookup"><span data-stu-id="edd1a-190">In the Window category, select the **WPF Application** template.</span></span>
  
3.  <span data-ttu-id="edd1a-191">Yeni proje adını `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-191">Name the new project `WpfHost`.</span></span>  
  
4.  <span data-ttu-id="edd1a-192">Konum için MyControls projesini içeren aynı üst düzey klasörü belirtin.</span><span class="sxs-lookup"><span data-stu-id="edd1a-192">For the location, specify the same top-level folder that contains the MyControls project.</span></span>  
  
5.  <span data-ttu-id="edd1a-193">Tıklayın **Tamam** projeyi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="edd1a-193">Click **OK** to create the project.</span></span>  
  
 <span data-ttu-id="edd1a-194">Ayrıca içeren DLL başvuruları eklemek gereken `MyControl1` ve diğer derlemeler.</span><span class="sxs-lookup"><span data-stu-id="edd1a-194">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>  
  
1.  <span data-ttu-id="edd1a-195">Çözüm Gezgini'nde proje adına sağ tıklayıp **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="edd1a-195">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="edd1a-196">Tıklayın **Gözat** sekmesini tıklatıp MyControls.dll içeren klasöre göz atın.</span><span class="sxs-lookup"><span data-stu-id="edd1a-196">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="edd1a-197">Bu kılavuz için bu klasör MyControls\bin\Debug'dır.</span><span class="sxs-lookup"><span data-stu-id="edd1a-197">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="edd1a-198">MyControls.dll seçin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="edd1a-198">Select MyControls.dll, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="edd1a-199">WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="edd1a-199">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
### <a name="implementing-the-basic-layout"></a><span data-ttu-id="edd1a-200">Temel düzeni uygulama</span><span class="sxs-lookup"><span data-stu-id="edd1a-200">Implementing the Basic Layout</span></span>  
 <span data-ttu-id="edd1a-201">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Ana bilgisayarının içinde MainWindow.xaml uygulama uygulanır.</span><span class="sxs-lookup"><span data-stu-id="edd1a-201">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="edd1a-202">Bu dosyayı içeren [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] düzenini tanımlar ve Windows Forms denetimi barındıran biçimlendirmesi.</span><span class="sxs-lookup"><span data-stu-id="edd1a-202">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="edd1a-203">Uygulamanın üç bölgelere ayrılmıştır:</span><span class="sxs-lookup"><span data-stu-id="edd1a-203">The application is divided into three regions:</span></span>  
  
-   <span data-ttu-id="edd1a-204">**Denetim özelliklerini** paneli denetimden çeşitli özelliklerini değiştirmek için kullanabileceğiniz bir seçenek düğmeleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-204">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>  
  
-   <span data-ttu-id="edd1a-205">**Denetiminden veri** paneli birkaç içerir <xref:System.Windows.Controls.TextBlock> verileri görüntüleyen öğeleri barındırılan denetiminden döndürdü.</span><span class="sxs-lookup"><span data-stu-id="edd1a-205">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>  
  
-   <span data-ttu-id="edd1a-206">Barındırılan denetim.</span><span class="sxs-lookup"><span data-stu-id="edd1a-206">The hosted control itself.</span></span>  
  
 <span data-ttu-id="edd1a-207">Aşağıdaki XAML içinde temel düzen gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-207">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="edd1a-208">Gerekli biçimlendirme konağa `MyControl1` Bu örnekte atlanmıştır, ancak daha sonra açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="edd1a-208">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>  
  
 <span data-ttu-id="edd1a-209">XAML içinde MainWindow.xaml aşağıdakiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="edd1a-209">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="edd1a-210">Visual Basic kullanıyorsanız, sınıfa değiştirme `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-210">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>  
  
 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 <span data-ttu-id="edd1a-211">İlk <xref:System.Windows.Controls.StackPanel> öğeyi içeren birkaç kümesi <xref:System.Windows.Controls.RadioButton> denetimden çeşitli varsayılan özelliklerini değiştirmenize olanak sağlayan denetimler.</span><span class="sxs-lookup"><span data-stu-id="edd1a-211">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="edd1a-212">Tarafından izlenen bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, hangi konakların `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-212">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="edd1a-213">En son <xref:System.Windows.Controls.StackPanel> öğeyi içeren birkaç <xref:System.Windows.Controls.TextBlock> barındırılan denetim tarafından döndürülen verileri görüntüleyen öğeleri.</span><span class="sxs-lookup"><span data-stu-id="edd1a-213">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="edd1a-214">Öğeleri sıralama ve <xref:System.Windows.Controls.DockPanel.Dock%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> öznitelik ayarlarını boşluklar veya bozulma ile bu denetimden penceresine ekleme.</span><span class="sxs-lookup"><span data-stu-id="edd1a-214">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>  
  
#### <a name="hosting-the-control"></a><span data-ttu-id="edd1a-215">Denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="edd1a-215">Hosting the Control</span></span>  
 <span data-ttu-id="edd1a-216">Önceki XAML aşağıdaki düzenlenmiş sürümü gereken öğeleri üzerinde odaklanır konağa `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-216">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>  
  
 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 <span data-ttu-id="edd1a-217">`xmlns` Ad alanı eşleme özniteliği için bir başvuru oluşturur `MyControls` barındırılan denetimi içeren ad alanı.</span><span class="sxs-lookup"><span data-stu-id="edd1a-217">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="edd1a-218">Bu eşlemeyi temsil sağlar `MyControl1` içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak `<mcl:MyControl1>`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-218">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>  
  
 <span data-ttu-id="edd1a-219">XAML içinde iki öğe barındırma işler:</span><span class="sxs-lookup"><span data-stu-id="edd1a-219">Two elements in the XAML handle the hosting:</span></span>  
  
-   <span data-ttu-id="edd1a-220">`WindowsFormsHost` temsil eden <xref:System.Windows.Forms.Integration.WindowsFormsHost> bir Windows Forms denetiminde barındırmanıza olanak sağlayan öğe bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="edd1a-220">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  
  
-   <span data-ttu-id="edd1a-221">`mcl:MyControl1`, temsil eden `MyControl1`, eklenen <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="edd1a-221">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="edd1a-222">Sonuç olarak, bu Windows Forms denetimini bir parçası olarak işlenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pencere ve uygulama denetimi ile kurabilir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-222">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>  
  
### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="edd1a-223">Arka plan kod dosyası uygulama</span><span class="sxs-lookup"><span data-stu-id="edd1a-223">Implementing the Code-Behind File</span></span>  
 <span data-ttu-id="edd1a-224">İşlevselliğini uygular yordam kodu MainWindow.xaml.vb veya MainWindow.xaml.cs, arka plan kod dosyasını içeren [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] önceki bölümde açıklanan.</span><span class="sxs-lookup"><span data-stu-id="edd1a-224">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="edd1a-225">Birincil görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="edd1a-225">The primary tasks are:</span></span>  
  
-   <span data-ttu-id="edd1a-226">Bir olay işleyici ekleme `MyControl1`'s `OnButtonClick` olay.</span><span class="sxs-lookup"><span data-stu-id="edd1a-226">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>  
  
-   <span data-ttu-id="edd1a-227">Çeşitli özelliklerini değiştirerek `MyControl1`seçeneği düğmelerinin koleksiyonunu nasıl ayarlanacağını göre.</span><span class="sxs-lookup"><span data-stu-id="edd1a-227">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>  
  
-   <span data-ttu-id="edd1a-228">Verileri görüntüleme denetim tarafından toplanır.</span><span class="sxs-lookup"><span data-stu-id="edd1a-228">Displaying the data collected by the control.</span></span>  
  
#### <a name="initializing-the-application"></a><span data-ttu-id="edd1a-229">Uygulamayı başlatma</span><span class="sxs-lookup"><span data-stu-id="edd1a-229">Initializing the Application</span></span>  
 <span data-ttu-id="edd1a-230">Başlatma kodu pencere için bir olay işleyicisi içindeki <xref:System.Windows.FrameworkElement.Loaded> olay ve denetim için bir olay işleyicisi ekler `OnButtonClick` olay.</span><span class="sxs-lookup"><span data-stu-id="edd1a-230">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>  
  
 <span data-ttu-id="edd1a-231">MainWindow.xaml.vb veya MainWindow.xaml.cs seçeneğinde, aşağıdaki kodu ekleyin `MainWindow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="edd1a-231">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 <span data-ttu-id="edd1a-232">Çünkü [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceden eklenen ele alınan `MyControl1` için <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt öğe koleksiyonuna çevirebilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> başvuru almak için `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-232">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="edd1a-233">Bir olay işleyicisi eklemek için bu başvuru sonra kullanabileceğiniz `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-233">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>  
  
 <span data-ttu-id="edd1a-234">Denetim kendisine bir başvuru sağlamanın yanı sıra <xref:System.Windows.Forms.Integration.WindowsFormsHost> uygulamadan değiştirebileceğiniz denetimin özelliklerini sayısını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="edd1a-234">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="edd1a-235">Başlatma kodunu uygulama daha sonra kullanmak için özel genel değişkenler bu değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="edd1a-235">The initialization code assigns those values to private global variables for later use in the application.</span></span>  
  
 <span data-ttu-id="edd1a-236">Türlerini kolayca erişebilmeleri `MyControls` DLL, aşağıdaki `Imports` veya `using` deyimini dosyanın en üstüne.</span><span class="sxs-lookup"><span data-stu-id="edd1a-236">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="edd1a-237">OnButtonClick olayını işleme</span><span class="sxs-lookup"><span data-stu-id="edd1a-237">Handling the OnButtonClick Event</span></span>  
 <span data-ttu-id="edd1a-238">`MyControl1` başlatır `OnButtonClick` kullanıcı herhangi bir denetimin düğmesini tıkladığında bir olay.</span><span class="sxs-lookup"><span data-stu-id="edd1a-238">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>  
  
 <span data-ttu-id="edd1a-239">Aşağıdaki kodu ekleyin `MainWindow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="edd1a-239">Add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 <span data-ttu-id="edd1a-240">Metin kutularına veri paketlenmiştir `MyControlEventArgs` nesne.</span><span class="sxs-lookup"><span data-stu-id="edd1a-240">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="edd1a-241">Kullanıcı tıklarsa **Tamam** düğmesi olay işleyicisi, verileri ayıklayan ve panelinde görüntüler `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="edd1a-241">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>  
  
#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="edd1a-242">Denetimin özelliklerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="edd1a-242">Modifying the Control’s Properties</span></span>  
 <span data-ttu-id="edd1a-243"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi birkaç barındırılan denetimin varsayılan özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-243">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="edd1a-244">Sonuç olarak, uygulamanızı daha yakından ayarlamalar denetiminin görünümünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edd1a-244">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="edd1a-245">Seçenek düğmeleri sol bölmede kümesi birkaç rengini ve yazı tipi özelliklerini değiştirmek kullanıcının etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="edd1a-245">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="edd1a-246">Her bir düğmeler kümesi için bir işleyici sahip <xref:System.Windows.Controls.Primitives.ButtonBase.Click> kullanıcının seçenek düğmesi seçimlerini algılar ve karşılık gelen özelliği denetimde değiştiren olay.</span><span class="sxs-lookup"><span data-stu-id="edd1a-246">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>  
  
 <span data-ttu-id="edd1a-247">Aşağıdaki kodu ekleyin `MainWindow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="edd1a-247">Add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="edd1a-248">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="edd1a-248">Build and run the application.</span></span> <span data-ttu-id="edd1a-249">Windows Forms bileşik denetimini içinde metin ekleyin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="edd1a-249">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="edd1a-250">Metin etiketler görünür.</span><span class="sxs-lookup"><span data-stu-id="edd1a-250">The text appears in the labels.</span></span> <span data-ttu-id="edd1a-251">Farklı radyo düğmeleri, denetimin üzerindeki etkisini görmek için tıklayın.</span><span class="sxs-lookup"><span data-stu-id="edd1a-251">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edd1a-252">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="edd1a-252">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="edd1a-253">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="edd1a-253">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [<span data-ttu-id="edd1a-254">İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="edd1a-254">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="edd1a-255">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="edd1a-255">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
