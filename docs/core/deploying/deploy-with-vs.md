---
title: Visual Studio ile .NET Core uygulamaları dağıtma
description: Visual Studio ile .NET Core uygulaması dağıtmayı öğrenin.
author: rpetrusha
ms.author: ronpet
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 4e8fbfa14c241c79f8708dfc2b288eeff2899891
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216243"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a><span data-ttu-id="705db-103">Visual Studio ile .NET Core uygulamaları dağıtma</span><span class="sxs-lookup"><span data-stu-id="705db-103">Deploy .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="705db-104">Bir .NET Core uygulamasını, uygulama ikililerini *içeren, ancak*hedef sistemde .NET Core varlığına veya her ikisini de içeren bir *bağımsız dağıtım*olarak bir .NET Core uygulaması dağıtabilirsiniz. uygulamanız ve .NET Core ikilileri.</span><span class="sxs-lookup"><span data-stu-id="705db-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="705db-105">.NET Core uygulama dağıtımına genel bir bakış için bkz. [.NET Core uygulama dağıtımı](index.md).</span><span class="sxs-lookup"><span data-stu-id="705db-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="705db-106">Aşağıdaki bölümlerde, aşağıdaki dağıtım türlerini oluşturmak için Microsoft Visual Studio nasıl kullanılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="705db-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="705db-107">Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="705db-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="705db-108">Üçüncü taraf bağımlılıklarla çerçeveye bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="705db-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="705db-109">Kendi içinde dağıtım</span><span class="sxs-lookup"><span data-stu-id="705db-109">Self-contained deployment</span></span>
- <span data-ttu-id="705db-110">Üçüncü taraf bağımlılıklarla kendi kendine kapsanan dağıtım</span><span class="sxs-lookup"><span data-stu-id="705db-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="705db-111">.NET Core uygulamaları geliştirmek için Visual Studio 'Yu kullanma hakkında bilgi için bkz. [Windows üzerinde .NET Core önkoşulları](../windows-prerequisites.md#prerequisites-to-develop-net-core-apps-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="705db-111">For information on using Visual Studio to develop .NET Core applications, see [Prerequisites for .NET Core on Windows](../windows-prerequisites.md#prerequisites-to-develop-net-core-apps-with-visual-studio).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="705db-112">Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="705db-112">Framework-dependent deployment</span></span>

<span data-ttu-id="705db-113">Bir üçüncü taraf bağımlılığı olmadan çerçeveye bağlı bir dağıtımı dağıtmak, uygulamayı oluşturma, test etme ve yayımlamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="705db-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="705db-114">İçinde C# yazılmış basit bir örnek işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="705db-114">A simple example written in C# illustrates the process.</span></span>  

