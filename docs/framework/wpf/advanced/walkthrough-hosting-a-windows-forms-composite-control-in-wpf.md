---
title: WPF 'de Windows Forms Bileşik denetim barındırma
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 22eb323d1c1921832630d1d1b30463b4ecb7d1fd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794237"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="f8adf-102">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="f8adf-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="f8adf-103">, uygulamalar oluşturmak için zengin bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8adf-103">provides a rich environment for creating applications.</span></span> <span data-ttu-id="f8adf-104">Ancak Windows Forms kodda önemli bir yatırımınız olduğunda, sıfırdan yazmak yerine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanızda bu kodların en az bir kısmını yeniden kullanmak daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-104">However, when you have a substantial investment in Windows Forms code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="f8adf-105">En yaygın senaryo, Windows Forms denetimlerinizi var.</span><span class="sxs-lookup"><span data-stu-id="f8adf-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="f8adf-106">Bazı durumlarda, bu denetimlerin kaynak koduna bile erişiminiz olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="f8adf-107">, bu denetimleri bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasında barındırmak için kolay bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8adf-107">provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="f8adf-108">Örneğin, özelleştirilmiş <xref:System.Windows.Forms.DataGridView> denetimlerinizi barındırırken birçok programlama için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8adf-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="f8adf-109">Bu izlenecek yol, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasında veri girişi gerçekleştirmek üzere Windows Forms Bileşik bir denetim barındıran bir uygulamada size kılavuzluk ediyor.</span><span class="sxs-lookup"><span data-stu-id="f8adf-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="f8adf-110">Bileşik denetim bir DLL içinde paketlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="f8adf-111">Bu genel yordam, daha karmaşık uygulamalar ve denetimler için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="f8adf-112">Bu izlenecek yol, görünüm ve işlevlerle neredeyse özdeş olacak şekilde tasarlanmıştır [: WINDOWS Forms WPF bileşik denetimini barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f8adf-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="f8adf-113">Birincil fark, barındırma senaryosunun tersine çevrilme olur.</span><span class="sxs-lookup"><span data-stu-id="f8adf-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="f8adf-114">İzlenecek yol iki bölüme ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="f8adf-115">İlk bölüm Windows Forms Bileşik denetimin uygulamasını kısaca açıklar.</span><span class="sxs-lookup"><span data-stu-id="f8adf-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="f8adf-116">İkinci bölüm, bileşik denetimin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulamada nasıl barındırılacağını, denetimden olayları nasıl alacağını ve denetimin bazı özelliklerine nasıl erişebileceğini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="f8adf-117">Bu izlenecek yolda gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f8adf-117">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="f8adf-118">Windows Forms Bileşik denetimi uygulama.</span><span class="sxs-lookup"><span data-stu-id="f8adf-118">Implementing the Windows Forms composite control.</span></span>  
  
- <span data-ttu-id="f8adf-119">WPF konak uygulamasını uygulama.</span><span class="sxs-lookup"><span data-stu-id="f8adf-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="f8adf-120">Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [WPF örneğinde Windows Forms Bileşik denetimi barındırma](https://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="f8adf-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f8adf-121">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f8adf-121">Prerequisites</span></span>  

