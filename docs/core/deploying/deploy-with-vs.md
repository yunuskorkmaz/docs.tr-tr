---
title: Visual Studio ile .NET Core uygulamalarını dağıtın
description: Visual Studio ile bir .NET Core uygulaması dağıtmayı öğrenin.
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 11a322278ce3ff38964fe2fa389e0b4a58897ec4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449029"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a><span data-ttu-id="55f6d-103">Visual Studio ile .NET Core uygulamalarını dağıtın</span><span class="sxs-lookup"><span data-stu-id="55f6d-103">Deploy .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="55f6d-104">Bir .NET Core uygulamasını, uygulama ikililerinizi içeren, ancak hedef sistemde .NET Core'un varlığına bağlı olan bir *çerçeveye bağımlı dağıtım*olarak veya hem uygulamanızı hem de .NET Core ikililerini içeren bağımsız bir *dağıtım*olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="55f6d-105">.NET Core uygulama dağıtımına genel bakış için [bkz.](index.md)</span><span class="sxs-lookup"><span data-stu-id="55f6d-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="55f6d-106">Aşağıdaki bölümlerde, aşağıdaki türde dağıtımlar oluşturmak için Microsoft Visual Studio'nun nasıl kullanılacağı gösteriş verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="55f6d-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="55f6d-107">Çerçeveye bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="55f6d-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="55f6d-108">Üçüncü taraf bağımlılıkları ile çerçeveye bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="55f6d-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="55f6d-109">Bağımsız dağıtım</span><span class="sxs-lookup"><span data-stu-id="55f6d-109">Self-contained deployment</span></span>
- <span data-ttu-id="55f6d-110">Üçüncü taraf bağımlılıkları ile bağımsız dağıtım</span><span class="sxs-lookup"><span data-stu-id="55f6d-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="55f6d-111">.NET Core uygulamalarını geliştirmek için Visual Studio'yu kullanma hakkında bilgi için [.NET Core bağımlılıkları ve gereksinimlerine](../install/dependencies.md?pivots=os-windows)bakın.</span><span class="sxs-lookup"><span data-stu-id="55f6d-111">For information on using Visual Studio to develop .NET Core applications, see [.NET Core dependencies and requirements](../install/dependencies.md?pivots=os-windows).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="55f6d-112">Çerçeveye bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="55f6d-112">Framework-dependent deployment</span></span>

<span data-ttu-id="55f6d-113">Üçüncü taraf bağımlılıkları olmayan bir çerçeveye bağımlı dağıtım dağıtmak yalnızca uygulamanın oluşturulmasını, test edilmesini ve yayımlanmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="55f6d-114">C# ile yazılmış basit bir örnek işlemi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-114">A simple example written in C# illustrates the process.</span></span>

