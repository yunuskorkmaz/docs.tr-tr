---
title: "İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81d808b982852d5cc6dc187a3c8389748a0dc0bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="f98f3-102">İzlenecek yol: WPF Uygulamasında Uygulama Verilerini Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="f98f3-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="f98f3-103">Önbelleğe alma, verileri hızlı erişim için bellekte depolamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f98f3-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="f98f3-104">Verileri yeniden erişildiğinde uygulamalar yerine özgün kaynak alma önbellekten veri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f98f3-104">When the data is accessed again, applications can get the data from the cache instead retrieving it from the original source.</span></span> <span data-ttu-id="f98f3-105">Bu, performans ve ölçeklenebilirlik iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-105">This can improve performance and scalability.</span></span> <span data-ttu-id="f98f3-106">Ayrıca, veri kaynağı geçici olarak devre dışı olduğunda kullanılabilir hale getirir verileri önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="f98f3-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>  
  
 <span data-ttu-id="f98f3-107">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Önbelleğe almayı kullanmanıza olanak sağlayan sınıflar sağlar [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="f98f3-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides classes that enable you to use caching in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications.</span></span> <span data-ttu-id="f98f3-108">Bu sınıfların bulunan <xref:System.Runtime.Caching> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f98f3-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f98f3-109"><xref:System.Runtime.Caching> Ad yeni [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f98f3-109">The <xref:System.Runtime.Caching> namespace is new in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="f98f3-110">Bu ad alanı yapar önbelleğe alma kullanılabilir tüm [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="f98f3-110">This namespace makes caching is available to all [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications.</span></span> <span data-ttu-id="f98f3-111">Önceki sürümlerinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], önbelleğe alma yalnızca kullanılabilir <xref:System.Web> ad alanı ve bu nedenle, bir bağımlılığı ASP.NET sınıfları gerekir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-111">In previous versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>  
  
 <span data-ttu-id="f98f3-112">Bu kılavuz, kullanılabilir önbellek işlevselliğinin nasıl kullanılacağını gösterir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] parçası olarak bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="f98f3-112">This walkthrough shows you how to use the caching functionality that is available in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="f98f3-113">Bu kılavuzda, bir metin dosyasının içeriğini önbelleğe.</span><span class="sxs-lookup"><span data-stu-id="f98f3-113">In the walkthrough, you cache the contents of a text file.</span></span>  
  
 <span data-ttu-id="f98f3-114">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="f98f3-114">Tasks illustrated in this walkthrough include the following:</span></span>  
  
-   <span data-ttu-id="f98f3-115">Bir WPF uygulaması projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="f98f3-115">Creating a WPF application project.</span></span>  
  
-   <span data-ttu-id="f98f3-116">Bir başvuru ekleyerek [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f98f3-116">Adding a reference to the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
-   <span data-ttu-id="f98f3-117">Bir önbellek başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="f98f3-117">Initializing a cache.</span></span>  
  
-   <span data-ttu-id="f98f3-118">Bir metin dosyasının içeriğini içeren bir önbellek girişi ekleme.</span><span class="sxs-lookup"><span data-stu-id="f98f3-118">Adding a cache entry that contains the contents of a text file.</span></span>  
  
-   <span data-ttu-id="f98f3-119">Bir çıkarma ilkesi için önbellek girişi sağlama.</span><span class="sxs-lookup"><span data-stu-id="f98f3-119">Providing an eviction policy for the cache entry.</span></span>  
  
-   <span data-ttu-id="f98f3-120">Önbelleğe alınmış dosya yolunu izleme ve önbellek örneği hakkında bilgilendirmek için izlenen öğe değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f98f3-121">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f98f3-121">Prerequisites</span></span>  
 <span data-ttu-id="f98f3-122">Bu kılavuzu tamamlamak için gerekir:</span><span class="sxs-lookup"><span data-stu-id="f98f3-122">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="f98f3-123">Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f98f3-123">Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].</span></span>  
  
-   <span data-ttu-id="f98f3-124">Küçük miktarda metin içeren bir metin dosyası.</span><span class="sxs-lookup"><span data-stu-id="f98f3-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="f98f3-125">(Metin dosyasının içeriğini bir ileti kutusu görüntülenir.) Örneklerde gösterilen kodu aşağıdaki dosyasıyla çalıştığınız varsayılır:</span><span class="sxs-lookup"><span data-stu-id="f98f3-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>  
  
     `c:\cache\cacheText.txt`  
  
     <span data-ttu-id="f98f3-126">Ancak, herhangi bir metin dosyasını kullanın ve bu kılavuzda kod küçük değişiklikler yapmak.</span><span class="sxs-lookup"><span data-stu-id="f98f3-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>  
  
## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="f98f3-127">Bir WPF uygulaması projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="f98f3-127">Creating a WPF Application Project</span></span>  
 <span data-ttu-id="f98f3-128">Bir WPF uygulaması projesi oluşturarak başlar.</span><span class="sxs-lookup"><span data-stu-id="f98f3-128">You will start by creating a WPF application project.</span></span>  
  
#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="f98f3-129">Bir WPF uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f98f3-129">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="f98f3-130">Başlat [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f98f3-130">Start [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
2.  <span data-ttu-id="f98f3-131">İçinde **dosya** menüsünde tıklatın **yeni**ve ardından **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="f98f3-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>  
  
     <span data-ttu-id="f98f3-132">**Yeni proje** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-132">The **New Project** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="f98f3-133">Altında **yüklü şablonlar**, kullanmak istediğiniz programlama dili seçin (**Visual Basic** veya **Visual C#**).</span><span class="sxs-lookup"><span data-stu-id="f98f3-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>  
  
4.  <span data-ttu-id="f98f3-134">İçinde **yeni proje** iletişim kutusunda **WPF uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="f98f3-134">In the **New Project** dialog box, select **WPF Application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f98f3-135">Görmüyorsanız, **WPF uygulaması** şablonu, bir sürümünü hedefleme emin olun [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] WPF destekler.</span><span class="sxs-lookup"><span data-stu-id="f98f3-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] that supports WPF.</span></span> <span data-ttu-id="f98f3-136">İçinde **yeni proje** iletişim kutusunda [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] listeden.</span><span class="sxs-lookup"><span data-stu-id="f98f3-136">In the **New Project** dialog box, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] from the list.</span></span>  
  