<span data-ttu-id="f8adf-122">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="f8adf-123">Windows Forms Bileşik denetimi uygulama</span><span class="sxs-lookup"><span data-stu-id="f8adf-123">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="f8adf-124">Bu örnekte kullanılan Windows Forms Bileşik denetim basit bir veri girişi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-124">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="f8adf-125">Bu form kullanıcının adını ve adresini alır ve bu bilgileri konağa döndürmek için özel bir olay kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-125">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="f8adf-126">Aşağıdaki çizimde işlenmiş denetim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-126">The following illustration shows the rendered control.</span></span>  

 <span data-ttu-id="f8adf-127">Aşağıdaki görüntüde Windows Forms Bileşik bir denetim gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f8adf-127">The following image shows a Windows Forms composite control:</span></span>  

 ![Basit bir Windows Forms denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a><span data-ttu-id="f8adf-129">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8adf-129">Creating the Project</span></span>  
 <span data-ttu-id="f8adf-130">Projeyi başlatmak için:</span><span class="sxs-lookup"><span data-stu-id="f8adf-130">To start the project:</span></span>  
  
1. <span data-ttu-id="f8adf-131">Visual Studio 'yu başlatın ve **Yeni proje** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-131">Launch Visual Studio, and open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="f8adf-132">Pencere kategorisinde **Windows Forms denetim kitaplığı** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-132">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3. <span data-ttu-id="f8adf-133">Yeni proje `MyControls`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-133">Name the new project `MyControls`.</span></span>  
  
4. <span data-ttu-id="f8adf-134">Konum için `WpfHostingWindowsFormsControl`gibi kolay adlandırılmış bir üst düzey klasör belirtin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-134">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="f8adf-135">Daha sonra, ana bilgisayar uygulamasını bu klasöre yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8adf-135">Later, you will put the host application in this folder.</span></span>  
  
5. <span data-ttu-id="f8adf-136">Projeyi oluşturmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-136">Click **OK** to create the project.</span></span> <span data-ttu-id="f8adf-137">Varsayılan proje, `UserControl1`adlı tek bir denetim içerir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-137">The default project contains a single control named `UserControl1`.</span></span>  
  
6. <span data-ttu-id="f8adf-138">Çözüm Gezgini `UserControl1` `MyControl1`olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-138">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="f8adf-139">Projenizin aşağıdaki sistem dll 'Lerine başvuruları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-139">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="f8adf-140">Bu dll 'Lerden herhangi biri varsayılan olarak dahil edilmez, bunları projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-140">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
- <span data-ttu-id="f8adf-141">Sistem</span><span class="sxs-lookup"><span data-stu-id="f8adf-141">System</span></span>  
  
- <span data-ttu-id="f8adf-142">System.Data</span><span class="sxs-lookup"><span data-stu-id="f8adf-142">System.Data</span></span>  
  
- <span data-ttu-id="f8adf-143">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="f8adf-143">System.Drawing</span></span>  
  
- <span data-ttu-id="f8adf-144">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="f8adf-144">System.Windows.Forms</span></span>  
  
- <span data-ttu-id="f8adf-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="f8adf-145">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="f8adf-146">Forma denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="f8adf-146">Adding Controls to the Form</span></span>  
 <span data-ttu-id="f8adf-147">Forma denetim eklemek için:</span><span class="sxs-lookup"><span data-stu-id="f8adf-147">To add controls to the form:</span></span>  
  
- <span data-ttu-id="f8adf-148">Tasarımcıda `MyControl1` açın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-148">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="f8adf-149">Form üzerinde, önceki çizimde oldukları gibi boyutlandırılmış ve düzenlenmiş beş <xref:System.Windows.Forms.Label> denetimi ve bunlara karşılık gelen <xref:System.Windows.Forms.TextBox> denetimlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-149">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="f8adf-150">Örnekte <xref:System.Windows.Forms.TextBox> denetimleri şu şekilde adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="f8adf-150">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 <span data-ttu-id="f8adf-151">**Tamam** ve **iptal**etiketli iki <xref:System.Windows.Forms.Button> denetimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-151">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="f8adf-152">Örnekte, düğme adları sırasıyla `btnOK` ve `btnCancel`.</span><span class="sxs-lookup"><span data-stu-id="f8adf-152">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="f8adf-153">Destekleyici kodu uygulama</span><span class="sxs-lookup"><span data-stu-id="f8adf-153">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="f8adf-154">Formu kod görünümünde açın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-154">Open the form in code view.</span></span> <span data-ttu-id="f8adf-155">Denetim, toplanan verileri özel `OnButtonClick` olayını yükselterek ana bilgisayarına döndürür.</span><span class="sxs-lookup"><span data-stu-id="f8adf-155">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="f8adf-156">Veriler, olay bağımsız değişkeni nesnesinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-156">The data is contained in the event argument object.</span></span> <span data-ttu-id="f8adf-157">Aşağıdaki kod, olay ve temsilci bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-157">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="f8adf-158">Aşağıdaki kodu `MyControl1` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-158">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 <span data-ttu-id="f8adf-159">`MyControlEventArgs` sınıfı, konağa döndürülecek bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-159">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>

 <span data-ttu-id="f8adf-160">Aşağıdaki sınıfı forma ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-160">Add the following class to the form.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 <span data-ttu-id="f8adf-161">Kullanıcı **Tamam** veya **iptal** düğmesine tıkladığında, <xref:System.Windows.Forms.Control.Click> olay işleyicileri verileri içeren ve `OnButtonClick` olayını başlatan bir `MyControlEventArgs` nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8adf-161">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="f8adf-162">İki işleyici arasındaki tek fark, olay bağımsız değişkeninin `IsOK` özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-162">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="f8adf-163">Bu özellik, ana bilgisayarın hangi düğmeye tıklandığını belirlemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8adf-163">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="f8adf-164">**Tamam** düğmesi için `true` olarak ayarlanır ve **iptal** düğmesi için `false`.</span><span class="sxs-lookup"><span data-stu-id="f8adf-164">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="f8adf-165">Aşağıdaki kod iki düğme işleyicisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-165">The following code shows the two button handlers.</span></span>

 <span data-ttu-id="f8adf-166">Aşağıdaki kodu `MyControl1` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-166">Add the following code to the `MyControl1` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="f8adf-167">Derlemeye tanımlayıcı bir ad verme ve derlemeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8adf-167">Giving the Assembly a Strong Name and Building the Assembly</span></span>
 <span data-ttu-id="f8adf-168">Bu derlemeye bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulaması tarafından başvurulması için, bir tanımlayıcı adı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-168">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="f8adf-169">Güçlü bir ad oluşturmak için sn. exe ile bir anahtar dosyası oluşturun ve bunu projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-169">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>

1. <span data-ttu-id="f8adf-170">Bir Visual Studio komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-170">Open a Visual Studio command prompt.</span></span> <span data-ttu-id="f8adf-171">Bunu yapmak için **Başlat** menüsüne tıklayın ve ardından **tüm programlar/Microsoft Visual Studio 2010/Visual Studio Araçları/Visual Studio komut istemi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-171">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="f8adf-172">Bu, özelleştirilmiş ortam değişkenleriyle bir konsol penceresi başlatır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-172">This launches a console window with customized environment variables.</span></span>

2. <span data-ttu-id="f8adf-173">Komut isteminde, proje klasörünüze gitmek için `cd` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-173">At the command prompt, use the `cd` command to go to your project folder.</span></span>

3. <span data-ttu-id="f8adf-174">Aşağıdaki komutu çalıştırarak MyControls. snk adlı bir anahtar dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f8adf-174">Generate a key file named MyControls.snk by running the following command.</span></span>

    ```console
    Sn.exe -k MyControls.snk
    ```

4. <span data-ttu-id="f8adf-175">Projenize anahtar dosyasını dahil etmek için Çözüm Gezgini ' de proje adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-175">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="f8adf-176">Proje tasarımcısında **imzalama** sekmesine tıklayın, **derlemeyi imzala** onay kutusunu seçin ve ardından anahtar dosyanıza göz atın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-176">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>

5. <span data-ttu-id="f8adf-177">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f8adf-177">Build the solution.</span></span> <span data-ttu-id="f8adf-178">Derleme MyControls. dll adlı bir DLL üretecektir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-178">The build will produce a DLL named MyControls.dll.</span></span>

## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="f8adf-179">WPF ana bilgisayar uygulamasını uygulama</span><span class="sxs-lookup"><span data-stu-id="f8adf-179">Implementing the WPF Host Application</span></span>
 <span data-ttu-id="f8adf-180">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ana bilgisayar uygulaması `MyControl1`barındırmak için <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-180">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="f8adf-181">Uygulama, denetimdeki verileri almak için `OnButtonClick` olayını işler.</span><span class="sxs-lookup"><span data-stu-id="f8adf-181">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="f8adf-182">Ayrıca, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamadan bazı denetim özelliklerini değiştirmenizi sağlayan bir seçenek düğmeleri koleksiyonuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-182">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="f8adf-183">Aşağıdaki çizimde tamamlanmış uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-183">The following illustration shows the finished application.</span></span>

<span data-ttu-id="f8adf-184">Aşağıdaki görüntüde WPF uygulamasına katıştırılmış denetim dahil olmak üzere tüm uygulama gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f8adf-184">The following image shows the complete application, including the control embedded in the WPF application:</span></span>

 ![WPF sayfasında gömülü bir denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a><span data-ttu-id="f8adf-186">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8adf-186">Creating the Project</span></span>
 <span data-ttu-id="f8adf-187">Projeyi başlatmak için:</span><span class="sxs-lookup"><span data-stu-id="f8adf-187">To start the project:</span></span>

1. <span data-ttu-id="f8adf-188">Visual Studio 'yu açın ve **Yeni proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-188">Open Visual Studio, and select **New Project**.</span></span>

2. <span data-ttu-id="f8adf-189">Pencere kategorisinde, **WPF uygulama** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-189">In the Window category, select the **WPF Application** template.</span></span>

3. <span data-ttu-id="f8adf-190">Yeni proje `WpfHost`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-190">Name the new project `WpfHost`.</span></span>

4. <span data-ttu-id="f8adf-191">Konum için, MyControls projesini içeren en üst düzey klasörü belirtin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-191">For the location, specify the same top-level folder that contains the MyControls project.</span></span>

5. <span data-ttu-id="f8adf-192">Projeyi oluşturmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-192">Click **OK** to create the project.</span></span>

 <span data-ttu-id="f8adf-193">Ayrıca, `MyControl1` ve diğer derlemeleri içeren DLL 'ye başvurular eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-193">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>

1. <span data-ttu-id="f8adf-194">Çözüm Gezgini ' de proje adına sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-194">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>

2. <span data-ttu-id="f8adf-195">**Araştır** sekmesine tıklayın ve MyControls. dll dosyasını içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-195">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="f8adf-196">Bu izlenecek yol için, bu klasör Mycontrols\bin\debugklasörüdür.</span><span class="sxs-lookup"><span data-stu-id="f8adf-196">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>

3. <span data-ttu-id="f8adf-197">MyControls. dll ' yi seçin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-197">Select MyControls.dll, and then click **OK**.</span></span>

4. <span data-ttu-id="f8adf-198">WindowsFormsIntegration. dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-198">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

### <a name="implementing-the-basic-layout"></a><span data-ttu-id="f8adf-199">Temel düzeni uygulama</span><span class="sxs-lookup"><span data-stu-id="f8adf-199">Implementing the Basic Layout</span></span>
 <span data-ttu-id="f8adf-200">Konak uygulamasının [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] MainWindow. xaml ' de uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-200">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="f8adf-201">Bu dosya, düzeni tanımlayan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] biçimlendirme içerir ve Windows Forms denetimini barındırır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-201">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="f8adf-202">Uygulama üç bölgeye ayrılmıştır:</span><span class="sxs-lookup"><span data-stu-id="f8adf-202">The application is divided into three regions:</span></span>

- <span data-ttu-id="f8adf-203">Barındırılan denetimin çeşitli özelliklerini değiştirmek için kullanabileceğiniz seçenek düğmelerinin koleksiyonunu içeren **denetim özellikleri** paneli.</span><span class="sxs-lookup"><span data-stu-id="f8adf-203">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>

- <span data-ttu-id="f8adf-204">Barındırılan denetimden döndürülen verileri görüntüleyen birkaç <xref:System.Windows.Controls.TextBlock> öğesi içeren denetim masası 'ndaki **veriler** .</span><span class="sxs-lookup"><span data-stu-id="f8adf-204">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>

- <span data-ttu-id="f8adf-205">Barındırılan denetimin kendisi.</span><span class="sxs-lookup"><span data-stu-id="f8adf-205">The hosted control itself.</span></span>

 <span data-ttu-id="f8adf-206">Temel düzen aşağıdaki XAML 'de gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-206">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="f8adf-207">`MyControl1` barındırmak için gereken biçimlendirme bu örnekte atlanır, ancak daha sonra ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-207">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>

 <span data-ttu-id="f8adf-208">MainWindow. xaml içindeki XAML 'yi aşağıdakiler ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-208">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="f8adf-209">Visual Basic kullanıyorsanız, sınıfı `x:Class="MainWindow"`olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-209">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 <span data-ttu-id="f8adf-210">İlk <xref:System.Windows.Controls.StackPanel> öğesi, barındırılan denetimin çeşitli varsayılan özelliklerini değiştirmenize olanak sağlayan birkaç <xref:System.Windows.Controls.RadioButton> denetim kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-210">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="f8adf-211">Bundan sonra `MyControl1`barındıran <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.</span><span class="sxs-lookup"><span data-stu-id="f8adf-211">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="f8adf-212">Son <xref:System.Windows.Controls.StackPanel> öğesi barındırılan denetim tarafından döndürülen verileri görüntüleyen birkaç <xref:System.Windows.Controls.TextBlock> öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-212">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="f8adf-213">Öğelerin ve <xref:System.Windows.Controls.DockPanel.Dock%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> öznitelik ayarlarının sıralaması barındırılan denetimi, boşluk veya deformasyon olmadan pencereye katıştırır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-213">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>

#### <a name="hosting-the-control"></a><span data-ttu-id="f8adf-214">Denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="f8adf-214">Hosting the Control</span></span>
 <span data-ttu-id="f8adf-215">Önceki XAML 'nin aşağıdaki düzenlenmiş sürümü `MyControl1`barındırmak için gereken öğelere odaklanır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-215">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 <span data-ttu-id="f8adf-216">`xmlns` ad alanı eşleme özniteliği barındırılan denetimi içeren `MyControls` ad alanına bir başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8adf-216">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="f8adf-217">Bu eşleme, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `MyControl1` `<mcl:MyControl1>`olarak temsil etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8adf-217">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>

 <span data-ttu-id="f8adf-218">XAML 'deki iki öğe barındırmayı işleme:</span><span class="sxs-lookup"><span data-stu-id="f8adf-218">Two elements in the XAML handle the hosting:</span></span>

- <span data-ttu-id="f8adf-219">`WindowsFormsHost`, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasında Windows Forms denetimini barındırmanızı sağlayan <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f8adf-219">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

- <span data-ttu-id="f8adf-220">`MyControl1`temsil eden `mcl:MyControl1`, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin alt koleksiyonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-220">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="f8adf-221">Sonuç olarak, bu Windows Forms denetimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] penceresinin bir parçası olarak işlenir ve uygulamadan denetimle iletişim kurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8adf-221">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>

### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="f8adf-222">Arka plan kod dosyasını uygulama</span><span class="sxs-lookup"><span data-stu-id="f8adf-222">Implementing the Code-Behind File</span></span>
 <span data-ttu-id="f8adf-223">MainWindow. xaml. vb veya MainWindow.xaml.cs arka plan kod dosyası, önceki bölümde açıklanan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] işlevlerini uygulayan yordamsal kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-223">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="f8adf-224">Birincil görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f8adf-224">The primary tasks are:</span></span>

- <span data-ttu-id="f8adf-225">`MyControl1``OnButtonClick` olayına bir olay işleyicisi iliştirme.</span><span class="sxs-lookup"><span data-stu-id="f8adf-225">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>

- <span data-ttu-id="f8adf-226">Seçenek düğmelerinin toplanması temelinde `MyControl1`çeşitli özelliklerini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="f8adf-226">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>

- <span data-ttu-id="f8adf-227">Denetim tarafından toplanan verileri görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="f8adf-227">Displaying the data collected by the control.</span></span>

#### <a name="initializing-the-application"></a><span data-ttu-id="f8adf-228">Uygulamayı başlatma</span><span class="sxs-lookup"><span data-stu-id="f8adf-228">Initializing the Application</span></span>
 <span data-ttu-id="f8adf-229">Başlatma kodu, pencerenin <xref:System.Windows.FrameworkElement.Loaded> olayı için bir olay işleyicisinde bulunur ve denetimin `OnButtonClick` olayına bir olay işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="f8adf-229">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>

 <span data-ttu-id="f8adf-230">MainWindow. xaml. vb veya MainWindow.xaml.cs içinde, `MainWindow` sınıfına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-230">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <span data-ttu-id="f8adf-231">Daha önce açıklanan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin alt öğe koleksiyonuna `MyControl1` eklendiğinden, <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> başvurusunu almak için <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin `MyControl1`dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8adf-231">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="f8adf-232">Daha sonra bu başvuruyu, `OnButtonClick`bir olay işleyicisi iliştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8adf-232">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>

 <span data-ttu-id="f8adf-233"><xref:System.Windows.Forms.Integration.WindowsFormsHost>, denetimin kendine başvuru sağlamaya ek olarak, uygulamanın içinden işleyebileceğiniz bir dizi denetimin özelliklerini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="f8adf-233">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="f8adf-234">Başlatma kodu, bu değerleri uygulamada daha sonra kullanılmak üzere özel genel değişkenlere atar.</span><span class="sxs-lookup"><span data-stu-id="f8adf-234">The initialization code assigns those values to private global variables for later use in the application.</span></span>

 <span data-ttu-id="f8adf-235">`MyControls` DLL 'deki türlere kolayca erişebilmeniz için, dosyanın en üstüne aşağıdaki `Imports` veya `using` ifadesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-235">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="f8adf-236">OnButtonClick olayını işleme</span><span class="sxs-lookup"><span data-stu-id="f8adf-236">Handling the OnButtonClick Event</span></span>
 <span data-ttu-id="f8adf-237">`MyControl1`, Kullanıcı denetimin düğmelerinden birini tıkladığında `OnButtonClick` olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-237">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>

 <span data-ttu-id="f8adf-238">Aşağıdaki kodu `MainWindow` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-238">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 <span data-ttu-id="f8adf-239">Metin kutularındaki veriler `MyControlEventArgs` nesnesine paketlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-239">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="f8adf-240">Kullanıcı **Tamam** düğmesine tıkladığında, olay işleyicisi verileri ayıklar ve aşağıdaki panelde görüntüler `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="f8adf-240">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>

#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="f8adf-241">Denetimin özelliklerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="f8adf-241">Modifying the Control’s Properties</span></span>
 <span data-ttu-id="f8adf-242"><xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, barındırılan denetimin varsayılan özelliklerinden birkaçını ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="f8adf-242">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="f8adf-243">Sonuç olarak, denetimin görünümünü uygulamanızın stiliyle daha yakından eşleşecek şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8adf-243">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="f8adf-244">Sol paneldeki seçenek düğmelerinin kümeleri, kullanıcının çeşitli renk ve yazı tipi özelliklerini değiştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8adf-244">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="f8adf-245">Her düğme kümesi, kullanıcının seçenek düğmesi seçimlerini algılayan ve denetimdeki ilgili özelliği değiştiren <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayı için bir işleyiciye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-245">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>

 <span data-ttu-id="f8adf-246">Aşağıdaki kodu `MainWindow` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8adf-246">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="f8adf-247">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-247">Build and run the application.</span></span> <span data-ttu-id="f8adf-248">Windows Forms Bileşik denetimine bir metin ekleyin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-248">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="f8adf-249">Metin, etiketlerde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f8adf-249">The text appears in the labels.</span></span> <span data-ttu-id="f8adf-250">Denetimdeki etkiyi görmek için farklı radyo düğmelerine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f8adf-250">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8adf-251">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8adf-251">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="f8adf-252">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="f8adf-252">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="f8adf-253">İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="f8adf-253">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="f8adf-254">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="f8adf-254">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
