---
title: 'İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: 2609a54ce8ba2076c35567fe5bc1d9961f6fef3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942054"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="4437e-102">İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="4437e-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="4437e-103">Önbelleğe alma, verileri hızlı erişim için bellekte depolamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4437e-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="4437e-104">Verilere yeniden erişildiğinde, uygulamalar verileri özgün kaynaktan almak yerine önbellekten alabilir.</span><span class="sxs-lookup"><span data-stu-id="4437e-104">When the data is accessed again, applications can get the data from the cache instead of retrieving it from the original source.</span></span> <span data-ttu-id="4437e-105">Bu, performansı ve ölçeklenebilirliği iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="4437e-105">This can improve performance and scalability.</span></span> <span data-ttu-id="4437e-106">Ayrıca, veri kaynağı geçici olarak kullanılamadığında önbelleğe alma verilerin kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4437e-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>

 <span data-ttu-id="4437e-107">.NET Framework, .NET Framework uygulamalarda önbelleğe alma kullanmanıza olanak sağlayan sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="4437e-107">The .NET Framework provides classes that enable you to use caching in .NET Framework applications.</span></span> <span data-ttu-id="4437e-108">Bu sınıflar <xref:System.Runtime.Caching> ad alanında bulunur.</span><span class="sxs-lookup"><span data-stu-id="4437e-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="4437e-109"><xref:System.Runtime.Caching> Ad alanı .NET Framework 4 ' te yenidir.</span><span class="sxs-lookup"><span data-stu-id="4437e-109">The <xref:System.Runtime.Caching> namespace is new in the .NET Framework 4.</span></span> <span data-ttu-id="4437e-110">Bu ad alanı, önbelleğe alma işlemini tüm .NET Framework uygulamaları için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4437e-110">This namespace makes caching is available to all .NET Framework applications.</span></span> <span data-ttu-id="4437e-111">.NET Framework önceki sürümlerinde, önbelleğe alma yalnızca <xref:System.Web> ad alanında kullanılabilir ve bu nedenle ASP.net sınıflarında bir bağımlılık gerektirdi.</span><span class="sxs-lookup"><span data-stu-id="4437e-111">In previous versions of the .NET Framework, caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>

 <span data-ttu-id="4437e-112">Bu izlenecek yol, bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamanın parçası olarak .NET Framework bulunan önbelleğe alma işlevselliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4437e-112">This walkthrough shows you how to use the caching functionality that is available in the .NET Framework as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="4437e-113">İzlenecek yolda, bir metin dosyasının içeriğini önbelleğe alırsınız.</span><span class="sxs-lookup"><span data-stu-id="4437e-113">In the walkthrough, you cache the contents of a text file.</span></span>

 <span data-ttu-id="4437e-114">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="4437e-114">Tasks illustrated in this walkthrough include the following:</span></span>

- <span data-ttu-id="4437e-115">WPF uygulaması projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="4437e-115">Creating a WPF application project.</span></span>

- <span data-ttu-id="4437e-116">.NET Framework 4 ' e başvuru ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="4437e-116">Adding a reference to the .NET Framework 4.</span></span>

- <span data-ttu-id="4437e-117">Önbellek başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="4437e-117">Initializing a cache.</span></span>

- <span data-ttu-id="4437e-118">Bir metin dosyasının içeriğini içeren bir önbellek girişi ekleme.</span><span class="sxs-lookup"><span data-stu-id="4437e-118">Adding a cache entry that contains the contents of a text file.</span></span>

- <span data-ttu-id="4437e-119">Önbellek girdisi için çıkarma ilkesi sağlama.</span><span class="sxs-lookup"><span data-stu-id="4437e-119">Providing an eviction policy for the cache entry.</span></span>

