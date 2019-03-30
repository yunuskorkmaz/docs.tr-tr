---
title: "İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 50d85b74b523c8985bd0d3d407097a4f42cfeb60
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654230"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="9787e-102">İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="9787e-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="9787e-103">uygulamaları oluşturmak için zengin bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="9787e-103">provides a rich environment for creating applications.</span></span> <span data-ttu-id="9787e-104">Önemli ölçüde yatırımınız varsa [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu olabilir en az yeniden daha etkili kodda bazıları, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama yerine baştan yeniden.</span><span class="sxs-lookup"><span data-stu-id="9787e-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="9787e-105">Mevcut Windows Forms denetimleri olduğunda en yaygın senaryodur.</span><span class="sxs-lookup"><span data-stu-id="9787e-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="9787e-106">Bazı durumlarda, bile bu denetimleri için kaynak koduna erişim olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9787e-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="9787e-107">gibi denetimleri barındırma için basit bir yordam sağlar bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="9787e-107">provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="9787e-108">Örneğin, kullanabileceğiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çoğu barındırırken, programlama için <xref:System.Windows.Forms.DataGridView> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="9787e-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="9787e-109">Bu izlenecek yolda veri girişi gerçekleştirmek için bir Windows Forms bileşik denetimini barındıran bir uygulama aracılığıyla adımları bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="9787e-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="9787e-110">Bileşik Denetim DLL içinde paketlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9787e-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="9787e-111">Bu genel yordam, daha karmaşık uygulamalar ve denetimler için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="9787e-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="9787e-112">Bu izlenecek yol Görünüm ve işlevselliği için neredeyse aynı olacak şekilde tasarlanan [izlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9787e-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="9787e-113">Barındırma senaryo tersine, birincil farktır.</span><span class="sxs-lookup"><span data-stu-id="9787e-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="9787e-114">İzlenecek yol, iki bölüme ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="9787e-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="9787e-115">İlk bölüm, Windows Forms bileşik denetimini uygulamasını kısaca açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9787e-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="9787e-116">İkinci bölüm içinde bileşik denetimini barındırmak nasıl ayrıntılı olarak ele alınmaktadır bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama denetim olaylarını almak ve denetim özelliklerini bazılarına erişmek.</span><span class="sxs-lookup"><span data-stu-id="9787e-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="9787e-117">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="9787e-117">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="9787e-118">Windows Forms bileşik denetimini uygulama.</span><span class="sxs-lookup"><span data-stu-id="9787e-118">Implementing the Windows Forms composite control.</span></span>  
  
-   <span data-ttu-id="9787e-119">WPF ana bilgisayar uygulaması oluşturma.</span><span class="sxs-lookup"><span data-stu-id="9787e-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="9787e-120">Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [bir WPF Örneği'nde Windows Forms bileşik denetimini barındırma](https://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="9787e-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9787e-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="9787e-121">Prerequisites</span></span>  

<span data-ttu-id="9787e-122">Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="9787e-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="9787e-123">Windows Forms bileşik denetimini uygulama</span><span class="sxs-lookup"><span data-stu-id="9787e-123">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="9787e-124">Bu örnekte kullanılan Windows Forms bileşik denetimini basit veri girişi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="9787e-124">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="9787e-125">Bu form kullanıcının adı ve adresi alır ve ana bilgisayar için bu bilgileri döndürmek için bir özel olay kullanır.</span><span class="sxs-lookup"><span data-stu-id="9787e-125">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="9787e-126">İşlenen denetimi aşağıda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9787e-126">The following illustration shows the rendered control.</span></span>  

 <span data-ttu-id="9787e-127">Aşağıdaki resimde, bir Windows Forms bileşik denetimini gösterir:</span><span class="sxs-lookup"><span data-stu-id="9787e-127">The following image shows a Windows Forms composite control:</span></span>  

 ![Basit bir Windows Forms denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a><span data-ttu-id="9787e-129">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9787e-129">Creating the Project</span></span>  
 <span data-ttu-id="9787e-130">Proje başlatmak için:</span><span class="sxs-lookup"><span data-stu-id="9787e-130">To start the project:</span></span>  
  
1.  <span data-ttu-id="9787e-131">Başlatma [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]açın **yeni proje** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="9787e-131">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="9787e-132">Pencere kategorisinde seçin **Windows Forms Denetim Kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="9787e-132">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3.  <span data-ttu-id="9787e-133">Yeni proje adını `MyControls`.</span><span class="sxs-lookup"><span data-stu-id="9787e-133">Name the new project `MyControls`.</span></span>  
  
4.  <span data-ttu-id="9787e-134">Konum için bir kolayca adlandırılmış üst düzey klasör gibi belirtin `WpfHostingWindowsFormsControl`.</span><span class="sxs-lookup"><span data-stu-id="9787e-134">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="9787e-135">Daha sonra ana bilgisayar uygulaması bu klasöre koyacaktır.</span><span class="sxs-lookup"><span data-stu-id="9787e-135">Later, you will put the host application in this folder.</span></span>  
  
5.  <span data-ttu-id="9787e-136">Tıklayın **Tamam** projeyi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9787e-136">Click **OK** to create the project.</span></span> <span data-ttu-id="9787e-137">Varsayılan proje adlı tek bir denetim içeren `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="9787e-137">The default project contains a single control named `UserControl1`.</span></span>  
  
6.  <span data-ttu-id="9787e-138">Çözüm Gezgini'nde, yeniden adlandırma `UserControl1` için `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="9787e-138">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="9787e-139">Projenize aşağıdaki sistem DLL'lerini başvuruları olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9787e-139">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="9787e-140">Bu DLL'leri birini varsayılan olarak dahil edilmez, bunları projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9787e-140">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
-   <span data-ttu-id="9787e-141">Sistem</span><span class="sxs-lookup"><span data-stu-id="9787e-141">System</span></span>  
  
-   <span data-ttu-id="9787e-142">System.Data</span><span class="sxs-lookup"><span data-stu-id="9787e-142">System.Data</span></span>  
  
-   <span data-ttu-id="9787e-143">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="9787e-143">System.Drawing</span></span>  
  
-   <span data-ttu-id="9787e-144">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="9787e-144">System.Windows.Forms</span></span>  
  
-   <span data-ttu-id="9787e-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="9787e-145">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="9787e-146">Formu için denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="9787e-146">Adding Controls to the Form</span></span>  
 <span data-ttu-id="9787e-147">Formu için denetimler eklemek için:</span><span class="sxs-lookup"><span data-stu-id="9787e-147">To add controls to the form:</span></span>  
  
-   <span data-ttu-id="9787e-148">Açık `MyControl1` Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="9787e-148">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="9787e-149">Beş ekleme <xref:System.Windows.Forms.Label> denetimleri ve bunlara karşılık gelen <xref:System.Windows.Forms.TextBox> denetimleri, boyutu ve formdaki yukarıdaki çizimin olduğu gibi düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="9787e-149">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="9787e-150">Örnekte, <xref:System.Windows.Forms.TextBox> denetimleri adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="9787e-150">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 <span data-ttu-id="9787e-151">İki ekleme <xref:System.Windows.Forms.Button> etiketli denetimler **Tamam** ve **iptal**.</span><span class="sxs-lookup"><span data-stu-id="9787e-151">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="9787e-152">Bu örnekte düğme adlarıdır `btnOK` ve `btnCancel`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="9787e-152">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="9787e-153">Destek kodu uygulama</span><span class="sxs-lookup"><span data-stu-id="9787e-153">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="9787e-154">Formun kod Görünümü'nde açın.</span><span class="sxs-lookup"><span data-stu-id="9787e-154">Open the form in code view.</span></span> <span data-ttu-id="9787e-155">Ana bilgisayar için toplanan verileri özel yükselterek denetimini döndürür `OnButtonClick` olay.</span><span class="sxs-lookup"><span data-stu-id="9787e-155">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="9787e-156">Verileri olay bağımsız değişkeni nesnesinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="9787e-156">The data is contained in the event argument object.</span></span> <span data-ttu-id="9787e-157">Aşağıdaki kod, olay ve temsilci bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9787e-157">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="9787e-158">Aşağıdaki kodu ekleyin `MyControl1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9787e-158">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 <span data-ttu-id="9787e-159">`MyControlEventArgs` Sınıfı konağa döndürülmesi gereken bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="9787e-159">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>

 <span data-ttu-id="9787e-160">Aşağıdaki sınıf formuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9787e-160">Add the following class to the form.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 <span data-ttu-id="9787e-161">Kullanıcı tıkladığında **Tamam** veya **iptal** düğmesi <xref:System.Windows.Forms.Control.Click> olay işleyicileri oluşturma bir `MyControlEventArgs` veri içeren nesne ve başlatır `OnButtonClick` olay.</span><span class="sxs-lookup"><span data-stu-id="9787e-161">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="9787e-162">Olay bağımsız değişkenin iki işleyiciler arasındaki tek fark, `IsOK` özelliği.</span><span class="sxs-lookup"><span data-stu-id="9787e-162">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="9787e-163">Bu özellik ana bilgisayarın hangi düğmesine tıklandığını belirleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="9787e-163">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="9787e-164">Ayarlanmış `true` için **Tamam** düğmesi ve `false` için **iptal** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9787e-164">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="9787e-165">Aşağıdaki kod, iki düğmesi işleyicileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="9787e-165">The following code shows the two button handlers.</span></span>

 <span data-ttu-id="9787e-166">Aşağıdaki kodu ekleyin `MyControl1` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9787e-166">Add the following code to the `MyControl1` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="9787e-167">Derlemeyi güçlü bir isim verilmesi ve bütünleştirilmiş kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="9787e-167">Giving the Assembly a Strong Name and Building the Assembly</span></span>
 <span data-ttu-id="9787e-168">Tarafından başvurulabilmesi derlemenin bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama, sağlam bir adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9787e-168">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="9787e-169">Güçlü bir ad oluşturmak için bir anahtar dosyası ile Sn.exe oluşturun ve projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9787e-169">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>

1.  <span data-ttu-id="9787e-170">Açık bir [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="9787e-170">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="9787e-171">Bunu yapmak için tıklatın **Başlat** menüsüne ve ardından **tüm programlar/Microsoft Visual Studio 2010/Visual Studio Araçları/Visual Studio komut istemi**.</span><span class="sxs-lookup"><span data-stu-id="9787e-171">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="9787e-172">Bu, özel ortam değişkenleriyle bir konsol penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="9787e-172">This launches a console window with customized environment variables.</span></span>

2.  <span data-ttu-id="9787e-173">Komut isteminde kullanmak `cd` proje klasörünüzün Git komutu.</span><span class="sxs-lookup"><span data-stu-id="9787e-173">At the command prompt, use the `cd` command to go to your project folder.</span></span>

3.  <span data-ttu-id="9787e-174">Aşağıdaki komutu çalıştırarak MyControls.snk adlı bir anahtar dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9787e-174">Generate a key file named MyControls.snk by running the following command.</span></span>

    ```
    Sn.exe -k MyControls.snk
    ```

4.  <span data-ttu-id="9787e-175">Anahtar dosyası projenize eklemek için Çözüm Gezgini'nde proje adına sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="9787e-175">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="9787e-176">Proje Tasarımcısı'nda tıklatın **imzalama** sekmesinde **derlemeyi imzalamayı** onay kutusunu işaretleyin ve ardından, anahtar dosyasına gidin.</span><span class="sxs-lookup"><span data-stu-id="9787e-176">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>

5.  <span data-ttu-id="9787e-177">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9787e-177">Build the solution.</span></span> <span data-ttu-id="9787e-178">Derleme MyControls.dll adlı bir DLL oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9787e-178">The build will produce a DLL named MyControls.dll.</span></span>

## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="9787e-179">WPF ana bilgisayar uygulaması uygulama</span><span class="sxs-lookup"><span data-stu-id="9787e-179">Implementing the WPF Host Application</span></span>
 <span data-ttu-id="9787e-180">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uygulamanız tarafından kullanılan ana <xref:System.Windows.Forms.Integration.WindowsFormsHost> barındırmak için `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="9787e-180">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="9787e-181">Uygulama işleyen `OnButtonClick` denetimden verileri almak için olay.</span><span class="sxs-lookup"><span data-stu-id="9787e-181">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="9787e-182">Ayrıca denetimin özelliklerinden bazıları değiştirebilmek için seçenek düğmeleri koleksiyonu vardır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="9787e-182">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="9787e-183">Aşağıdaki resimde tamamlanmış uygulama gösterilir.</span><span class="sxs-lookup"><span data-stu-id="9787e-183">The following illustration shows the finished application.</span></span>

<span data-ttu-id="9787e-184">Aşağıdaki görüntüde, WPF uygulamasında katıştırılmış denetime dahil olmak üzere tüm uygulamanın gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9787e-184">The following image shows the complete application, including the control embedded in the WPF application:</span></span>

 ![Bir denetimi gösteren ekran görüntüsü, bir WPF sayfasındaki katıştırılmış.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a><span data-ttu-id="9787e-186">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9787e-186">Creating the Project</span></span>
 <span data-ttu-id="9787e-187">Proje başlatmak için:</span><span class="sxs-lookup"><span data-stu-id="9787e-187">To start the project:</span></span>

1.  <span data-ttu-id="9787e-188">Açık [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]seçip **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="9787e-188">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>

2.  <span data-ttu-id="9787e-189">Pencere kategorisinde seçin **WPF uygulaması** şablonu.</span><span class="sxs-lookup"><span data-stu-id="9787e-189">In the Window category, select the **WPF Application** template.</span></span>

3.  <span data-ttu-id="9787e-190">Yeni proje adını `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="9787e-190">Name the new project `WpfHost`.</span></span>

4.  <span data-ttu-id="9787e-191">Konum için MyControls projesini içeren aynı üst düzey klasörü belirtin.</span><span class="sxs-lookup"><span data-stu-id="9787e-191">For the location, specify the same top-level folder that contains the MyControls project.</span></span>

5.  <span data-ttu-id="9787e-192">Tıklayın **Tamam** projeyi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9787e-192">Click **OK** to create the project.</span></span>

 <span data-ttu-id="9787e-193">Ayrıca içeren DLL başvuruları eklemek gereken `MyControl1` ve diğer derlemeler.</span><span class="sxs-lookup"><span data-stu-id="9787e-193">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>

1.  <span data-ttu-id="9787e-194">Çözüm Gezgini'nde proje adına sağ tıklayıp **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="9787e-194">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>

2.  <span data-ttu-id="9787e-195">Tıklayın **Gözat** sekmesini tıklatıp MyControls.dll içeren klasöre göz atın.</span><span class="sxs-lookup"><span data-stu-id="9787e-195">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="9787e-196">Bu kılavuz için bu klasör MyControls\bin\Debug'dır.</span><span class="sxs-lookup"><span data-stu-id="9787e-196">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>

3.  <span data-ttu-id="9787e-197">MyControls.dll seçin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="9787e-197">Select MyControls.dll, and then click **OK**.</span></span>

4.  <span data-ttu-id="9787e-198">WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9787e-198">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

### <a name="implementing-the-basic-layout"></a><span data-ttu-id="9787e-199">Temel düzeni uygulama</span><span class="sxs-lookup"><span data-stu-id="9787e-199">Implementing the Basic Layout</span></span>
 <span data-ttu-id="9787e-200">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Ana bilgisayarının içinde MainWindow.xaml uygulama uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9787e-200">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="9787e-201">Bu dosyayı içeren [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] düzenini tanımlar ve Windows Forms denetimi barındıran biçimlendirmesi.</span><span class="sxs-lookup"><span data-stu-id="9787e-201">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="9787e-202">Uygulamanın üç bölgelere ayrılmıştır:</span><span class="sxs-lookup"><span data-stu-id="9787e-202">The application is divided into three regions:</span></span>

-   <span data-ttu-id="9787e-203">**Denetim özelliklerini** paneli denetimden çeşitli özelliklerini değiştirmek için kullanabileceğiniz bir seçenek düğmeleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="9787e-203">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>

-   <span data-ttu-id="9787e-204">**Denetiminden veri** paneli birkaç içerir <xref:System.Windows.Controls.TextBlock> verileri görüntüleyen öğeleri barındırılan denetiminden döndürdü.</span><span class="sxs-lookup"><span data-stu-id="9787e-204">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>

-   <span data-ttu-id="9787e-205">Barındırılan denetim.</span><span class="sxs-lookup"><span data-stu-id="9787e-205">The hosted control itself.</span></span>

 <span data-ttu-id="9787e-206">Aşağıdaki XAML içinde temel düzen gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9787e-206">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="9787e-207">Gerekli biçimlendirme konağa `MyControl1` Bu örnekte atlanmıştır, ancak daha sonra açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="9787e-207">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>

 <span data-ttu-id="9787e-208">XAML içinde MainWindow.xaml aşağıdakiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9787e-208">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="9787e-209">Visual Basic kullanıyorsanız, sınıfa değiştirme `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="9787e-209">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 <span data-ttu-id="9787e-210">İlk <xref:System.Windows.Controls.StackPanel> öğeyi içeren birkaç kümesi <xref:System.Windows.Controls.RadioButton> denetimden çeşitli varsayılan özelliklerini değiştirmenize olanak sağlayan denetimler.</span><span class="sxs-lookup"><span data-stu-id="9787e-210">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="9787e-211">Tarafından izlenen bir <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, hangi konakların `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="9787e-211">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="9787e-212">En son <xref:System.Windows.Controls.StackPanel> öğeyi içeren birkaç <xref:System.Windows.Controls.TextBlock> barındırılan denetim tarafından döndürülen verileri görüntüleyen öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9787e-212">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="9787e-213">Öğeleri sıralama ve <xref:System.Windows.Controls.DockPanel.Dock%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> öznitelik ayarlarını boşluklar veya bozulma ile bu denetimden penceresine ekleme.</span><span class="sxs-lookup"><span data-stu-id="9787e-213">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>

#### <a name="hosting-the-control"></a><span data-ttu-id="9787e-214">Denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="9787e-214">Hosting the Control</span></span>
 <span data-ttu-id="9787e-215">Önceki XAML aşağıdaki düzenlenmiş sürümü gereken öğeleri üzerinde odaklanır konağa `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="9787e-215">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 <span data-ttu-id="9787e-216">`xmlns` Ad alanı eşleme özniteliği için bir başvuru oluşturur `MyControls` barındırılan denetimi içeren ad alanı.</span><span class="sxs-lookup"><span data-stu-id="9787e-216">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="9787e-217">Bu eşlemeyi temsil sağlar `MyControl1` içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak `<mcl:MyControl1>`.</span><span class="sxs-lookup"><span data-stu-id="9787e-217">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>

 <span data-ttu-id="9787e-218">XAML içinde iki öğe barındırma işler:</span><span class="sxs-lookup"><span data-stu-id="9787e-218">Two elements in the XAML handle the hosting:</span></span>

-   <span data-ttu-id="9787e-219">`WindowsFormsHost` temsil eden <xref:System.Windows.Forms.Integration.WindowsFormsHost> bir Windows Forms denetiminde barındırmanıza olanak sağlayan öğe bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="9787e-219">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

-   <span data-ttu-id="9787e-220">`mcl:MyControl1`, temsil eden `MyControl1`, eklenen <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9787e-220">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="9787e-221">Sonuç olarak, bu Windows Forms denetimini bir parçası olarak işlenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pencere ve uygulama denetimi ile kurabilir.</span><span class="sxs-lookup"><span data-stu-id="9787e-221">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>

### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="9787e-222">Arka plan kod dosyası uygulama</span><span class="sxs-lookup"><span data-stu-id="9787e-222">Implementing the Code-Behind File</span></span>
 <span data-ttu-id="9787e-223">İşlevselliğini uygular yordam kodu MainWindow.xaml.vb veya MainWindow.xaml.cs, arka plan kod dosyasını içeren [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] önceki bölümde açıklanan.</span><span class="sxs-lookup"><span data-stu-id="9787e-223">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="9787e-224">Birincil görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9787e-224">The primary tasks are:</span></span>

-   <span data-ttu-id="9787e-225">Bir olay işleyici ekleme `MyControl1`'s `OnButtonClick` olay.</span><span class="sxs-lookup"><span data-stu-id="9787e-225">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>

-   <span data-ttu-id="9787e-226">Çeşitli özelliklerini değiştirerek `MyControl1`seçeneği düğmelerinin koleksiyonunu nasıl ayarlanacağını göre.</span><span class="sxs-lookup"><span data-stu-id="9787e-226">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>

-   <span data-ttu-id="9787e-227">Verileri görüntüleme denetim tarafından toplanır.</span><span class="sxs-lookup"><span data-stu-id="9787e-227">Displaying the data collected by the control.</span></span>

#### <a name="initializing-the-application"></a><span data-ttu-id="9787e-228">Uygulamayı başlatma</span><span class="sxs-lookup"><span data-stu-id="9787e-228">Initializing the Application</span></span>
 <span data-ttu-id="9787e-229">Başlatma kodu pencere için bir olay işleyicisi içindeki <xref:System.Windows.FrameworkElement.Loaded> olay ve denetim için bir olay işleyicisi ekler `OnButtonClick` olay.</span><span class="sxs-lookup"><span data-stu-id="9787e-229">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>

 <span data-ttu-id="9787e-230">MainWindow.xaml.vb veya MainWindow.xaml.cs seçeneğinde, aşağıdaki kodu ekleyin `MainWindow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9787e-230">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <span data-ttu-id="9787e-231">Çünkü [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] önceden eklenen ele alınan `MyControl1` için <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt öğe koleksiyonuna çevirebilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> başvuru almak için `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="9787e-231">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="9787e-232">Bir olay işleyicisi eklemek için bu başvuru sonra kullanabileceğiniz `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="9787e-232">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>

 <span data-ttu-id="9787e-233">Denetim kendisine bir başvuru sağlamanın yanı sıra <xref:System.Windows.Forms.Integration.WindowsFormsHost> uygulamadan değiştirebileceğiniz denetimin özelliklerini sayısını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="9787e-233">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="9787e-234">Başlatma kodunu uygulama daha sonra kullanmak için özel genel değişkenler bu değerleri atar.</span><span class="sxs-lookup"><span data-stu-id="9787e-234">The initialization code assigns those values to private global variables for later use in the application.</span></span>

 <span data-ttu-id="9787e-235">Türlerini kolayca erişebilmeleri `MyControls` DLL, aşağıdaki `Imports` veya `using` deyimini dosyanın en üstüne.</span><span class="sxs-lookup"><span data-stu-id="9787e-235">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="9787e-236">OnButtonClick olayını işleme</span><span class="sxs-lookup"><span data-stu-id="9787e-236">Handling the OnButtonClick Event</span></span>
 <span data-ttu-id="9787e-237">`MyControl1` başlatır `OnButtonClick` kullanıcı herhangi bir denetimin düğmesini tıkladığında bir olay.</span><span class="sxs-lookup"><span data-stu-id="9787e-237">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>

 <span data-ttu-id="9787e-238">Aşağıdaki kodu ekleyin `MainWindow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9787e-238">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 <span data-ttu-id="9787e-239">Metin kutularına veri paketlenmiştir `MyControlEventArgs` nesne.</span><span class="sxs-lookup"><span data-stu-id="9787e-239">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="9787e-240">Kullanıcı tıklarsa **Tamam** düğmesi olay işleyicisi, verileri ayıklayan ve panelinde görüntüler `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="9787e-240">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>

#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="9787e-241">Denetimin özelliklerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="9787e-241">Modifying the Control’s Properties</span></span>
 <span data-ttu-id="9787e-242"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi birkaç barındırılan denetimin varsayılan özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9787e-242">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="9787e-243">Sonuç olarak, uygulamanızı daha yakından ayarlamalar denetiminin görünümünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9787e-243">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="9787e-244">Seçenek düğmeleri sol bölmede kümesi birkaç rengini ve yazı tipi özelliklerini değiştirmek kullanıcının etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="9787e-244">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="9787e-245">Her bir düğmeler kümesi için bir işleyici sahip <xref:System.Windows.Controls.Primitives.ButtonBase.Click> kullanıcının seçenek düğmesi seçimlerini algılar ve karşılık gelen özelliği denetimde değiştiren olay.</span><span class="sxs-lookup"><span data-stu-id="9787e-245">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>

 <span data-ttu-id="9787e-246">Aşağıdaki kodu ekleyin `MainWindow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9787e-246">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="9787e-247">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9787e-247">Build and run the application.</span></span> <span data-ttu-id="9787e-248">Windows Forms bileşik denetimini içinde metin ekleyin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="9787e-248">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="9787e-249">Metin etiketler görünür.</span><span class="sxs-lookup"><span data-stu-id="9787e-249">The text appears in the labels.</span></span> <span data-ttu-id="9787e-250">Farklı radyo düğmeleri, denetimin üzerindeki etkisini görmek için tıklayın.</span><span class="sxs-lookup"><span data-stu-id="9787e-250">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9787e-251">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9787e-251">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="9787e-252">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="9787e-252">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="9787e-253">İzlenecek yol: WPF'de Windows Forms denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="9787e-253">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="9787e-254">İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma</span><span class="sxs-lookup"><span data-stu-id="9787e-254">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