1. <span data-ttu-id="705db-115">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="705db-115">Create the project.</span></span>

   <span data-ttu-id="705db-116">**Dosya** > **Yeni** > **Proje**’yi seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="705db-117">**Yeni proje** C# iletişim kutusunda, dil (veya Visual Basic) Proje kategorilerini **yüklü** proje türleri bölmesinde genişletin, **.NET Core**' u seçin ve ardından orta bölmedeki **konsol uygulaması (.NET Core)** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="705db-118">**Ad** metin kutusuna "fdd" gibi bir proje adı girin.</span><span class="sxs-lookup"><span data-stu-id="705db-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="705db-119">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="705db-120">Uygulamanın kaynak kodunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="705db-120">Add the application's source code.</span></span>

   <span data-ttu-id="705db-121">Düzenleyicide *program.cs* veya *program. vb* dosyasını açın ve otomatik oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="705db-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="705db-122">Kullanıcıdan metin girmesini ve Kullanıcı tarafından girilen tek tek kelimeleri görüntülediğini ister.</span><span class="sxs-lookup"><span data-stu-id="705db-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="705db-123">Giriş metnindeki sözcükleri ayırmak için `\w+` normal ifadeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="705db-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="705db-124">Uygulamanızın hata ayıklama derlemesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="705db-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="705db-125">Yapı**Yapı çözümünü** **seçin.**  > </span><span class="sxs-lookup"><span data-stu-id="705db-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="705db-126">Ayrıca, **hata** > ayıklama**başlatma hata ayıklamayı**seçerek uygulamanızın hata ayıklama derlemesini derleyip çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="705db-127">Uygulamanızı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="705db-127">Deploy your app.</span></span>

   <span data-ttu-id="705db-128">Programı hata ayıkladıktan ve test ettikten sonra, uygulamanızla birlikte dağıtılacak dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="705db-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="705db-129">Visual Studio 'dan yayımlamak için şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="705db-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="705db-130">Uygulamanızın bir sürümünü (hata ayıklama yerine) oluşturmak için, araç çubuğundaki çözüm yapılandırmasını **Hata Ayıkla** 'dan **Release** olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="705db-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="705db-131">**Çözüm Gezgini** ' de projeye (çözüme değil) sağ tıklayın ve **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="705db-132">**Yayımla** sekmesinde **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="705db-133">Visual Studio, uygulamanızı oluşturan dosyaları yerel dosya sistemine yazar.</span><span class="sxs-lookup"><span data-stu-id="705db-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="705db-134">**Yayımla** sekmesinde artık tek bir profil, **folderprofile**gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="705db-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="705db-135">Profilin yapılandırma ayarları, sekmesinin **Özet** bölümünde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="705db-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="705db-136">Elde edilen dosyalar, Windows 'da ve `Publish` `publish` projenizin *.\bin\release\netcoreapp2.1* alt dizininin bir alt dizininde bulunan UNIX sistemlerinde adlı bir dizine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="705db-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="705db-137">Yayımlama işlemi, uygulamanızın dosyalarıyla birlikte, uygulamanız hakkındaki hata ayıklama bilgilerini içeren bir program veritabanı (. pdb) dosyası yayar.</span><span class="sxs-lookup"><span data-stu-id="705db-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="705db-138">Dosya öncelikle hata ayıklama özel durumları için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="705db-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="705db-139">Bunu uygulamanızın dosyalarıyla paketlemeyi seçemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="705db-140">Ancak, uygulamanızın yayın derlemesinde hata ayıklamak istediğiniz olaya kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="705db-141">Tüm uygulama dosyalarını dilediğiniz şekilde dağıtın.</span><span class="sxs-lookup"><span data-stu-id="705db-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="705db-142">Örneğin, bunları bir ZIP dosyasında paketleyebilir, basit `copy` bir komut kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="705db-143">Kullanıcılar yüklendikten sonra, `dotnet` komutunu kullanarak ve gibi uygulama dosya adını `dotnet fdd.dll`sağlayarak uygulamanızı yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="705db-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="705db-144">Uygulama ikililerinin yanı sıra, yükleyicinizin de paylaşılan çerçeve yükleyicisini paketi veya uygulama yüklemesinin bir parçası olarak bir önkoşul olarak denetlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="705db-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="705db-145">Paylaşılan Framework 'ün yüklenmesi, makine genelinde olduğundan yönetici/kök erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="705db-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="705db-146">Üçüncü taraf bağımlılıklarla çerçeveye bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="705db-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="705db-147">Bir veya daha fazla üçüncü taraf bağımlılığı olan çerçeveye bağlı bir dağıtımı dağıtmak, tüm bağımlılıkların projeniz için kullanılabilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="705db-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="705db-148">Uygulamanızı derlemek için aşağıdaki ek adımlar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="705db-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="705db-149">Projenize bir NuGet paketine başvuru eklemek için **NuGet paket yöneticisini** kullanın; paket sisteminizde zaten yoksa, uygulamayı da yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="705db-150">Paket Yöneticisi 'ni açmak için **Araçlar** > **NuGet Paket Yöneticisi** > **çözüm için NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="705db-151">Sisteminizde yüklü `Newtonsoft.Json` olduğunu doğrulayın ve yoksa yükleme yapın.</span><span class="sxs-lookup"><span data-stu-id="705db-151">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="705db-152">**Yüklü** sekme, sisteminizde yüklü olan NuGet paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="705db-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="705db-153">Orada listelenmemişse **, araştırma sekmesini seçin** ve arama kutusuna "Newtonsoft. JSON" yazın. `Newtonsoft.Json`</span><span class="sxs-lookup"><span data-stu-id="705db-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="705db-154">Sağ bölmedeki ve ' yi seçerek, yüklemeyi seçmeden önce projenizi seçin. `Newtonsoft.Json`</span><span class="sxs-lookup"><span data-stu-id="705db-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="705db-155">Zaten sisteminizde yüklüyse, **çözüm için paketleri Yönet** sekmesinin sağ bölmesinde projenizi seçerek projenize ekleyin. `Newtonsoft.Json`</span><span class="sxs-lookup"><span data-stu-id="705db-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="705db-156">Üçüncü taraf bağımlılıkları olan çerçeveye bağlı bir dağıtımın yalnızca üçüncü taraf bağımlılıkları olarak taşındığına göz önünde kalabileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="705db-156">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="705db-157">Örneğin, bir üçüncü taraf kitaplığı yalnızca macOS destekliyorsa, uygulama Windows sistemlerine taşınabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="705db-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="705db-158">Bu durum, üçüncü taraf bağımlılığının yerel koda bağlı olması durumunda meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="705db-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="705db-159">Bunun iyi bir örneği, [libuv](https://github.com/libuv/libuv)üzerinde yerel bir bağımlılık gerektiren [Kestrel sunucusudur](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel).</span><span class="sxs-lookup"><span data-stu-id="705db-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="705db-160">Bu tür üçüncü taraf bağımlılığı olan bir uygulama için FDD oluşturulduğunda, yayımlanan çıktı, yerel bağımlılığın desteklediği (ve NuGet paketinde bulunan) her [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) için bir klasör içerir.</span><span class="sxs-lookup"><span data-stu-id="705db-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a><span data-ttu-id="705db-161">Üçüncü taraf bağımlılıkları olmayan kendi kendine kapsanan dağıtım</span><span class="sxs-lookup"><span data-stu-id="705db-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="705db-162">Bir üçüncü taraf bağımlılığı olmadan kendi içinde bir dağıtımı dağıtmak, projeyi oluşturma, *csproj* dosyasını değiştirme, uygulama oluşturma, test etme ve uygulamayı yayımlamayı kapsar.</span><span class="sxs-lookup"><span data-stu-id="705db-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="705db-163">İçinde C# yazılmış basit bir örnek işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="705db-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="705db-164">Yalnızca çerçeveye bağımlı bir dağıtımda olduğu gibi projenizi oluşturarak, kodlayarak ve test etmeye başlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="705db-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="705db-165">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="705db-165">Create the project.</span></span>

   <span data-ttu-id="705db-166">**Dosya** > **Yeni** > **Proje**’yi seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="705db-167">**Yeni proje** C# iletişim kutusunda, dil (veya Visual Basic) Proje kategorilerini **yüklü** proje türleri bölmesinde genişletin, **.NET Core**' u seçin ve ardından orta bölmedeki **konsol uygulaması (.NET Core)** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="705db-168">**Ad** metin kutusuna "SCD" gibi bir proje adı girin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="705db-169">Uygulamanın kaynak kodunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="705db-169">Add the application's source code.</span></span>

   <span data-ttu-id="705db-170">Düzenleyicinizde *program.cs* veya *program. vb* dosyasını açın ve otomatik oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="705db-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="705db-171">Kullanıcıdan metin girmesini ve Kullanıcı tarafından girilen tek tek kelimeleri görüntülediğini ister.</span><span class="sxs-lookup"><span data-stu-id="705db-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="705db-172">Giriş metnindeki sözcükleri ayırmak için `\w+` normal ifadeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="705db-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="705db-173">Genelleştirme sabit modunu kullanmak isteyip istemediğinizi belirleme.</span><span class="sxs-lookup"><span data-stu-id="705db-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="705db-174">Özellikle uygulamanız Linux hedefliyorsa, [Genelleştirme sabit modundan](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)yararlanarak dağıtımınızın toplam boyutunu azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="705db-175">Genelleştirme sabit modu, genel olarak uyumlu olmayan ve [sabit kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)biçimlendirme kurallarını, büyük/küçük harf kurallarını ve dize karşılaştırmayı ve sıralama düzenini kullanabilen uygulamalar için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="705db-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="705db-176">Sabit modu etkinleştirmek için, **Çözüm Gezgini**' de projenize (çözüm değil) sağ tıklayın ve **scd. csproj Düzenle** ' yi seçin veya **scd. vbproj**' i düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="705db-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="705db-177">Ardından, aşağıdaki vurgulanmış satırları dosyaya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="705db-177">Then add the following highlighted lines to the file:</span></span>

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. <span data-ttu-id="705db-178">Uygulamanızın hata ayıklama derlemesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="705db-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="705db-179">Yapı**Yapı çözümünü** **seçin.**  > </span><span class="sxs-lookup"><span data-stu-id="705db-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="705db-180">Ayrıca, **hata** > ayıklama**başlatma hata ayıklamayı**seçerek uygulamanızın hata ayıklama derlemesini derleyip çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="705db-181">Bu hata ayıklama adımı, ana bilgisayar platformunda çalışırken uygulamanızdaki sorunları belirlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="705db-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="705db-182">Yine de hedef Platformlarınızın her birinde test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="705db-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="705db-183">Genelleştirme sabit modunu etkinleştirdiyseniz, özellikle kültüre duyarlı verilerin yokluğunun uygulamanız için uygun olup olmadığını test ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="705db-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="705db-184">Hata ayıklamayı tamamladıktan sonra, kendi içindeki dağıtımınızı yayımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="705db-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="705db-185">Visual Studio 15,6 ve öncesi</span><span class="sxs-lookup"><span data-stu-id="705db-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="705db-186">Programı hata ayıkladıktan ve test ettikten sonra, hedeflediği her platform için uygulamanıza dağıtılacak dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="705db-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="705db-187">Uygulamanızı Visual Studio 'dan yayımlamak için şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="705db-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="705db-188">Uygulamanızın hedeflenecek platformları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="705db-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="705db-189">**Çözüm Gezgini** ' de projenize (çözüm değil) sağ tıklayın ve **scd. csproj öğesini Düzenle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="705db-190">Csproj dosyanızın `<RuntimeIdentifiers>` `<PropertyGroup>` bölümünde uygulamanızın hedeflediği platformları tanımlayan bir etiket oluşturun ve hedeflediğiniz her platformun çalışma zamanı tanımlayıcısını (RID) belirtin.</span><span class="sxs-lookup"><span data-stu-id="705db-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="705db-191">Ayrıca, RIDs 'yi ayırmak için noktalı virgül eklemeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="705db-191">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="705db-192">Çalışma zamanı tanımlayıcılarının listesi için bkz. [Runtime Identifier Catalog](../rid-catalog.md) .</span><span class="sxs-lookup"><span data-stu-id="705db-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="705db-193">Örneğin, aşağıdaki örnek, uygulamanın 64 bitlik Windows 10 işletim sistemleri ve 64 bit işletim sistemi X sürümü 10,11 işletim sisteminde çalıştığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="705db-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="705db-194">Öğesinin csproj dosyanızda sahip olduğunuz herhangi birine `<PropertyGroup>` gidebileceğini unutmayın. `<RuntimeIdentifiers>`</span><span class="sxs-lookup"><span data-stu-id="705db-194">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="705db-195">Bu bölümde daha sonra bir örnek *csproj* dosyası belirir.</span><span class="sxs-lookup"><span data-stu-id="705db-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="705db-196">Uygulamanızı yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="705db-196">Publish your app.</span></span>

   <span data-ttu-id="705db-197">Programı hata ayıkladıktan ve test ettikten sonra, hedeflediği her platform için uygulamanıza dağıtılacak dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="705db-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="705db-198">Uygulamanızı Visual Studio 'dan yayımlamak için şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="705db-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="705db-199">Uygulamanızın bir sürümünü (hata ayıklama yerine) oluşturmak için, araç çubuğundaki çözüm yapılandırmasını **Hata Ayıkla** 'dan **Release** olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="705db-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="705db-200">**Çözüm Gezgini** ' de projeye (çözüme değil) sağ tıklayın ve **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="705db-201">**Yayımla** sekmesinde **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="705db-202">Visual Studio, uygulamanızı oluşturan dosyaları yerel dosya sistemine yazar.</span><span class="sxs-lookup"><span data-stu-id="705db-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="705db-203">**Yayımla** sekmesinde artık tek bir profil, **folderprofile**gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="705db-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="705db-204">Profilin yapılandırma ayarları, sekmesinin **Özet** bölümünde gösterilir. **Hedef çalışma zamanı** hangi çalışma zamanının yayımlandığını tanımlar ve **hedef konum** , kendinden bağımsız dağıtım dosyalarının yazıldığı yeri belirler.</span><span class="sxs-lookup"><span data-stu-id="705db-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="705db-205">Visual Studio varsayılan olarak tüm yayımlanan dosyaları tek bir dizine yazar.</span><span class="sxs-lookup"><span data-stu-id="705db-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="705db-206">Kolaylık olması için, her bir hedef çalışma zamanı için ayrı profiller oluşturmak ve yayımlanan dosyaları platforma özgü bir dizine yerleştirmek en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="705db-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="705db-207">Bu, her hedef platform için ayrı bir yayımlama profili oluşturmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="705db-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="705db-208">Bu nedenle, şimdi aşağıdakileri yaparak her platform için uygulamayı yeniden oluşturun:</span><span class="sxs-lookup"><span data-stu-id="705db-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="705db-209">**Yayımla** iletişim kutusunda **Yeni Profil oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="705db-210">**Bir yayımlama hedefi seç** iletişim kutusunda, **klasör seçin** konumunu *Bin\release\publishoutput\win10-x64*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="705db-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="705db-211">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-211">Select **OK**.</span></span>

         1. <span data-ttu-id="705db-212">Profiller listesinden yeni profili (**FolderProfile1**) seçin ve `win10-x64` **hedef çalışma zamanının** olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="705db-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="705db-213">Değilse, **Ayarlar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="705db-214">**Profil ayarları** iletişim kutusunda **hedef çalışma zamanını** olarak `win10-x64` değiştirip **Kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="705db-215">Aksi takdirde **iptal**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="705db-216">Uygulamanızı 64 bitlik Windows 10 platformları için yayımlamak üzere **Yayımla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="705db-217">`osx.10.11-x64` Platform için bir profil oluşturmak üzere önceki adımları tekrar izleyin.</span><span class="sxs-lookup"><span data-stu-id="705db-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="705db-218">**Hedef konum** *Bin\Release\PublishOutput\osx.10.11-x64*ve **hedef çalışma zamanı** `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="705db-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="705db-219">Visual Studio 'Nun bu profile atadığı ad **FolderProfile2**' dir.</span><span class="sxs-lookup"><span data-stu-id="705db-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="705db-220">Her hedef konumun, uygulamanızı başlatmak için gereken tüm dosya (hem uygulama dosyalarınız hem de tüm .NET Core dosyaları) kümesini içerdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="705db-220">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="705db-221">Yayımlama işlemi, uygulamanızın dosyalarıyla birlikte, uygulamanız hakkındaki hata ayıklama bilgilerini içeren bir program veritabanı (. pdb) dosyası yayar.</span><span class="sxs-lookup"><span data-stu-id="705db-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="705db-222">Dosya öncelikle hata ayıklama özel durumları için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="705db-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="705db-223">Bunu uygulamanızın dosyalarıyla paketlemeyi seçemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="705db-224">Ancak, uygulamanızın yayın derlemesinde hata ayıklamak istediğiniz olaya kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="705db-225">Yayınlanan dosyaları dilediğiniz gibi dağıtın.</span><span class="sxs-lookup"><span data-stu-id="705db-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="705db-226">Örneğin, bunları bir ZIP dosyasında paketleyebilir, basit `copy` bir komut kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="705db-227">Bu proje için tüm *csproj* dosyası aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="705db-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="705db-228">Visual Studio 15,7 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="705db-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="705db-229">Programı hata ayıkladıktan ve test ettikten sonra, hedeflediği her platform için uygulamanıza dağıtılacak dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="705db-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="705db-230">Bu, her hedef platform için ayrı bir profil oluşturmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="705db-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="705db-231">Uygulamanızın hedeflediği her platform için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="705db-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="705db-232">Hedef platformunuz için bir profil oluşturun.</span><span class="sxs-lookup"><span data-stu-id="705db-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="705db-233">Oluşturduğunuz ilk profildir, **Çözüm Gezgini** ' de projeye (çözüme değil) sağ tıklayın ve **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="705db-234">Zaten bir profil oluşturduysanız, zaten açık değilse **Yayımla** iletişim kutusunu açmak için projeye sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="705db-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="705db-235">Ardından **Yeni profil**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="705db-236">**Bir Yayımla hedefi seç** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="705db-236">The **Pick a Publish Target** dialog box opens.</span></span>
  
1. <span data-ttu-id="705db-237">Visual Studio 'Nun uygulamanızı yayımlayıp konumunu seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="705db-238">Yalnızca tek bir platforma yayımlıyorsanız, **klasör seçin** metin kutusunda varsayılan değeri kabul edebilirsiniz; Bu, uygulamanızın çerçeveye bağımlı dağıtımını \*\<Project-Directory > \bin\release\netcoreapp2,\publish\* dizinine yayınlar.</span><span class="sxs-lookup"><span data-stu-id="705db-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework dependent deployment of your application to the \*\<project-directory>\bin\Release\netcoreapp2.1\publish\* directory.</span></span>

   <span data-ttu-id="705db-239">Birden fazla platforma yayımlıyorsanız, hedef platformu tanımlayan bir dize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="705db-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="705db-240">Örneğin, "Linux" dizesini dosya yoluna eklerseniz, Visual Studio uygulamanızın  *\<çerçeveye bağımlı dağıtımını, App-Directory > \bin\release\netcoreapp2,\publish\linux* dizinine yayımlar.</span><span class="sxs-lookup"><span data-stu-id="705db-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="705db-241">**Yayımla** düğmesinin yanındaki açılan liste simgesini seçerek profili oluşturun ve **Profil oluştur**' a seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="705db-242">Sonra profili oluşturmak için **Profil oluştur** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="705db-243">Kendinden bağımsız bir dağıtım yayımladığını ve uygulamanızın hedeflenecek bir platform tanımlacağınızı belirtin.</span><span class="sxs-lookup"><span data-stu-id="705db-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="705db-244">**Yayımla** Iletişim kutusunda **profil ayarları** Iletişim kutusunu açmak için **Yapılandır** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="705db-245">**Dağıtım modu** liste kutusunda **kendine ait** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="705db-246">**Hedef çalışma zamanı** liste kutusunda, uygulamanızın hedeflediği platformlardan birini seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="705db-247">Değişikliklerinizi kabul etmek ve iletişim kutusunu kapatmak için **Kaydet** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="705db-248">Profilinizi adlandırın.</span><span class="sxs-lookup"><span data-stu-id="705db-248">Name your profile.</span></span>

   1. <span data-ttu-id="705db-249">Profilinizi adlandırmak için **Eylemler** > **Yeniden Adlandır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="705db-250">Profilinize hedef platformu tanımlayan bir ad atayın ve ardından \**Kaydet*' i seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="705db-251">Uygulamanızın hedeflediği ek hedef platformları tanımlamak için bu adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="705db-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="705db-252">Profillerinizi yapılandırdınız ve şimdi uygulamanızı yayımlamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="705db-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="705db-253">Bunu yapmak için:</span><span class="sxs-lookup"><span data-stu-id="705db-253">To do this:</span></span>

   1. <span data-ttu-id="705db-254">**Yayımla** penceresi açık değilse, **Çözüm Gezgini** ' de projeye (çözüm değil) sağ tıklayın ve **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="705db-255">Yayınlamak istediğiniz profili seçin ve ardından **Yayımla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="705db-256">Bu, yayımlanacak her profil için bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="705db-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="705db-257">Her hedef konumun (örneğimizde, bin\release\netcoreapp2,\publish\\*profile-Name* ' in, uygulamanızı başlatmak için gereken tam dosya kümesini (hem uygulama dosyalarınız hem de tüm .NET Core dosyaları) içerdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="705db-257">Note that each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="705db-258">Yayımlama işlemi, uygulamanızın dosyalarıyla birlikte, uygulamanız hakkındaki hata ayıklama bilgilerini içeren bir program veritabanı (. pdb) dosyası yayar.</span><span class="sxs-lookup"><span data-stu-id="705db-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="705db-259">Dosya öncelikle hata ayıklama özel durumları için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="705db-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="705db-260">Bunu uygulamanızın dosyalarıyla paketlemeyi seçemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="705db-261">Ancak, uygulamanızın yayın derlemesinde hata ayıklamak istediğiniz olaya kaydetmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="705db-262">Yayınlanan dosyaları dilediğiniz gibi dağıtın.</span><span class="sxs-lookup"><span data-stu-id="705db-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="705db-263">Örneğin, bunları bir ZIP dosyasında paketleyebilir, basit `copy` bir komut kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="705db-264">Bu proje için tüm *csproj* dosyası aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="705db-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="705db-265">Ayrıca, Visual Studio, hedeflediğiniz her platform için ayrı bir\*yayımlama profili (. pubxml) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="705db-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="705db-266">Örneğin, Linux profilimiz için dosya (Linux. pubxml) aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="705db-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121. 
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="705db-267">Üçüncü taraf bağımlılıklarla kendi kendine kapsanan dağıtım</span><span class="sxs-lookup"><span data-stu-id="705db-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="705db-268">Bir veya daha fazla üçüncü taraf bağımlılığı ile kendi içindeki bir dağıtımı dağıtmak, bağımlılıkların eklenmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="705db-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="705db-269">Uygulamanızı derlemek için aşağıdaki ek adımlar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="705db-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="705db-270">Projenize bir NuGet paketine başvuru eklemek için **NuGet paket yöneticisini** kullanın; paket sisteminizde zaten yoksa, uygulamayı da yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="705db-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="705db-271">Paket Yöneticisi 'ni açmak için **Araçlar** > **NuGet Paket Yöneticisi** > **çözüm için NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="705db-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="705db-272">Sisteminizde yüklü `Newtonsoft.Json` olduğunu doğrulayın ve yoksa yükleme yapın.</span><span class="sxs-lookup"><span data-stu-id="705db-272">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="705db-273">**Yüklü** sekme, sisteminizde yüklü olan NuGet paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="705db-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="705db-274">Orada listelenmemişse **, araştırma sekmesini seçin** ve arama kutusuna "Newtonsoft. JSON" yazın. `Newtonsoft.Json`</span><span class="sxs-lookup"><span data-stu-id="705db-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="705db-275">Sağ bölmedeki ve ' yi seçerek, yüklemeyi seçmeden önce projenizi seçin. `Newtonsoft.Json`</span><span class="sxs-lookup"><span data-stu-id="705db-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="705db-276">Zaten sisteminizde yüklüyse, **çözüm için paketleri Yönet** sekmesinin sağ bölmesinde projenizi seçerek projenize ekleyin. `Newtonsoft.Json`</span><span class="sxs-lookup"><span data-stu-id="705db-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="705db-277">Bu proje için tüm *csproj* dosyası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="705db-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="705db-278">Visual Studio 15,6 ve öncesi</span><span class="sxs-lookup"><span data-stu-id="705db-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="705db-279">Visual Studio 15,7 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="705db-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

<span data-ttu-id="705db-280">Uygulamanızı dağıttığınızda, uygulamanızda kullanılan tüm üçüncü taraf bağımlılıkları da uygulama dosyalarınıza dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="705db-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="705db-281">Uygulamanın üzerinde çalıştığı sistemde üçüncü taraf kitaplıkları gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="705db-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="705db-282">Yalnızca bir üçüncü taraf kitaplığıyla bu kitaplık tarafından desteklenen platformlar için bir bağımsız dağıtım dağıtabileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="705db-282">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="705db-283">Bu, daha önce yüklenmedikleri müddetçe, yerel bağımlılıkların hedef platformda mevcut olmaması durumunda, çerçeveye bağımlı dağıtımda yerel bağımlılıklarla üçüncü taraf bağımlılıklara sahip olmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="705db-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="705db-284">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="705db-284">See also</span></span>

- [<span data-ttu-id="705db-285">.NET Core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="705db-285">.NET Core Application Deployment</span></span>](index.md)
- [<span data-ttu-id="705db-286">.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="705db-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