- <span data-ttu-id="4437e-120">Önbelleğe alınan dosyanın yolunu izleme ve izlenen öğedeki değişikliklerle ilgili önbellek örneğine bildirme.</span><span class="sxs-lookup"><span data-stu-id="4437e-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4437e-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4437e-121">Prerequisites</span></span>
 <span data-ttu-id="4437e-122">Bu izlenecek yolu tamamlamak için şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="4437e-122">In order to complete this walkthrough, you will need:</span></span>

- <span data-ttu-id="4437e-123">Microsoft Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="4437e-123">Microsoft Visual Studio 2010.</span></span>

- <span data-ttu-id="4437e-124">Az miktarda metin içeren bir metin dosyası.</span><span class="sxs-lookup"><span data-stu-id="4437e-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="4437e-125">(Metin dosyasının içeriğini bir ileti kutusunda görüntüleyirsiniz.) İzlenecek yolda gösterilen kod, aşağıdaki dosyayla çalıştığınızı varsayar:</span><span class="sxs-lookup"><span data-stu-id="4437e-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>

     `c:\cache\cacheText.txt`

     <span data-ttu-id="4437e-126">Ancak, herhangi bir metin dosyasını kullanabilir ve bu kılavuzda kodda küçük değişiklikler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4437e-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>

## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="4437e-127">WPF uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="4437e-127">Creating a WPF Application Project</span></span>
 <span data-ttu-id="4437e-128">Bir WPF uygulama projesi oluşturarak başlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="4437e-128">You will start by creating a WPF application project.</span></span>

#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="4437e-129">WPF uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4437e-129">To create a WPF application</span></span>

1. <span data-ttu-id="4437e-130">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4437e-130">Start Visual Studio.</span></span>

2. <span data-ttu-id="4437e-131">**Dosya** menüsünde **Yeni**' ye ve ardından **Yeni proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>

     <span data-ttu-id="4437e-132">**Yeni proje** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4437e-132">The **New Project** dialog box is displayed.</span></span>

