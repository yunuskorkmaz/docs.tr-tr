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
ms.openlocfilehash: e4c1de17b131ee68c6e6fce0035b703eb5b489a0
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991880"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="82a4d-102">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="82a4d-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="82a4d-103">uygulamalar oluşturmak için zengin bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="82a4d-103">provides a rich environment for creating applications.</span></span> <span data-ttu-id="82a4d-104">Ancak, kod içinde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] önemli bir yatırımınız olduğunda, sıfırdan yazmak yerine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamanızda bu kodun en az bir kısmını yeniden kullanmak daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="82a4d-105">En yaygın senaryo, Windows Forms denetimlerinizi var.</span><span class="sxs-lookup"><span data-stu-id="82a4d-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="82a4d-106">Bazı durumlarda, bu denetimlerin kaynak koduna bile erişiminiz olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="82a4d-107">bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamada bu denetimleri barındırmak için kolay bir yordam sağlar.</span><span class="sxs-lookup"><span data-stu-id="82a4d-107">provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="82a4d-108">Örneğin, özelleştirilmiş <xref:System.Windows.Forms.DataGridView> denetimlerinizi barındırırken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birçok programlama için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82a4d-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="82a4d-109">Bu izlenecek yol, bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamada veri girişi gerçekleştirmek üzere Windows Forms Bileşik denetim barındıran bir uygulamada size kılavuzluk ediyor.</span><span class="sxs-lookup"><span data-stu-id="82a4d-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="82a4d-110">Bileşik denetim bir DLL içinde paketlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="82a4d-111">Bu genel yordam, daha karmaşık uygulamalar ve denetimler için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="82a4d-112">Bu izlenecek yol, görünümü ve işlevselliği [gözden geçirmede neredeyse özdeş olacak şekilde tasarlanmıştır: Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)Içinde WPF bileşik denetimi barındırma.</span><span class="sxs-lookup"><span data-stu-id="82a4d-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="82a4d-113">Birincil fark, barındırma senaryosunun tersine çevrilme olur.</span><span class="sxs-lookup"><span data-stu-id="82a4d-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="82a4d-114">İzlenecek yol iki bölüme ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="82a4d-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="82a4d-115">İlk bölüm Windows Forms Bileşik denetimin uygulamasını kısaca açıklar.</span><span class="sxs-lookup"><span data-stu-id="82a4d-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="82a4d-116">İkinci bölümde, bileşik denetimin bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamada nasıl barındırılabileceği, denetimden olayların nasıl alınacağı ve denetimin özelliklerinden bazılarına erişme hakkında ayrıntılı bilgi yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="82a4d-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="82a4d-117">Bu izlenecek yolda gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="82a4d-117">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="82a4d-118">Windows Forms Bileşik denetimi uygulama.</span><span class="sxs-lookup"><span data-stu-id="82a4d-118">Implementing the Windows Forms composite control.</span></span>  
  
- <span data-ttu-id="82a4d-119">WPF konak uygulamasını uygulama.</span><span class="sxs-lookup"><span data-stu-id="82a4d-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="82a4d-120">Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [WPF örneğinde Windows Forms Bileşik denetimi barındırma](https://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="82a4d-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="82a4d-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="82a4d-121">Prerequisites</span></span>  