1. <span data-ttu-id="55f6d-115">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55f6d-115">Create the project.</span></span>

   <span data-ttu-id="55f6d-116">**Dosya** > **Yeni** > **Proje'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="55f6d-117">Yeni **Proje** iletişim kutusunda, **yüklü** proje türleri bölmesinde dilinizin (C# veya Visual Basic) proje kategorilerini genişletin, **.NET Core'u**seçin ve ardından orta bölmedeki **Konsol Uygulaması (.NET Core)** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="55f6d-118">**Ad** metin kutusuna "FDD" gibi bir proje adı girin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="55f6d-119">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="55f6d-120">Uygulamanın kaynak kodunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-120">Add the application's source code.</span></span>

   <span data-ttu-id="55f6d-121">Program.cs *veya* *Program.vb* dosyasını düzenleyicide açın ve otomatik oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the autogenerated code with the following code.</span></span> <span data-ttu-id="55f6d-122">Kullanıcıdan metin girmesini ister ve kullanıcı tarafından girilen tek tek sözcükleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="55f6d-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="55f6d-123">Giriş metnindeki `\w+` sözcükleri ayırmak için normal ifadeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="55f6d-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="55f6d-124">Uygulamanızın hata ayıklama yapısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55f6d-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="55f6d-125">**Yapı** > **Çözümünü**Seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="55f6d-126">Ayrıca Hata **Debug** > **Ayıklama Başlatma Hata Ayıklama'yı**seçerek uygulamanızın Hata Ayıklama oluşturma sını derleyebilir ve çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="55f6d-127">Uygulamanızı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="55f6d-127">Deploy your app.</span></span>

   <span data-ttu-id="55f6d-128">Programı debugged ve test ettikten sonra, uygulamaile dağıtılacak dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55f6d-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="55f6d-129">Visual Studio'dan yayınlamak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="55f6d-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="55f6d-130">Uygulamanızın Sürüm (Hata Ayıklama yerine) sürümünü oluşturmak için çözüm yapılandırmasını araç çubuğunda **Hata Ayıklama'dan** **Sürüm'e** değiştirin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="55f6d-131">**Solution Explorer'da** projeye (çözüm değil) sağ tıklayın ve **Yayımla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="55f6d-132">**Yayımla** sekmesinde **Yayımla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="55f6d-133">Visual Studio, uygulamanızı oluşturan dosyaları yerel dosya sistemine yazar.</span><span class="sxs-lookup"><span data-stu-id="55f6d-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="55f6d-134">**Yayımla** sekmesi artık tek bir profil, **FolderProfile**gösterir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="55f6d-135">Profilin yapılandırma ayarları sekenin **Özet** bölümünde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="55f6d-136">Elde edilen dosyalar, Windows'da `Publish` ve `publish` projenizin *.\bin\release\netcoreapp2.1* alt dizininin alt dizininde bulunan Unix sistemlerinde adlı bir dizine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="55f6d-137">Uygulamanızın dosyalarıyla birlikte, yayımlama işlemi, uygulamanızla ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar.</span><span class="sxs-lookup"><span data-stu-id="55f6d-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="55f6d-138">Dosya, öncelikle hata ayıklama özel durumları için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="55f6d-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="55f6d-139">Uygulamanızın dosyalarıyla paketlememeyi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="55f6d-140">Ancak, uygulamanızın Sürüm yapısıhatasını ayıklamak istemeniz durumunda bunu kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="55f6d-141">Tüm uygulama dosyalarını istediğiniz şekilde dağıtın.</span><span class="sxs-lookup"><span data-stu-id="55f6d-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="55f6d-142">Örneğin, bunları zip dosyasında paketleyebilir, basit `copy` bir komut kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="55f6d-143">Kurulduktan sonra, kullanıcılar daha sonra komutu `dotnet` kullanarak ve uygulama dosya adını `dotnet fdd.dll`sağlayarak uygulamanızı yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="55f6d-144">Uygulama ikililerine ek olarak, yükleyiciniz paylaşılan çerçeve yükleyicisini de paketlemeli veya uygulama yüklemesinin bir parçası olarak ön koşul olarak bunu kontrol etmelidir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="55f6d-145">Paylaşılan çerçevenin yüklenmesi, makine genelinde olduğundan Yönetici/kök erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="55f6d-146">Üçüncü taraf bağımlılıkları ile çerçeveye bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="55f6d-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="55f6d-147">Bir veya daha fazla üçüncü taraf bağımlılıkla çerçeveye bağımlı bir dağıtım dağıtmak, projenizde herhangi bir bağımlılık olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="55f6d-148">Uygulamanızı oluşturmadan önce aşağıdaki ek adımlar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="55f6d-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="55f6d-149">Projenize bir NuGet paketine başvuru eklemek için **NuGet Paket Yöneticisi'ni** kullanın; ve paket sisteminizde zaten mevcut değilse, yükleyin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="55f6d-150">Paket yöneticisini açmak için, **Araçlar** > **NuGet Paket Yöneticisi** > **Çözüm için Paketleri Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="55f6d-151">Üçüncü taraf bağımlılıklarınızın (örneğin,) `Newtonsoft.Json`sisteminize yüklenmiş olduğunu onaylayın ve değilse bunları yükleyin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-151">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="55f6d-152">**Yüklü** sekme, sisteminizde yüklü olan NuGet paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="55f6d-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="55f6d-153">Burada `Newtonsoft.Json` listelenmemişse, **Gözat** sekmesini seçin ve arama kutusuna "Newtonsoft.Json" girin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="55f6d-154">`Newtonsoft.Json` **Install'u**seçmeden önce sağ bölmede projenizi seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="55f6d-155">Sisteminizde zaten yüklüyse, `Newtonsoft.Json` **Projenizi Çözüm için Paketleri Yönet** sekmesinin sağ bölmesinde seçerek projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="55f6d-156">Üçüncü taraf bağımlılıkları olan çerçeveye bağımlı dağıtım, yalnızca üçüncü taraf bağımlılıkları kadar taşınabilirdir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-156">A framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="55f6d-157">Örneğin, bir üçüncü taraf kitaplığı yalnızca macOS'u destekliyorsa, uygulama Windows sistemlerine taşınabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="55f6d-158">Bu, üçüncü taraf bağımlılığının kendisi yerel koda bağlıysa olur.</span><span class="sxs-lookup"><span data-stu-id="55f6d-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="55f6d-159">Bunun iyi bir örneği [Kestrel sunucusudur,](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) [libuv](https://github.com/libuv/libuv)üzerinde yerli bir bağımlılık gerektirir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="55f6d-160">Bu tür üçüncü taraf bağımlılığı olan bir uygulama için bir FDD oluşturulduğunda, yayımlanan çıktı, yerel bağımlılığın desteklediği (ve NuGet paketinde bulunan) her [Runtime Tanımlayıcısı (RID)](../rid-catalog.md) için bir klasör içerir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a><span data-ttu-id="55f6d-161">Üçüncü taraf bağımlılıkları olmadan bağımsız dağıtım</span><span class="sxs-lookup"><span data-stu-id="55f6d-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="55f6d-162">Üçüncü taraf bağımlılıkları olmadan bağımsız bir dağıtım dağıtmak, projeyi oluşturmayı, *csproj* dosyasını değiştirmeyi, uygulamayı oluşturmayı, test etmeye ve yayımlamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="55f6d-163">C# ile yazılmış basit bir örnek işlemi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="55f6d-164">Tıpkı çerçeveye bağımlı bir dağıtım da olduğu gibi projenizi oluşturarak, kodlayarak ve test ederek başlarsınız:</span><span class="sxs-lookup"><span data-stu-id="55f6d-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="55f6d-165">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55f6d-165">Create the project.</span></span>

   <span data-ttu-id="55f6d-166">**Dosya** > **Yeni** > **Proje'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="55f6d-167">Yeni **Proje** iletişim kutusunda, **yüklü** proje türleri bölmesinde dilinizin (C# veya Visual Basic) proje kategorilerini genişletin, **.NET Core'u**seçin ve ardından orta bölmedeki **Konsol Uygulaması (.NET Core)** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="55f6d-168">**Ad** metin kutusuna "SCD" gibi bir proje adı girin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="55f6d-169">Uygulamanın kaynak kodunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-169">Add the application's source code.</span></span>

   <span data-ttu-id="55f6d-170">Düzenleyicinizdeki *Program.cs* veya *Program.vb* dosyasını açın ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the autogenerated code with the following code.</span></span> <span data-ttu-id="55f6d-171">Kullanıcıdan metin girmesini ister ve kullanıcı tarafından girilen tek tek sözcükleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="55f6d-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="55f6d-172">Giriş metnindeki `\w+` sözcükleri ayırmak için normal ifadeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="55f6d-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="55f6d-173">Genelleştirme değişmez modunu kullanmak isteyip istemediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="55f6d-174">Özellikle uygulamanız Linux'u hedefliyorsa, [küreselleşme değişmez modundan](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)yararlanarak dağıtımınızın toplam boyutunu küçültebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span> <span data-ttu-id="55f6d-175">Genelleştirme değişmez modu, genel olarak farkında olmayan ve biçimlendirme kurallarını, kasa konvansiyonlarını ve [değişken kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)dize karşılaştırma ve sıralama sırasını kullanabilen uygulamalar için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="55f6d-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="55f6d-176">Değişmez modu etkinleştirmek **için, Solution Explorer'da**projenize (çözüm edeğil) sağ tıklayın ve **SCD.csproj'u Edit** veya **SCD.vbproj'u Edit'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="55f6d-177">Ardından dosyaya aşağıdaki vurgulanmış satırları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="55f6d-177">Then add the following highlighted lines to the file:</span></span>

   [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj?highlight=6-8)]