3. <span data-ttu-id="4437e-133">**Yüklü şablonlar**altında kullanmak istediğiniz programlama dilini (**Visual Basic** veya **görsel C#** ) seçin.</span><span class="sxs-lookup"><span data-stu-id="4437e-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>

4. <span data-ttu-id="4437e-134">**Yeni proje** Iletişim kutusunda **WPF uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="4437e-134">In the **New Project** dialog box, select **WPF Application**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4437e-135">**WPF uygulama** şablonunu GÖRMÜYORSANıZ, WPF 'yi destekleyen .NET Framework bir sürümünü hedeflediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4437e-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the .NET Framework that supports WPF.</span></span> <span data-ttu-id="4437e-136">**Yeni proje** iletişim kutusunda listeden .NET Framework 4 ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="4437e-136">In the **New Project** dialog box, select .NET Framework 4 from the list.</span></span>

5. <span data-ttu-id="4437e-137">**Ad** metin kutusuna projeniz için bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="4437e-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="4437e-138">Örneğin, **WPFCaching**girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4437e-138">For example, you can enter **WPFCaching**.</span></span>

6. <span data-ttu-id="4437e-139">**Çözüm için dizin oluştur** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="4437e-139">Select the **Create directory for solution** check box.</span></span>

7. <span data-ttu-id="4437e-140">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4437e-140">Click **OK**.</span></span>

     <span data-ttu-id="4437e-141">WPF Tasarımcısı **Tasarım** görünümünde açılır ve MainWindow. xaml dosyasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4437e-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> <span data-ttu-id="4437e-142">Visual Studio **My projem** klasörünü, Application. xaml dosyasını ve MainWindow. xaml dosyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4437e-142">Visual Studio creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="4437e-143">.NET Framework hedefleme ve önbelleğe alma derlemelerine başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="4437e-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>
 <span data-ttu-id="4437e-144">Varsayılan olarak, WPF uygulamaları öğesini hedefleyin [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4437e-144">By default, WPF applications target the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span></span> <span data-ttu-id="4437e-145">Bir WPF uygulamasında <xref:System.Runtime.Caching> ad alanını kullanmak için, uygulamanın .NET Framework 4 ' ü ( [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]değil) hedeflemesi ve ad alanına bir başvuru içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4437e-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the .NET Framework 4 (not the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) and must include a reference to the namespace.</span></span>

 <span data-ttu-id="4437e-146">Bu nedenle, sonraki adım .NET Framework hedefini değiştirmek ve <xref:System.Runtime.Caching> ad alanına bir başvuru eklemektir.</span><span class="sxs-lookup"><span data-stu-id="4437e-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="4437e-147">.NET Framework hedefini değiştirme yordamı, bir Visual Basic projesinde ve bir görsel C# projede farklıdır.</span><span class="sxs-lookup"><span data-stu-id="4437e-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="4437e-148">Visual Basic içindeki hedef .NET Framework değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="4437e-148">To change the target .NET Framework in Visual Basic</span></span>

1. <span data-ttu-id="4437e-149">**Çözüm Gezgini**' nde, proje adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>

     <span data-ttu-id="4437e-150">Uygulamanın Özellikler penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4437e-150">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="4437e-151">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-151">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="4437e-152">Pencerenin alt kısmında **Gelişmiş derleme seçenekleri...** öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>

     <span data-ttu-id="4437e-153">**Gelişmiş derleyici ayarları** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4437e-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>

4. <span data-ttu-id="4437e-154">**Hedef Framework (tüm konfigürasyonlar)** listesinde .NET Framework 4 ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="4437e-154">In the **Target framework (all configurations)** list, select .NET Framework 4.</span></span> <span data-ttu-id="4437e-155">(Seçmeyin [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span><span class="sxs-lookup"><span data-stu-id="4437e-155">(Do not select [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span></span>

5. <span data-ttu-id="4437e-156">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4437e-156">Click **OK**.</span></span>

     <span data-ttu-id="4437e-157">**Hedef Framework değişikliği** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4437e-157">The **Target Framework Change** dialog box is displayed.</span></span>

6. <span data-ttu-id="4437e-158">**Hedef çerçeve değişimi** Iletişim kutusunda **Evet**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>

     <span data-ttu-id="4437e-159">Proje kapatılıp yeniden açıldı.</span><span class="sxs-lookup"><span data-stu-id="4437e-159">The project is closed and is then reopened.</span></span>

7. <span data-ttu-id="4437e-160">Aşağıdaki adımları izleyerek önbelleğe alma derlemesine bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4437e-160">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="4437e-161">**Çözüm Gezgini**, projenin adına sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="4437e-162">**.Net** sekmesini seçin, öğesini seçin `System.Runtime.Caching`ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="4437e-163">Görsel C# projedeki hedef .NET Framework değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="4437e-163">To change the target .NET Framework in a Visual C# project</span></span>

1. <span data-ttu-id="4437e-164">**Çözüm Gezgini**, proje adına sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>

     <span data-ttu-id="4437e-165">Uygulamanın Özellikler penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4437e-165">The properties window for the application is displayed.</span></span>

2. <span data-ttu-id="4437e-166">**Uygulama** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-166">Click the **Application** tab.</span></span>

3. <span data-ttu-id="4437e-167">**Hedef çerçeve** listesinde .NET Framework 4 ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="4437e-167">In the **Target framework** list, select .NET Framework 4.</span></span> <span data-ttu-id="4437e-168">( **.NET Framework 4 Istemci profili**seçmeyin.)</span><span class="sxs-lookup"><span data-stu-id="4437e-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>

4. <span data-ttu-id="4437e-169">Aşağıdaki adımları izleyerek önbelleğe alma derlemesine bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4437e-169">Add a reference to the caching assembly by following these steps:</span></span>

    1. <span data-ttu-id="4437e-170">**Başvurular** klasörüne sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-170">Right-click the **References** folder and then click **Add Reference**.</span></span>

    2. <span data-ttu-id="4437e-171">**.Net** sekmesini seçin, öğesini seçin `System.Runtime.Caching`ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>

## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="4437e-172">WPF penceresine düğme ekleme</span><span class="sxs-lookup"><span data-stu-id="4437e-172">Adding a Button to the WPF Window</span></span>
 <span data-ttu-id="4437e-173">Ardından düğme denetimi ekleyeceksiniz ve düğmenin `Click` olayı için bir olay işleyicisi oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="4437e-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="4437e-174">Daha sonra, düğmesine tıkladığınızda metin dosyasının içeriği önbelleğe alınır ve görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4437e-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>

#### <a name="to-add-a-button-control"></a><span data-ttu-id="4437e-175">Düğme denetimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="4437e-175">To add a button control</span></span>

1. <span data-ttu-id="4437e-176">**Çözüm Gezgini**, açmak için MainWindow. xaml dosyasına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>

2. <span data-ttu-id="4437e-177">**Araç kutusundan**, **ortak WPF denetimleri**altında, `Button` `MainWindow` pencereye bir denetim sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="4437e-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>

3. <span data-ttu-id="4437e-178">**Özellikler** penceresinde, **önbellek almak**için `Button` denetimin `Content` özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>

## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="4437e-179">Önbelleği başlatma ve bir girişi önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="4437e-179">Initializing the Cache and Caching an Entry</span></span>
 <span data-ttu-id="4437e-180">Daha sonra, aşağıdaki görevleri gerçekleştirmek için kodu ekleyeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="4437e-180">Next, you will add the code to perform the following tasks:</span></span>

- <span data-ttu-id="4437e-181">Cache sınıfının bir örneğini oluşturun — diğer bir deyişle, yeni <xref:System.Runtime.Caching.MemoryCache> bir nesne örnekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4437e-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>

- <span data-ttu-id="4437e-182">Önbelleğin metin dosyasındaki değişiklikleri izlemek için <xref:System.Runtime.Caching.HostFileChangeMonitor> bir nesne kullandığını belirtin.</span><span class="sxs-lookup"><span data-stu-id="4437e-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>

- <span data-ttu-id="4437e-183">Metin dosyasını okuyun ve içeriğini önbellek girişi olarak önbelleğe alın.</span><span class="sxs-lookup"><span data-stu-id="4437e-183">Read the text file and cache its contents as a cache entry.</span></span>

- <span data-ttu-id="4437e-184">Önbelleğe alınmış metin dosyasının içeriğini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="4437e-184">Display the contents of the cached text file.</span></span>

#### <a name="to-create-the-cache-object"></a><span data-ttu-id="4437e-185">Önbellek nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4437e-185">To create the cache object</span></span>

1. <span data-ttu-id="4437e-186">MainWindow.xaml.cs veya MainWindow. xaml. vb dosyasında bir olay işleyicisi oluşturmak için yeni eklediğiniz düğmeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>

2. <span data-ttu-id="4437e-187">Dosyanın en üstünde (Sınıf bildiriminden önce) aşağıdaki `Imports` (Visual Basic) veya `using` (C#) deyimlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4437e-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. <span data-ttu-id="4437e-188">Olay işleyicisinde, önbellek nesnesinin örneğini oluşturmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4437e-188">In the event handler, add the following code to instantiate the cache object:</span></span>

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <span data-ttu-id="4437e-189"><xref:System.Runtime.Caching.ObjectCache> Sınıfı, bellek içi nesne önbelleği sağlayan yerleşik bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="4437e-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>

4. <span data-ttu-id="4437e-190">Adlı `filecontents`bir önbellek girişinin içeriğini okumak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4437e-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. <span data-ttu-id="4437e-191">Adlı `filecontents` önbellek girişinin varolup olmadığını denetlemek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4437e-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     <span data-ttu-id="4437e-192">Belirtilen önbellek girdisi yoksa, metin dosyasını okuyup önbelleğe bir önbellek girişi olarak eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4437e-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>

6. <span data-ttu-id="4437e-193">Blokta, önbellek girişinin 10 saniye sonra süresinin dolacağını belirten yeni <xref:System.Runtime.Caching.CacheItemPolicy> bir nesne oluşturmak için aşağıdaki kodu ekleyin. `if/then`</span><span class="sxs-lookup"><span data-stu-id="4437e-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     <span data-ttu-id="4437e-194">Çıkarma veya süre sonu bilgileri sağlanmazsa, varsayılan <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>olarak, önbellek girişlerinin yalnızca mutlak bir süre temelinde süresi dolmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4437e-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="4437e-195">Bunun yerine, önbellek girişlerinin süreleri yalnızca bellek baskısı olduğunda sona erer.</span><span class="sxs-lookup"><span data-stu-id="4437e-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="4437e-196">En iyi uygulama olarak her zaman kesin bir şekilde mutlak veya kayan bir süre sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4437e-196">As a best practice, you should always explicitly provide either an absolute or a sliding expiration.</span></span>

7. <span data-ttu-id="4437e-197">`if/then` Bloğunun içinde ve önceki adımda eklediğiniz kodun ardından, izlemek istediğiniz dosya yolları için bir koleksiyon oluşturmak ve metin dosyasının yolunu koleksiyona eklemek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4437e-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    > <span data-ttu-id="4437e-198">Kullanmak istediğiniz metin dosyası yoksa `c:\cache\cacheText.txt`, metin dosyasının kullanmak istediğiniz yolu belirtin.</span><span class="sxs-lookup"><span data-stu-id="4437e-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>

8. <span data-ttu-id="4437e-199">Önceki adımda eklediğiniz kodu izleyerek, önbellek girdisi için değişiklik izleyicileri koleksiyonuna yeni <xref:System.Runtime.Caching.HostFileChangeMonitor> bir nesne eklemek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4437e-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <span data-ttu-id="4437e-200"><xref:System.Runtime.Caching.HostFileChangeMonitor> Nesne, metin dosyasının yolunu izler ve değişiklik oluşursa önbelleğe bildirir.</span><span class="sxs-lookup"><span data-stu-id="4437e-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="4437e-201">Bu örnekte, dosyanın içeriği değişirse önbellek girişinin kullanım süreleri dolacak.</span><span class="sxs-lookup"><span data-stu-id="4437e-201">In this example, the cache entry will expire if the content of the file changes.</span></span>

9. <span data-ttu-id="4437e-202">Önceki adımda eklediğiniz kodu izleyerek, metin dosyasının içeriğini okumak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4437e-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     <span data-ttu-id="4437e-203">Tarih ve saat zaman damgası eklenir, böylece önbellek girişinin süresinin ne zaman dolacağını görebileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="4437e-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>

10. <span data-ttu-id="4437e-204">Önceki adımda eklediğiniz kodu izleyerek, dosyanın içeriğini önbellek nesnesine <xref:System.Runtime.Caching.CacheItem> örnek olarak eklemek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4437e-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     <span data-ttu-id="4437e-205">Daha önce oluşturduğunuz <xref:System.Runtime.Caching.CacheItemPolicy> nesneyi bir parametre olarak geçirerek önbellek girişinin nasıl çıkarılmalıdır?</span><span class="sxs-lookup"><span data-stu-id="4437e-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>

11. <span data-ttu-id="4437e-206">`if/then` Bloğundan sonra, önbelleğe alınmış dosya içeriğini bir ileti kutusunda göstermek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4437e-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. <span data-ttu-id="4437e-207">**Build** menüsünde, projenizi derlemek Için **WPFCaching oluştur** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>

## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="4437e-208">WPF uygulamasında önbelleğe almayı test etme</span><span class="sxs-lookup"><span data-stu-id="4437e-208">Testing Caching in the WPF Application</span></span>
 <span data-ttu-id="4437e-209">Artık uygulamayı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4437e-209">You can now test the application.</span></span>

#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="4437e-210">WPF uygulamasında önbelleğe almayı sınamak için</span><span class="sxs-lookup"><span data-stu-id="4437e-210">To test caching in the WPF application</span></span>

1. <span data-ttu-id="4437e-211">Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="4437e-211">Press CTRL+F5 to run the application.</span></span>

     <span data-ttu-id="4437e-212">`MainWindow` Pencere görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4437e-212">The `MainWindow` window is displayed.</span></span>

2. <span data-ttu-id="4437e-213">**Önbelleği al**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-213">Click **Get Cache**.</span></span>

     <span data-ttu-id="4437e-214">Metin dosyasındaki önbelleğe alınmış içerik bir ileti kutusunda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4437e-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="4437e-215">Dosyadaki zaman damgasına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4437e-215">Notice the timestamp on the file.</span></span>

3. <span data-ttu-id="4437e-216">İleti kutusunu kapatın ve ardından önbelleği yeniden **Al** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4437e-216">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="4437e-217">Zaman damgası değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="4437e-217">The timestamp is unchanged.</span></span> <span data-ttu-id="4437e-218">Bu, önbelleğe alınan içeriğin görüntülendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4437e-218">This indicates the cached content is displayed.</span></span>

4. <span data-ttu-id="4437e-219">10 saniye veya daha fazla bekleyip önbelleği yeniden **Al** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>

     <span data-ttu-id="4437e-220">Bu kez yeni bir zaman damgası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4437e-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="4437e-221">Bu, ilkenin önbellek girişinin sona ereceğini ve önbelleğe alınmış yeni içeriğin görüntülendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4437e-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>

5. <span data-ttu-id="4437e-222">Bir metin düzenleyicisinde, oluşturduğunuz metin dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="4437e-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="4437e-223">Henüz herhangi bir değişiklik yapmayın.</span><span class="sxs-lookup"><span data-stu-id="4437e-223">Do not make any changes yet.</span></span>

6. <span data-ttu-id="4437e-224">İleti kutusunu kapatın ve ardından önbelleği yeniden **Al** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4437e-224">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="4437e-225">Zaman damgasına yeniden dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4437e-225">Notice the timestamp again.</span></span>

7. <span data-ttu-id="4437e-226">Metin dosyasında bir değişiklik yapıp dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="4437e-226">Make a change to the text file and then save the file.</span></span>

8. <span data-ttu-id="4437e-227">İleti kutusunu kapatın ve ardından önbelleği yeniden **Al** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4437e-227">Close the message box and then click **Get Cache** again.</span></span>

     <span data-ttu-id="4437e-228">Bu ileti kutusunda metin dosyasındaki güncelleştirilmiş içerik ve yeni bir zaman damgası bulunur.</span><span class="sxs-lookup"><span data-stu-id="4437e-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="4437e-229">Bu, mutlak zaman aşımı süresi dolmasa bile, ana bilgisayar dosyası değişiklik izleyicisinin, dosyayı değiştirdiğiniz sırada önbellek girdisini hemen kaldırdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4437e-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4437e-230">Dosyada değişiklik yapmanız için daha fazla zaman tanımak üzere çıkarma süresini 20 saniye veya daha fazla artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4437e-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>

## <a name="code-example"></a><span data-ttu-id="4437e-231">Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="4437e-231">Code Example</span></span>
 <span data-ttu-id="4437e-232">Bu yönergeyi tamamladıktan sonra, oluşturduğunuz projenin kodu aşağıdaki örneğe benzer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4437e-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="4437e-233">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4437e-233">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [<span data-ttu-id="4437e-234">.NET Framework Uygulamalarında Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="4437e-234">Caching in .NET Framework Applications</span></span>](../../performance/caching-in-net-framework-applications.md)