<span data-ttu-id="82a4d-122">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="82a4d-123">Windows Forms Bileşik denetimi uygulama</span><span class="sxs-lookup"><span data-stu-id="82a4d-123">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="82a4d-124">Bu örnekte kullanılan Windows Forms Bileşik denetim basit bir veri girişi biçimidir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-124">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="82a4d-125">Bu form kullanıcının adını ve adresini alır ve bu bilgileri konağa döndürmek için özel bir olay kullanır.</span><span class="sxs-lookup"><span data-stu-id="82a4d-125">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="82a4d-126">Aşağıdaki çizimde işlenmiş denetim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-126">The following illustration shows the rendered control.</span></span>  

 <span data-ttu-id="82a4d-127">Aşağıdaki görüntüde Windows Forms Bileşik bir denetim gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="82a4d-127">The following image shows a Windows Forms composite control:</span></span>  

 ![Basit bir Windows Forms denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a><span data-ttu-id="82a4d-129">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="82a4d-129">Creating the Project</span></span>  
 <span data-ttu-id="82a4d-130">Projeyi başlatmak için:</span><span class="sxs-lookup"><span data-stu-id="82a4d-130">To start the project:</span></span>  
  
1. <span data-ttu-id="82a4d-131">Başlatın [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]ve **Yeni proje** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-131">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="82a4d-132">Pencere kategorisinde **Windows Forms denetim kitaplığı** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-132">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3. <span data-ttu-id="82a4d-133">Yeni projeyi `MyControls`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-133">Name the new project `MyControls`.</span></span>  
  
4. <span data-ttu-id="82a4d-134">Konum için, gibi kolay adlandırılmış bir üst düzey klasör `WpfHostingWindowsFormsControl`belirtin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-134">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="82a4d-135">Daha sonra, ana bilgisayar uygulamasını bu klasöre yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82a4d-135">Later, you will put the host application in this folder.</span></span>  
  
5. <span data-ttu-id="82a4d-136">Projeyi oluşturmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-136">Click **OK** to create the project.</span></span> <span data-ttu-id="82a4d-137">Varsayılan proje adlı `UserControl1`tek bir denetim içerir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-137">The default project contains a single control named `UserControl1`.</span></span>  
  
6. <span data-ttu-id="82a4d-138">Çözüm Gezgini ' de, `UserControl1` olarak `MyControl1`yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-138">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="82a4d-139">Projenizin aşağıdaki sistem dll 'Lerine başvuruları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82a4d-139">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="82a4d-140">Bu dll 'Lerden herhangi biri varsayılan olarak dahil edilmez, bunları projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-140">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
- <span data-ttu-id="82a4d-141">Sistem</span><span class="sxs-lookup"><span data-stu-id="82a4d-141">System</span></span>  
  
- <span data-ttu-id="82a4d-142">System.Data</span><span class="sxs-lookup"><span data-stu-id="82a4d-142">System.Data</span></span>  
  
- <span data-ttu-id="82a4d-143">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="82a4d-143">System.Drawing</span></span>  
  
- <span data-ttu-id="82a4d-144">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="82a4d-144">System.Windows.Forms</span></span>  
  
- <span data-ttu-id="82a4d-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="82a4d-145">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="82a4d-146">Forma denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="82a4d-146">Adding Controls to the Form</span></span>  
 <span data-ttu-id="82a4d-147">Forma denetim eklemek için:</span><span class="sxs-lookup"><span data-stu-id="82a4d-147">To add controls to the form:</span></span>  
  
- <span data-ttu-id="82a4d-148">Tasarımcıda `MyControl1` açın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-148">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="82a4d-149">Formda, <xref:System.Windows.Forms.Label> önceki çizimde oldukları gibi <xref:System.Windows.Forms.TextBox> boyutlandırılmış ve düzenlenmiş beş denetim ve bunlara karşılık gelen denetimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-149">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="82a4d-150">Örnekte, <xref:System.Windows.Forms.TextBox> denetimler şu şekilde adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="82a4d-150">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 <span data-ttu-id="82a4d-151">Tamam ve <xref:System.Windows.Forms.Button> **iptal**etiketli iki denetim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-151">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="82a4d-152">Örnekte, düğme adları sırasıyla ve `btnOK` `btnCancel`' dir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-152">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="82a4d-153">Destekleyici kodu uygulama</span><span class="sxs-lookup"><span data-stu-id="82a4d-153">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="82a4d-154">Formu kod görünümünde açın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-154">Open the form in code view.</span></span> <span data-ttu-id="82a4d-155">Denetim, toplanan verileri özel `OnButtonClick` olayı yükselterek ana bilgisayarına döndürür.</span><span class="sxs-lookup"><span data-stu-id="82a4d-155">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="82a4d-156">Veriler, olay bağımsız değişkeni nesnesinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="82a4d-156">The data is contained in the event argument object.</span></span> <span data-ttu-id="82a4d-157">Aşağıdaki kod, olay ve temsilci bildirimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-157">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="82a4d-158">`MyControl1` Sınıfına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-158">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 <span data-ttu-id="82a4d-159">`MyControlEventArgs` Sınıfı, konağa döndürülecek bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-159">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>

 <span data-ttu-id="82a4d-160">Aşağıdaki sınıfı forma ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-160">Add the following class to the form.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 <span data-ttu-id="82a4d-161">Kullanıcı **Tamam** veya **iptal** <xref:System.Windows.Forms.Control.Click> düğmesine tıkladığında, olay işleyicileri verileri içeren bir `MyControlEventArgs` nesne oluşturur ve `OnButtonClick` olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="82a4d-161">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="82a4d-162">İki işleyici arasındaki tek fark, olay bağımsız değişkeninin `IsOK` özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-162">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="82a4d-163">Bu özellik, ana bilgisayarın hangi düğmeye tıklandığını belirlemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="82a4d-163">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="82a4d-164">`true` **Tamam** düğmesi ve`false` **iptal** düğmesi için olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="82a4d-164">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="82a4d-165">Aşağıdaki kod iki düğme işleyicisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-165">The following code shows the two button handlers.</span></span>

 <span data-ttu-id="82a4d-166">`MyControl1` Sınıfına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-166">Add the following code to the `MyControl1` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="82a4d-167">Derlemeye tanımlayıcı bir ad verme ve derlemeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="82a4d-167">Giving the Assembly a Strong Name and Building the Assembly</span></span>
 <span data-ttu-id="82a4d-168">Bu derlemeye bir uygulama tarafından başvurulması için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir tanımlayıcı adı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-168">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="82a4d-169">Güçlü bir ad oluşturmak için sn. exe ile bir anahtar dosyası oluşturun ve bunu projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-169">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>

1. <span data-ttu-id="82a4d-170">Bir [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-170">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="82a4d-171">Bunu yapmak için **Başlat** menüsüne tıklayın ve ardından **tüm programlar/Microsoft Visual Studio 2010/Visual Studio Araçları/Visual Studio komut istemi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-171">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="82a4d-172">Bu, özelleştirilmiş ortam değişkenleriyle bir konsol penceresi başlatır.</span><span class="sxs-lookup"><span data-stu-id="82a4d-172">This launches a console window with customized environment variables.</span></span>

2. <span data-ttu-id="82a4d-173">Komut isteminde, proje klasörünüze gitmek için `cd` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-173">At the command prompt, use the `cd` command to go to your project folder.</span></span>

3. <span data-ttu-id="82a4d-174">Aşağıdaki komutu çalıştırarak MyControls. snk adlı bir anahtar dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="82a4d-174">Generate a key file named MyControls.snk by running the following command.</span></span>

    ```console
    Sn.exe -k MyControls.snk
    ```

4. <span data-ttu-id="82a4d-175">Projenize anahtar dosyasını dahil etmek için Çözüm Gezgini ' de proje adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-175">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="82a4d-176">Proje tasarımcısında **imzalama** sekmesine tıklayın, **derlemeyi imzala** onay kutusunu seçin ve ardından anahtar dosyanıza göz atın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-176">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>

5. <span data-ttu-id="82a4d-177">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="82a4d-177">Build the solution.</span></span> <span data-ttu-id="82a4d-178">Derleme MyControls. dll adlı bir DLL üretecektir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-178">The build will produce a DLL named MyControls.dll.</span></span>

## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="82a4d-179">WPF ana bilgisayar uygulamasını uygulama</span><span class="sxs-lookup"><span data-stu-id="82a4d-179">Implementing the WPF Host Application</span></span>
 <span data-ttu-id="82a4d-180">Konak uygulama, barındırmak <xref:System.Windows.Forms.Integration.WindowsFormsHost> `MyControl1`için denetimi kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82a4d-180">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="82a4d-181">Uygulama, denetimden verileri `OnButtonClick` almak için olayı işler.</span><span class="sxs-lookup"><span data-stu-id="82a4d-181">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="82a4d-182">Ayrıca, bazı denetim özelliklerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamadan değiştirmenize olanak sağlayan bir seçenek düğmeleri koleksiyonuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-182">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="82a4d-183">Aşağıdaki çizimde tamamlanmış uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-183">The following illustration shows the finished application.</span></span>

<span data-ttu-id="82a4d-184">Aşağıdaki görüntüde WPF uygulamasına katıştırılmış denetim dahil olmak üzere tüm uygulama gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="82a4d-184">The following image shows the complete application, including the control embedded in the WPF application:</span></span>

 ![WPF sayfasında gömülü bir denetimi gösteren ekran görüntüsü.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a><span data-ttu-id="82a4d-186">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="82a4d-186">Creating the Project</span></span>
 <span data-ttu-id="82a4d-187">Projeyi başlatmak için:</span><span class="sxs-lookup"><span data-stu-id="82a4d-187">To start the project:</span></span>

1. <span data-ttu-id="82a4d-188">Açın [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]ve **Yeni proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-188">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>

2. <span data-ttu-id="82a4d-189">Pencere kategorisinde, **WPF uygulama** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-189">In the Window category, select the **WPF Application** template.</span></span>

3. <span data-ttu-id="82a4d-190">Yeni projeyi `WpfHost`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-190">Name the new project `WpfHost`.</span></span>

4. <span data-ttu-id="82a4d-191">Konum için, MyControls projesini içeren en üst düzey klasörü belirtin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-191">For the location, specify the same top-level folder that contains the MyControls project.</span></span>

5. <span data-ttu-id="82a4d-192">Projeyi oluşturmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-192">Click **OK** to create the project.</span></span>

 <span data-ttu-id="82a4d-193">Ayrıca, ve diğer derlemeler içeren `MyControl1` dll 'ye başvurular eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-193">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>

1. <span data-ttu-id="82a4d-194">Çözüm Gezgini ' de proje adına sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-194">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>

2. <span data-ttu-id="82a4d-195">**Araştır** sekmesine tıklayın ve MyControls. dll dosyasını içeren klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-195">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="82a4d-196">Bu izlenecek yol için, bu klasör Mycontrols\bin\debugklasörüdür.</span><span class="sxs-lookup"><span data-stu-id="82a4d-196">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>

3. <span data-ttu-id="82a4d-197">MyControls. dll ' yi seçin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-197">Select MyControls.dll, and then click **OK**.</span></span>

4. <span data-ttu-id="82a4d-198">WindowsFormsIntegration. dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-198">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

### <a name="implementing-the-basic-layout"></a><span data-ttu-id="82a4d-199">Temel düzeni uygulama</span><span class="sxs-lookup"><span data-stu-id="82a4d-199">Implementing the Basic Layout</span></span>
 <span data-ttu-id="82a4d-200">Konak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] uygulamanın, MainWindow. xaml ' de uygulanması.</span><span class="sxs-lookup"><span data-stu-id="82a4d-200">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="82a4d-201">Bu dosya, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] düzeni tanımlayan biçimlendirmeyi içerir ve Windows Forms denetimi barındırır.</span><span class="sxs-lookup"><span data-stu-id="82a4d-201">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="82a4d-202">Uygulama üç bölgeye ayrılmıştır:</span><span class="sxs-lookup"><span data-stu-id="82a4d-202">The application is divided into three regions:</span></span>

- <span data-ttu-id="82a4d-203">Barındırılan denetimin çeşitli özelliklerini değiştirmek için kullanabileceğiniz seçenek düğmelerinin koleksiyonunu içeren **denetim özellikleri** paneli.</span><span class="sxs-lookup"><span data-stu-id="82a4d-203">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>

- <span data-ttu-id="82a4d-204">Barındırılan denetimden döndürülen verileri görüntüleyen çeşitli <xref:System.Windows.Controls.TextBlock> öğeleri içeren denetim masası 'ndaki veriler.</span><span class="sxs-lookup"><span data-stu-id="82a4d-204">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>

- <span data-ttu-id="82a4d-205">Barındırılan denetimin kendisi.</span><span class="sxs-lookup"><span data-stu-id="82a4d-205">The hosted control itself.</span></span>

 <span data-ttu-id="82a4d-206">Temel düzen aşağıdaki XAML 'de gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-206">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="82a4d-207">Barındırmak `MyControl1` için gereken biçimlendirme bu örnekte atlanır, ancak daha sonra ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="82a4d-207">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>

 <span data-ttu-id="82a4d-208">MainWindow. xaml içindeki XAML 'yi aşağıdakiler ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-208">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="82a4d-209">Visual Basic kullanıyorsanız, sınıfını olarak `x:Class="MainWindow"`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-209">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 <span data-ttu-id="82a4d-210">İlk <xref:System.Windows.Controls.StackPanel> öğe, barındırılan denetimin çeşitli varsayılan <xref:System.Windows.Controls.RadioButton> özelliklerini değiştirmenize olanak tanıyan birkaç denetim kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-210">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="82a4d-211">Bu, ardından barındıran <xref:System.Windows.Forms.Integration.WindowsFormsHost> `MyControl1`bir öğesi.</span><span class="sxs-lookup"><span data-stu-id="82a4d-211">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="82a4d-212">Son <xref:System.Windows.Controls.StackPanel> öğesi, barındırılan denetim <xref:System.Windows.Controls.TextBlock> tarafından döndürülen verileri görüntüleyen çeşitli öğeler içerir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-212">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="82a4d-213">Öğelerin ve <xref:System.Windows.Controls.DockPanel.Dock%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> öznitelik ayarlarının sıralaması barındırılan denetimi, boşluk veya deformasyon olmadan pencereye katıştırır.</span><span class="sxs-lookup"><span data-stu-id="82a4d-213">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>

#### <a name="hosting-the-control"></a><span data-ttu-id="82a4d-214">Denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="82a4d-214">Hosting the Control</span></span>
 <span data-ttu-id="82a4d-215">Önceki XAML 'nin aşağıdaki düzenlenmiş sürümü barındırmak `MyControl1`için gereken öğelere odaklanır.</span><span class="sxs-lookup"><span data-stu-id="82a4d-215">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 <span data-ttu-id="82a4d-216">Ad alanı eşleme özniteliği barındırılan denetimi içeren `MyControls` ad alanına bir başvuru oluşturur. `xmlns`</span><span class="sxs-lookup"><span data-stu-id="82a4d-216">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="82a4d-217">Bu eşleme, içinde `MyControl1` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak `<mcl:MyControl1>`temsil etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="82a4d-217">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>

 <span data-ttu-id="82a4d-218">XAML 'deki iki öğe barındırmayı işleme:</span><span class="sxs-lookup"><span data-stu-id="82a4d-218">Two elements in the XAML handle the hosting:</span></span>

- <span data-ttu-id="82a4d-219">`WindowsFormsHost`<xref:System.Windows.Forms.Integration.WindowsFormsHost> bir[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamada Windows Forms denetimini barındırmanızı sağlayan öğeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="82a4d-219">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

- <span data-ttu-id="82a4d-220">`mcl:MyControl1`öğesini temsil `MyControl1`eden <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi öğenin alt koleksiyonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-220">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="82a4d-221">Sonuç olarak, bu Windows Forms denetimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pencerenin bir parçası olarak işlenir ve uygulamadan denetimle iletişim kurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82a4d-221">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>

### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="82a4d-222">Arka plan kod dosyasını uygulama</span><span class="sxs-lookup"><span data-stu-id="82a4d-222">Implementing the Code-Behind File</span></span>
 <span data-ttu-id="82a4d-223">MainWindow. xaml. vb veya MainWindow.xaml.cs arka plan kod dosyası, önceki bölümde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] açıklanan işlevleri uygulayan yordamsal kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-223">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="82a4d-224">Birincil görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="82a4d-224">The primary tasks are:</span></span>

- <span data-ttu-id="82a4d-225">Olayına bir olay işleyicisi `MyControl1` `OnButtonClick` iliştirme.</span><span class="sxs-lookup"><span data-stu-id="82a4d-225">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>

- <span data-ttu-id="82a4d-226">Seçenek düğmelerinin toplanması temelinde `MyControl1`' nin çeşitli özelliklerini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="82a4d-226">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>

- <span data-ttu-id="82a4d-227">Denetim tarafından toplanan verileri görüntüleme.</span><span class="sxs-lookup"><span data-stu-id="82a4d-227">Displaying the data collected by the control.</span></span>

#### <a name="initializing-the-application"></a><span data-ttu-id="82a4d-228">Uygulamayı başlatma</span><span class="sxs-lookup"><span data-stu-id="82a4d-228">Initializing the Application</span></span>
 <span data-ttu-id="82a4d-229">Başlatma kodu, pencerenin <xref:System.Windows.FrameworkElement.Loaded> olayı için bir olay işleyicisinde bulunur ve `OnButtonClick` denetimin olayına bir olay işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="82a4d-229">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>

 <span data-ttu-id="82a4d-230">MainWindow. xaml. vb veya MainWindow.xaml.cs içinde, `MainWindow` sınıfına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-230">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <span data-ttu-id="82a4d-231"><xref:System.Windows.Forms.Integration.WindowsFormsHost> `MyControl1` Dahaönce<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> , `MyControl1` öğenin<xref:System.Windows.Forms.Integration.WindowsFormsHost> alt öğe koleksiyonuna eklenmiş olduğundan, başvurusunu almak için öğesini çevirebilirsiniz. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82a4d-231">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="82a4d-232">Daha sonra bu başvuruyu, ' a bir olay işleyicisi `OnButtonClick`iliştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82a4d-232">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>

 <span data-ttu-id="82a4d-233">Denetimin kendine başvuru sağlamaya ek olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> uygulamanın içinden işleyebileceğiniz bir dizi denetimin özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-233">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="82a4d-234">Başlatma kodu, bu değerleri uygulamada daha sonra kullanılmak üzere özel genel değişkenlere atar.</span><span class="sxs-lookup"><span data-stu-id="82a4d-234">The initialization code assigns those values to private global variables for later use in the application.</span></span>

 <span data-ttu-id="82a4d-235">`MyControls` Dll 'deki türlere kolayca erişebilmeniz için, dosyanın en üstüne aşağıdaki `Imports` veya `using` ifadesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-235">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="82a4d-236">OnButtonClick olayını işleme</span><span class="sxs-lookup"><span data-stu-id="82a4d-236">Handling the OnButtonClick Event</span></span>
 <span data-ttu-id="82a4d-237">`MyControl1`Kullanıcı, denetim düğmelerinden birini tıkladığında olayıbaşlatır.`OnButtonClick`</span><span class="sxs-lookup"><span data-stu-id="82a4d-237">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>

 <span data-ttu-id="82a4d-238">`MainWindow` Sınıfına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-238">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 <span data-ttu-id="82a4d-239">Metin kutularındaki veriler `MyControlEventArgs` nesnesine paketlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-239">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="82a4d-240">Kullanıcı **Tamam** düğmesine tıkladığında, olay işleyicisi verileri ayıklar ve aşağıdaki `MyControl1`panelde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="82a4d-240">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>

#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="82a4d-241">Denetimin özelliklerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="82a4d-241">Modifying the Control’s Properties</span></span>
 <span data-ttu-id="82a4d-242"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi, barındırılan denetimin varsayılan özelliklerinden birkaçını gösterir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-242">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="82a4d-243">Sonuç olarak, denetimin görünümünü uygulamanızın stiliyle daha yakından eşleşecek şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82a4d-243">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="82a4d-244">Sol paneldeki seçenek düğmelerinin kümeleri, kullanıcının çeşitli renk ve yazı tipi özelliklerini değiştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="82a4d-244">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="82a4d-245">Her düğme kümesi, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay için kullanıcının seçenek düğmesi seçimlerini algılayan ve denetimdeki ilgili özelliği değiştiren bir işleyicisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-245">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>

 <span data-ttu-id="82a4d-246">`MainWindow` Sınıfına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="82a4d-246">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="82a4d-247">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-247">Build and run the application.</span></span> <span data-ttu-id="82a4d-248">Windows Forms Bileşik denetimine bir metin ekleyin ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-248">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="82a4d-249">Metin, etiketlerde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="82a4d-249">The text appears in the labels.</span></span> <span data-ttu-id="82a4d-250">Denetimdeki etkiyi görmek için farklı radyo düğmelerine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="82a4d-250">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82a4d-251">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82a4d-251">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="82a4d-252">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="82a4d-252">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="82a4d-253">İzlenecek yol: WPF 'de Windows Forms denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="82a4d-253">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="82a4d-254">İzlenecek yol: Windows Forms WPF bileşik denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="82a4d-254">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