1. <span data-ttu-id="55f6d-178">Uygulamanızın hata ayıklama yapısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55f6d-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="55f6d-179">**Yapı** > **Çözümünü**Seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="55f6d-180">Ayrıca Hata **Debug** > **Ayıklama Başlatma Hata Ayıklama'yı**seçerek uygulamanızın Hata Ayıklama oluşturma sını derleyebilir ve çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="55f6d-181">Bu hata ayıklama adımı, ana bilgisayar platformunuzda çalışırken uygulamanızla ilgili sorunları belirlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="55f6d-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="55f6d-182">Yine de hedef platformlarınızın her birinde test etmek zorunda kalacak.</span><span class="sxs-lookup"><span data-stu-id="55f6d-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="55f6d-183">Genelleştirme değişmez modunu etkinleştirdiyseniz, kültüre duyarlı verilerin yokluğunun uygulamanız için uygun olup olmadığını özellikle test edin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="55f6d-184">Hata ayıklamayı tamamladıktan sonra, bağımsız dağıtımınızı yayımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="55f6d-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[<span data-ttu-id="55f6d-185">Visual Studio 15.6 ve önceki</span><span class="sxs-lookup"><span data-stu-id="55f6d-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="55f6d-186">Programı debugged ve test ettikten sonra, hedeflenenekadar her platform için uygulamanızla dağıtılacak dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55f6d-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="55f6d-187">Uygulamanızı Visual Studio'dan yayınlamak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="55f6d-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="55f6d-188">Uygulamanızın hedefalacağı platformları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="55f6d-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="55f6d-189">**Solution Explorer'da** projenize (çözüm değil) sağ tıklayın ve **SCD.csproj'u Edit'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="55f6d-190">*csproj* `<PropertyGroup>` dosyanızın uygulamahedeflerinizi hedefleyen platformları tanımlayan bölümünde bir `<RuntimeIdentifiers>` etiket oluşturun ve hedeflediğiniz her platformun çalışma zamanı tanımlayıcısını (RID) belirtin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="55f6d-191">Ayrıca RID'leri ayırmak için bir yarı nokta eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-191">You also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="55f6d-192">Çalışma zamanı tanımlayıcılarının listesi için [Runtime Tanımlayıcı kataloğuna](../rid-catalog.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="55f6d-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="55f6d-193">Örneğin, aşağıdaki örnek, uygulamanın 64 bit Windows 10 işletim sistemleri ve 64 bit OS X Sürüm 10.11 işletim sistemi üzerinde çalıştığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="55f6d-194">Öğe `<RuntimeIdentifiers>` `<PropertyGroup>` *csproj* dosyanızda bulunan herhangi bir içine gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-194">The `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="55f6d-195">Tam bir örnek *csproj* dosyası daha sonra bu bölümde görünür.</span><span class="sxs-lookup"><span data-stu-id="55f6d-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="55f6d-196">Uygulamanızı yayınlayın.</span><span class="sxs-lookup"><span data-stu-id="55f6d-196">Publish your app.</span></span>

   <span data-ttu-id="55f6d-197">Programı debugged ve test ettikten sonra, hedeflenenekadar her platform için uygulamanızla dağıtılacak dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55f6d-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="55f6d-198">Uygulamanızı Visual Studio'dan yayınlamak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="55f6d-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="55f6d-199">Uygulamanızın Sürüm (Hata Ayıklama yerine) sürümünü oluşturmak için çözüm yapılandırmasını araç çubuğunda **Hata Ayıklama'dan** **Sürüm'e** değiştirin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="55f6d-200">**Solution Explorer'da** projeye (çözüm değil) sağ tıklayın ve **Yayımla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="55f6d-201">**Yayımla** sekmesinde **Yayımla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="55f6d-202">Visual Studio, uygulamanızı oluşturan dosyaları yerel dosya sistemine yazar.</span><span class="sxs-lookup"><span data-stu-id="55f6d-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="55f6d-203">**Yayımla** sekmesi artık tek bir profil, **FolderProfile**gösterir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="55f6d-204">Profilin yapılandırma ayarları sekmenin **Özet** bölümünde gösterilir. **Hedef Çalışma Zamanı** hangi çalışma zamanının yayımlandığını tanımlar ve Hedef **Konum,** bağımsız dağıtım dosyalarının nerede yazıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="55f6d-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="55f6d-205">Visual Studio varsayılan olarak tüm yayımlanmış dosyaları tek bir dizine yazar.</span><span class="sxs-lookup"><span data-stu-id="55f6d-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="55f6d-206">Kolaylık sağlamak için, her hedef çalışma zamanı için ayrı profiller oluşturmak ve yayımlanmış dosyaları platforma özgü bir dizine yerleştirmek en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="55f6d-207">Bu, her hedef platform için ayrı bir yayımlama profili oluşturmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="55f6d-208">Yani şimdi aşağıdakileri yaparak her platform için uygulama yeniden:</span><span class="sxs-lookup"><span data-stu-id="55f6d-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="55f6d-209">**Yayımla** iletişim kutusunda **yeni profil oluştur'u** seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="55f6d-210">**Yayımlama hedef** iletişim kutusunda, klasör konumunu *bin\Release\PublishOutput\win10-x64*olarak **seçin'** i değiştirin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="55f6d-211">**Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-211">Select **OK**.</span></span>

         1. <span data-ttu-id="55f6d-212">Profiller listesindeki yeni profili **(FolderProfile1)** seçin ve **Hedef Çalışma Zamanı'nın** . `win10-x64`</span><span class="sxs-lookup"><span data-stu-id="55f6d-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="55f6d-213">Değilse, **Ayarlar'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="55f6d-214">Profil **Ayarları** iletişim kutusunda, **Hedef Çalışma** `win10-x64` Süresini değiştirin ve **Kaydet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="55f6d-215">Aksi takdirde **Cancel**İptal et'i seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="55f6d-216">Uygulamanızı 64 bit Windows 10 platformları için yayımlamak için **Yayımla'yı** seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="55f6d-217">`osx.10.11-x64` Platform için bir profil oluşturmak için önceki adımları yeniden izleyin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="55f6d-218">**Hedef Konum** *bin\Release\PublishOutput\osx.10.11-x64*ve **Hedef Çalışma** `osx.10.11-x64`Zamanı .</span><span class="sxs-lookup"><span data-stu-id="55f6d-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="55f6d-219">Visual Studio'nun bu profile atadığı ad **FolderProfile2'dir.**</span><span class="sxs-lookup"><span data-stu-id="55f6d-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="55f6d-220">Her hedef konum, uygulamanızı başlatmak için gereken dosyaların (hem uygulama dosyalarınız hem de tüm .NET Core dosyaları) tüm dosya kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-220">Each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="55f6d-221">Uygulamanızın dosyalarıyla birlikte, yayımlama işlemi, uygulamanızla ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar.</span><span class="sxs-lookup"><span data-stu-id="55f6d-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="55f6d-222">Dosya, öncelikle hata ayıklama özel durumları için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="55f6d-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="55f6d-223">Uygulamanızın dosyalarıyla paketlememeyi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="55f6d-224">Ancak, uygulamanızın Sürüm yapısıhatasını ayıklamak istemeniz durumunda bunu kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="55f6d-225">Yayımlanmış dosyaları istediğiniz şekilde dağıtın.</span><span class="sxs-lookup"><span data-stu-id="55f6d-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="55f6d-226">Örneğin, bunları zip dosyasında paketleyebilir, basit `copy` bir komut kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="55f6d-227">Aşağıdaki bu proje için tam *csproj* dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="55f6d-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[<span data-ttu-id="55f6d-228">Visual Studio 15.7 ve sonrası</span><span class="sxs-lookup"><span data-stu-id="55f6d-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="55f6d-229">Programı debugged ve test ettikten sonra, hedeflenenekadar her platform için uygulamanızla dağıtılacak dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55f6d-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="55f6d-230">Bu, her hedef platform için ayrı bir profil oluşturmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="55f6d-231">Uygulamanızın hedeflenen her platform için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="55f6d-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="55f6d-232">Hedef platformunuz için bir profil oluşturun.</span><span class="sxs-lookup"><span data-stu-id="55f6d-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="55f6d-233">Oluşturduğunuz ilk profil buysa, **Solution Explorer'daki** projeye (çözüm değil) sağ tıklayın ve **Yayımla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="55f6d-234">Zaten bir profil oluşturduysanız, zaten açık değilse **Yayımla** iletişim kutusunu açmak için projeye sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="55f6d-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="55f6d-235">Ardından **Yeni Profil'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="55f6d-236">Hedef **Yayımla** iletişim kutusunu seç açılır.</span><span class="sxs-lookup"><span data-stu-id="55f6d-236">The **Pick a Publish Target** dialog box opens.</span></span>