5.  <span data-ttu-id="f98f3-137">İçinde **adı** metin kutusuna, projeniz için bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="f98f3-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="f98f3-138">Örneğin, girebilirsiniz **WPFCaching**.</span><span class="sxs-lookup"><span data-stu-id="f98f3-138">For example, you can enter **WPFCaching**.</span></span>  
  
6.  <span data-ttu-id="f98f3-139">Seçin **çözüm için dizin oluştur** onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="f98f3-139">Select the **Create directory for solution** check box.</span></span>  
  
7.  <span data-ttu-id="f98f3-140">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f98f3-140">Click **OK**.</span></span>  
  
     <span data-ttu-id="f98f3-141">WPF Tasarımcısı açılır **tasarım** görüntülemek ve MainWindow.xaml dosyayı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f98f3-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]<span data-ttu-id="f98f3-142">oluşturur **My proje** klasörü, Application.xaml dosyası ve MainWindow.xaml dosyası.</span><span class="sxs-lookup"><span data-stu-id="f98f3-142"> creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>  
  
## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="f98f3-143">.NET Framework hedefleme ve önbelleğe alma derlemelerine başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="f98f3-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>  
 <span data-ttu-id="f98f3-144">Varsayılan olarak, WPF uygulamalar hedef [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f98f3-144">By default, WPF applications target the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span></span> <span data-ttu-id="f98f3-145">Kullanılacak <xref:System.Runtime.Caching> gerekir uygulama ad alanı bir WPF uygulamasında hedef [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (değil [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) ve ad alanı için bir başvuru içermelidir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (not the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) and must include a reference to the namespace.</span></span>  
  
 <span data-ttu-id="f98f3-146">Bu nedenle, bir başvuru ekleyin ve .NET Framework hedef değiştirmek için sonraki adım olan <xref:System.Runtime.Caching> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f98f3-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f98f3-147">.NET Framework hedef değiştirme yordamı, Visual Basic projesinde ve Visual C# projesinde farklıdır.</span><span class="sxs-lookup"><span data-stu-id="f98f3-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>  
  
#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="f98f3-148">Visual Basic'te .NET Framework hedef değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="f98f3-148">To change the target .NET Framework in Visual Basic</span></span>  
  
1.  <span data-ttu-id="f98f3-149">İçinde **Çözüm Gezgini**, proje adına sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="f98f3-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="f98f3-150">Uygulama için Özellikler penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-150">The properties window for the application is displayed.</span></span>  
  
2.  <span data-ttu-id="f98f3-151">Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="f98f3-151">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="f98f3-152">Pencerenin alt kısmındaki tıklatın **Gelişmiş derleme seçenekleri...** .</span><span class="sxs-lookup"><span data-stu-id="f98f3-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>  
  
     <span data-ttu-id="f98f3-153">**Gelişmiş derleyici ayarları** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="f98f3-154">İçinde **hedef Framework'ü (tüm yapılandırmaları)** listesinde [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f98f3-154">In the **Target framework (all configurations)** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="f98f3-155">(Seçmeyin [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span><span class="sxs-lookup"><span data-stu-id="f98f3-155">(Do not select [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span></span>  
  
5.  <span data-ttu-id="f98f3-156">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f98f3-156">Click **OK**.</span></span>  
  
     <span data-ttu-id="f98f3-157">**Hedef Framework değişiklik** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-157">The **Target Framework Change** dialog box is displayed.</span></span>  
  
6.  <span data-ttu-id="f98f3-158">İçinde **hedef Framework değişiklik** iletişim kutusu, tıklatın **Evet**.</span><span class="sxs-lookup"><span data-stu-id="f98f3-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>  
  
     <span data-ttu-id="f98f3-159">Proje kapatılır ve daha sonra yeniden açılacak.</span><span class="sxs-lookup"><span data-stu-id="f98f3-159">The project is closed and is then reopened.</span></span>  
  
7.  <span data-ttu-id="f98f3-160">Aşağıdaki adımları izleyerek önbelleğe alma derlemesine başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f98f3-160">Add a reference to the caching assembly by following these steps:</span></span>  
  
    1.  <span data-ttu-id="f98f3-161">İçinde **Çözüm Gezgini**, proje adına sağ tıklayın ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="f98f3-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="f98f3-162">Seçin **.NET** sekmesine `System.Runtime.Caching`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="f98f3-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>  
  
#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="f98f3-163">Visual C# projesinde hedef .NET Framework değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="f98f3-163">To change the target .NET Framework in a Visual C# project</span></span>  
  
1.  <span data-ttu-id="f98f3-164">İçinde **Çözüm Gezgini**, proje adına sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="f98f3-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>  
  
     <span data-ttu-id="f98f3-165">Uygulama için Özellikler penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-165">The properties window for the application is displayed.</span></span>  
  
2.  <span data-ttu-id="f98f3-166">Tıklatın **uygulama** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="f98f3-166">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="f98f3-167">İçinde **hedef framework** listesinde [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f98f3-167">In the **Target framework** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="f98f3-168">(Seçmeyin **.NET Framework 4 istemci profili**.)</span><span class="sxs-lookup"><span data-stu-id="f98f3-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>  
  
4.  <span data-ttu-id="f98f3-169">Aşağıdaki adımları izleyerek önbelleğe alma derlemesine başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f98f3-169">Add a reference to the caching assembly by following these steps:</span></span>  
  
    1.  <span data-ttu-id="f98f3-170">Sağ **başvuruları** klasörünü ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="f98f3-170">Right-click the **References** folder and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="f98f3-171">Seçin **.NET** sekmesine `System.Runtime.Caching`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="f98f3-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>  
  
## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="f98f3-172">WPF penceresi düğme ekleme</span><span class="sxs-lookup"><span data-stu-id="f98f3-172">Adding a Button to the WPF Window</span></span>  
 <span data-ttu-id="f98f3-173">Ardından, işlemi düğme denetimi ekler ve düğmenin için bir olay işleyicisi oluşturun `Click` olay.</span><span class="sxs-lookup"><span data-stu-id="f98f3-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="f98f3-174">Daha sonra Düğmeye tıkladığınızda, metin dosyasının içeriğini önbelleğe alınan görüntülenir ve böylece kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f98f3-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>  
  
#### <a name="to-add-a-button-control"></a><span data-ttu-id="f98f3-175">Düğme denetimi eklemek için</span><span class="sxs-lookup"><span data-stu-id="f98f3-175">To add a button control</span></span>  
  
1.  <span data-ttu-id="f98f3-176">İçinde **Çözüm Gezgini**, açmak için MainWindow.xaml dosyasını çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f98f3-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>  
  
2.  <span data-ttu-id="f98f3-177">Gelen **araç**altında **genel WPF denetimlerinin**, sürükleyin bir `Button` denetimini `MainWindow` penceresi.</span><span class="sxs-lookup"><span data-stu-id="f98f3-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>  
  
3.  <span data-ttu-id="f98f3-178">İçinde **özellikleri** penceresindeki ayarlayın `Content` özelliği `Button` denetimini **önbelleğe alma**.</span><span class="sxs-lookup"><span data-stu-id="f98f3-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>  
  
## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="f98f3-179">Önbelleği başlatılıyor ve bir giriş önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="f98f3-179">Initializing the Cache and Caching an Entry</span></span>  
 <span data-ttu-id="f98f3-180">Sonra aşağıdaki görevleri gerçekleştirmek için kod ekleyeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="f98f3-180">Next, you will add the code to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="f98f3-181">Önbellek sınıfının bir örneğini oluşturma — diğer bir deyişle, yeni bir örneğini <xref:System.Runtime.Caching.MemoryCache> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f98f3-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>  
  
-   <span data-ttu-id="f98f3-182">Önbellek kullandığını belirtirseniz bir <xref:System.Runtime.Caching.HostFileChangeMonitor> metin dosyasındaki değişiklikleri izlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="f98f3-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>  
  
-   <span data-ttu-id="f98f3-183">Metin dosyası okuma ve içeriğinin bir önbellek girişi olarak önbelleğe.</span><span class="sxs-lookup"><span data-stu-id="f98f3-183">Read the text file and cache its contents as a cache entry.</span></span>  
  
-   <span data-ttu-id="f98f3-184">Önbelleğe alınan metin dosyasının içeriğini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f98f3-184">Display the contents of the cached text file.</span></span>  
  
#### <a name="to-create-the-cache-object"></a><span data-ttu-id="f98f3-185">Önbellek nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f98f3-185">To create the cache object</span></span>  
  
1.  <span data-ttu-id="f98f3-186">Olay işleyici MainWindow.xaml.cs veya MainWindow.Xaml.vb dosyasında oluşturmak için yeni eklenen düğmesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f98f3-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>  
  
2.  <span data-ttu-id="f98f3-187">(Önce sınıf bildirimi) dosyasının üst kısmında, aşağıdaki ekleyin `Imports` (Visual Basic) veya `using` deyimleri (C#):</span><span class="sxs-lookup"><span data-stu-id="f98f3-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  <span data-ttu-id="f98f3-188">Olay işleyicisi önbellek nesnesi örneği oluşturmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f98f3-188">In the event handler, add the following code to instantiate the cache object:</span></span>  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     <span data-ttu-id="f98f3-189"><xref:System.Runtime.Caching.ObjectCache> Bir bellek içi nesne önbelleği sağlayan yerleşik bir sınıf bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="f98f3-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>  
  
4.  <span data-ttu-id="f98f3-190">Adlı bir önbellek girişi içeriğini okumak için aşağıdaki kodu ekleyin `filecontents`:</span><span class="sxs-lookup"><span data-stu-id="f98f3-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  <span data-ttu-id="f98f3-191">Önbellek girdisi adlı olup olmadığını denetlemek için aşağıdaki kodu ekleyin `filecontents` bulunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="f98f3-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     <span data-ttu-id="f98f3-192">Belirtilen önbellek girişi mevcut değilse, metin dosyası okuma ve önbelleğe bir önbellek girişi olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f98f3-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>  
  
6.  <span data-ttu-id="f98f3-193">İçinde `if/then` engellemek, yeni bir oluşturmak için aşağıdaki kodu ekleyin <xref:System.Runtime.Caching.CacheItemPolicy> önbellek girişinin 10 saniye sonra süresi belirtir nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f98f3-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     <span data-ttu-id="f98f3-194">Hiçbir çıkarma veya sona erme bilgileri verdiyse, varsayılan değer <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, önbellek girişlerinin başka bir deyişle, süresi dolmayacak tabanlı yalnızca mutlak bir saat.</span><span class="sxs-lookup"><span data-stu-id="f98f3-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="f98f3-195">Bunun yerine, yalnızca bellek baskısı olduğunda önbellek girişlerinin süresinin.</span><span class="sxs-lookup"><span data-stu-id="f98f3-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="f98f3-196">En iyi uygulama, mutlak veya kaplamayı sona erme her zaman açıkça sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f98f3-196">As a best practice, you should always explicitly provide either an absolute or a siding expiration.</span></span>  
  
7.  <span data-ttu-id="f98f3-197">İçinde `if/then` engelleme ve önceki adımda eklediğiniz kodun, izlemek ve metin dosyasının yolunu koleksiyona eklemek istediğiniz dosya yolları için bir koleksiyon oluşturmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f98f3-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>  
  
    ```vb  
    Dim filePaths As New List(Of String)()  
    filePaths.Add("c:\cache\cacheText.txt")  
    ```  
  
    ```csharp  
    List<string> filePaths = new List<string>();  
    filePaths.Add("c:\\cache\\cacheText.txt");  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f98f3-198">Kullanmak istediğiniz metin dosyası olup olmadığını `c:\cache\cacheText.txt`, metin dosyasının bulunduğu kullanmak istediğiniz yolu belirtin.</span><span class="sxs-lookup"><span data-stu-id="f98f3-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>  
  
8.  <span data-ttu-id="f98f3-199">Yeni bir eklemek için aşağıdaki kodu ekleyin önceki adımda eklediğiniz koddan <xref:System.Runtime.Caching.HostFileChangeMonitor> değişiklik koleksiyonuna nesnesi için önbellek girişi izler:</span><span class="sxs-lookup"><span data-stu-id="f98f3-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     <span data-ttu-id="f98f3-200"><xref:System.Runtime.Caching.HostFileChangeMonitor> Nesne metin dosyanın yolu izler ve değişiklikleri oluştuğunda önbellek bildirir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="f98f3-201">Dosya içeriği değişirse bu örnekte, önbellek girişinin süresi dolar.</span><span class="sxs-lookup"><span data-stu-id="f98f3-201">In this example, the cache entry will expire if the content of the file changes.</span></span>  
  
9. <span data-ttu-id="f98f3-202">Önceki adımda eklediğiniz koddan metin dosyasının içeriğini okumak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f98f3-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     <span data-ttu-id="f98f3-203">Önbellek girişinin süresi dolduğunda görmeye olmayacaktır tarih ve saat damgası eklenir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>  
  
10. <span data-ttu-id="f98f3-204">Dosya içeriğini önbellek nesnesi olarak eklemek için aşağıdaki kodu ekleyin önceki adımda eklediğiniz koddan bir <xref:System.Runtime.Caching.CacheItem> örneği:</span><span class="sxs-lookup"><span data-stu-id="f98f3-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     <span data-ttu-id="f98f3-205">Nasıl önbellek girişi geçirerek çıkarılmasına hakkında bilgi belirtmek <xref:System.Runtime.Caching.CacheItemPolicy> parametre olarak daha önce oluşturduğunuz nesne.</span><span class="sxs-lookup"><span data-stu-id="f98f3-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>  
  
11. <span data-ttu-id="f98f3-206">Sonra `if/then` engellemek, önbelleğe alınmış dosya içeriğini bir ileti kutusu içinde görüntülemek için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f98f3-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. <span data-ttu-id="f98f3-207">İçinde **yapı** menüsünde tıklatın **yapı WPFCaching** projenizi yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="f98f3-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>  
  
## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="f98f3-208">WPF uygulamasında önbelleğe almayı test etme</span><span class="sxs-lookup"><span data-stu-id="f98f3-208">Testing Caching in the WPF Application</span></span>  
 <span data-ttu-id="f98f3-209">Şimdi uygulamayı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f98f3-209">You can now test the application.</span></span>  
  
#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="f98f3-210">WPF uygulamasında önbelleğe alma işlemini sınamak için</span><span class="sxs-lookup"><span data-stu-id="f98f3-210">To test caching in the WPF application</span></span>  
  
1.  <span data-ttu-id="f98f3-211">Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f98f3-211">Press CTRL+F5 to run the application.</span></span>  
  
     <span data-ttu-id="f98f3-212">`MainWindow` Penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-212">The `MainWindow` window is displayed.</span></span>  
  
2.  <span data-ttu-id="f98f3-213">Tıklatın **alma önbellek**.</span><span class="sxs-lookup"><span data-stu-id="f98f3-213">Click **Get Cache**.</span></span>  
  
     <span data-ttu-id="f98f3-214">Önbelleğe alınmış içeriği metin dosyasından bir ileti kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="f98f3-215">Dosyanın zaman damgasını dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f98f3-215">Notice the timestamp on the file.</span></span>  
  
3.  <span data-ttu-id="f98f3-216">İleti kutusunu kapatın ve ardından **önbelleğe alma** yeniden**.**</span><span class="sxs-lookup"><span data-stu-id="f98f3-216">Close the message box and then click **Get Cache** again**.**</span></span>  
  
     <span data-ttu-id="f98f3-217">Zaman damgası değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="f98f3-217">The timestamp is unchanged.</span></span> <span data-ttu-id="f98f3-218">Bu, önbelleğe alınmış içeriği görüntülendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-218">This indicates the cached content is displayed.</span></span>  
  
4.  <span data-ttu-id="f98f3-219">10 saniye veya daha fazla bekleyin ve ardından **önbelleğe alma** yeniden.</span><span class="sxs-lookup"><span data-stu-id="f98f3-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>  
  
     <span data-ttu-id="f98f3-220">Bu yeni bir zaman damgası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="f98f3-221">Bu ilke sona önbellek girişi sağlar ve yeni önbelleğe alınmış içeriği görüntülendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>  
  
5.  <span data-ttu-id="f98f3-222">Oluşturduğunuz metin dosyasını bir metin düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="f98f3-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="f98f3-223">Herhangi bir değişiklik henüz yapmayın.</span><span class="sxs-lookup"><span data-stu-id="f98f3-223">Do not make any changes yet.</span></span>  
  
6.  <span data-ttu-id="f98f3-224">İleti kutusunu kapatın ve ardından **önbelleğe alma** yeniden**.**</span><span class="sxs-lookup"><span data-stu-id="f98f3-224">Close the message box and then click **Get Cache** again**.**</span></span>  
  
     <span data-ttu-id="f98f3-225">Zaman damgası yeniden dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f98f3-225">Notice the timestamp again.</span></span>  
  
7.  <span data-ttu-id="f98f3-226">Metin dosyasına bir değişikliği yapın ve ardından dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f98f3-226">Make a change to the text file and then save the file.</span></span>  
  
8.  <span data-ttu-id="f98f3-227">İleti kutusunu kapatın ve ardından **önbelleğe alma** yeniden.</span><span class="sxs-lookup"><span data-stu-id="f98f3-227">Close the message box and then click **Get Cache** again.</span></span>  
  
     <span data-ttu-id="f98f3-228">Bu ileti kutusu güncelleştirilmiş içerik metin dosyasını ve yeni bir zaman damgası içerir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="f98f3-229">Bu, hemen dosya değiştirildiğinde mutlak zaman aşımı süresi dolmamış olsa da ana bilgisayar dosyası değişiklik İzleyicisi önbellek girişi çıkarılacak olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f98f3-230">20 saniye veya daha fazla bilgi için dosyada değişiklik yapmak daha fazla süre izin vermek için çıkarma süresini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="f98f3-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>  
  
## <a name="code-example"></a><span data-ttu-id="f98f3-231">Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="f98f3-231">Code Example</span></span>  
 <span data-ttu-id="f98f3-232">Bu kılavuzu tamamladıktan sonra oluşturduğunuz proje kodunu aşağıdaki örnek benzer.</span><span class="sxs-lookup"><span data-stu-id="f98f3-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f98f3-233">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f98f3-233">See Also</span></span>  
 <xref:System.Runtime.Caching.MemoryCache>  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching>  
 [<span data-ttu-id="f98f3-234">.NET Framework Uygulamalarında Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="f98f3-234">Caching in .NET Framework Applications</span></span>](../../../../docs/framework/performance/caching-in-net-framework-applications.md)