1. <span data-ttu-id="55f6d-237">Visual Studio'nun başvurunuzu yayınladığı konumu seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="55f6d-238">Yalnızca tek bir platformda yayınlıyorsanız, klasör metin kutusu **seç'te** varsayılan değeri kabul edebilirsiniz; bu, uygulamanızın \* \<>\bin\Release\netcoreapp2.1\publish\* dizinine uygulamanızın çerçeveye bağlı dağıtımını yayımlar.</span><span class="sxs-lookup"><span data-stu-id="55f6d-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework-dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish* directory.</span></span>

   <span data-ttu-id="55f6d-239">Birden fazla platformda yayımlıyorsanız, hedef platformu tanımlayan bir dize ekine getirin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="55f6d-240">Örneğin, dosya yoluna "linux" dizesini eklerseniz, Visual Studio uygulamanızın çerçeveye bağlı dağıtımını \* \<proje dizinine>\bin\Release\netcoreapp2.1\publish\linux\* dizinine yayınlar.</span><span class="sxs-lookup"><span data-stu-id="55f6d-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework-dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="55f6d-241">**Yayımla** düğmesinin yanındaki açılır liste simgesini seçerek ve Profil Oluştur'u seçerek **profili oluşturun.**</span><span class="sxs-lookup"><span data-stu-id="55f6d-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="55f6d-242">Ardından profili oluşturmak için **Profil Oluştur** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="55f6d-243">Bağımsız bir dağıtım yayınladığınızı belirtin ve uygulamanızın hedefalacağı bir platform tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="55f6d-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="55f6d-244">**Yayımla** iletişim kutusunda, **Profil Ayarları** iletişim kutusunu açmak için **Yapıla** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="55f6d-245">**Dağıtım Modu** liste kutusunda Kendi **Kendine Yeten'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="55f6d-246">Hedef **Çalışma Zamanı** liste kutusunda, uygulamanızın hedeflenedığı platformlardan birini seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="55f6d-247">Değişikliklerinizi kabul etmek ve iletişim kutusunu kapatmak için **Kaydet'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="55f6d-248">Profilinize isim verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-248">Name your profile.</span></span>

   1. <span data-ttu-id="55f6d-249">Profilinize isim vermek için **Eylemler** > **Profilini Yeniden Adlandır'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="55f6d-250">Profilinize hedef platformu tanımlayan bir ad atayın ve ardından \**Kaydet'i*seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="55f6d-251">Uygulamanızın hedeflenebilen ek hedef platformlarını tanımlamak için bu adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="55f6d-252">Profillerinizi yapılandırıldınız ve artık uygulamanızı yayınlamaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="55f6d-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="55f6d-253">Bunu yapmak için:</span><span class="sxs-lookup"><span data-stu-id="55f6d-253">To do this:</span></span>

   1. <span data-ttu-id="55f6d-254">**Yayımla** penceresi şu anda açık değilse, **Solution Explorer'da** projeye (çözüm değil) sağ tıklayın ve **Yayımla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="55f6d-255">Yayınlamak istediğiniz profili seçin, ardından **Yayımla'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="55f6d-256">Yayınlanacak her profil için bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="55f6d-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="55f6d-257">Her hedef konum (örneğimiz söz konusu olduğunda, bin\release\netcoreapp2.1\publish\\profil*adı,* uygulamanızı başlatmak için gereken dosyaların tamamını (hem uygulama dosyalarınız hem de tüm .NET Core dosyaları) içerir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-257">Each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="55f6d-258">Uygulamanızın dosyalarıyla birlikte, yayımlama işlemi, uygulamanızla ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar.</span><span class="sxs-lookup"><span data-stu-id="55f6d-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="55f6d-259">Dosya, öncelikle hata ayıklama özel durumları için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="55f6d-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="55f6d-260">Uygulamanızın dosyalarıyla paketlememeyi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="55f6d-261">Ancak, uygulamanızın Sürüm yapısıhatasını ayıklamak istemeniz durumunda bunu kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="55f6d-262">Yayımlanmış dosyaları istediğiniz şekilde dağıtın.</span><span class="sxs-lookup"><span data-stu-id="55f6d-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="55f6d-263">Örneğin, bunları zip dosyasında paketleyebilir, basit `copy` bir komut kullanabilir veya istediğiniz herhangi bir yükleme paketiyle dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="55f6d-264">Aşağıdaki bu proje için tam *csproj* dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="55f6d-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="55f6d-265">Buna ek olarak, Visual Studio hedeflediğiniz her platform için ayrı bir yayımlama profili (.pubxml)\*oluşturur.</span><span class="sxs-lookup"><span data-stu-id="55f6d-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="55f6d-266">Örneğin, linux profilimiz (linux.pubxml) için dosya aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="55f6d-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

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

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="55f6d-267">Üçüncü taraf bağımlılıkları ile bağımsız dağıtım</span><span class="sxs-lookup"><span data-stu-id="55f6d-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="55f6d-268">Bir veya daha fazla üçüncü taraf bağımlılıkla bağımsız bir dağıtım dağıtmak, bağımlılıkların eklenmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="55f6d-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="55f6d-269">Uygulamanızı oluşturmadan önce aşağıdaki ek adımlar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="55f6d-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="55f6d-270">Projenize bir NuGet paketine başvuru eklemek için **NuGet Paket Yöneticisi'ni** kullanın; ve paket sisteminizde zaten mevcut değilse, yükleyin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="55f6d-271">Paket yöneticisini açmak için, **Araçlar** > **NuGet Paket Yöneticisi** > **Çözüm için Paketleri Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="55f6d-272">Üçüncü taraf bağımlılıklarınızın (örneğin,) `Newtonsoft.Json`sisteminize yüklenmiş olduğunu onaylayın ve değilse bunları yükleyin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-272">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="55f6d-273">**Yüklü** sekme, sisteminizde yüklü olan NuGet paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="55f6d-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="55f6d-274">Burada `Newtonsoft.Json` listelenmemişse, **Gözat** sekmesini seçin ve arama kutusuna "Newtonsoft.Json" girin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="55f6d-275">`Newtonsoft.Json` **Install'u**seçmeden önce sağ bölmede projenizi seçin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="55f6d-276">Sisteminizde zaten yüklüyse, `Newtonsoft.Json` **Projenizi Çözüm için Paketleri Yönet** sekmesinin sağ bölmesinde seçerek projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="55f6d-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="55f6d-277">Bu proje için *csproj* dosyasının tamamı aşağıda veda edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="55f6d-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earlier"></a>[<span data-ttu-id="55f6d-278">Visual Studio 15.6 ve önceki</span><span class="sxs-lookup"><span data-stu-id="55f6d-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

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

# <a name="visual-studio-157-and-later"></a>[<span data-ttu-id="55f6d-279">Visual Studio 15.7 ve sonrası</span><span class="sxs-lookup"><span data-stu-id="55f6d-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

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

<span data-ttu-id="55f6d-280">Uygulamanızı dağıttığınızda, uygulamanızda kullanılan tüm üçüncü taraf bağımlılıkları da uygulama dosyalarınızda bulunur.</span><span class="sxs-lookup"><span data-stu-id="55f6d-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="55f6d-281">Uygulamanın çalıştırıldığı sistemde üçüncü taraf kitaplıkları gerekmez.</span><span class="sxs-lookup"><span data-stu-id="55f6d-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="55f6d-282">Yalnızca, üçüncü taraf kitaplığı yla birlikte bağımsız bir dağıtımı bu kitaplık tarafından desteklenen platformlara dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-282">You can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="55f6d-283">Bu, daha önce yüklenmediği sürece yerel bağımlılıkların hedef platformda bulunamayacağı, çerçeveye bağımlı dağıtımınızda yerel bağımlılıklarla üçüncü taraf bağımlılıklara sahip olmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="55f6d-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="55f6d-284">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55f6d-284">See also</span></span>

- [<span data-ttu-id="55f6d-285">.NET Çekirdek Uygulama Dağıtımı</span><span class="sxs-lookup"><span data-stu-id="55f6d-285">.NET Core Application Deployment</span></span>](index.md)
- [<span data-ttu-id="55f6d-286">.NET Core Runtime Tanımlayıcı (RID) kataloğu</span><span class="sxs-lookup"><span data-stu-id="55f6d-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
