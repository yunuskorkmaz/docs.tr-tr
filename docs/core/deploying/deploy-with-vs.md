---
title: Visual Studio ile .NET core uygulama dağıtımı
description: Visual Studio ile .NET Core uygulama dağıtımı öğrenin
author: rpetrusha
ms.author: ronpet
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.openlocfilehash: 62cfef08a8319981891c713c08c34eba5ab54b6f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227746"
---
# <a name="deploying-net-core-apps-with-visual-studio"></a><span data-ttu-id="b5c9d-103">Dağıtımı .NET Core uygulamaları Visual Studio ile</span><span class="sxs-lookup"><span data-stu-id="b5c9d-103">Deploying .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="b5c9d-104">Dağıtabileceğiniz bir .NET Core uygulaması ya da farklı bir *framework bağımlı dağıtım*, uygulama ikili dosyalarını içerir, ancak hedef sistem üzerinde veya olarak .NET Core varlığını bağımlı bir *müstakil Dağıtım*, hem uygulama hem de .NET Core ikili dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="b5c9d-105">.NET Core uygulama dağıtımı genel bakış için bkz. [.NET Core uygulaması dağıtımını](index.md).</span><span class="sxs-lookup"><span data-stu-id="b5c9d-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="b5c9d-106">Aşağıdaki bölümlerde, aşağıdaki türde dağıtımları oluşturmak için Microsoft Visual Studio kullanmayı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="b5c9d-107">Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="b5c9d-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="b5c9d-108">Framework bağımlı dağıtım üçüncü taraf bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="b5c9d-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="b5c9d-109">Kendi içinde dağıtım</span><span class="sxs-lookup"><span data-stu-id="b5c9d-109">Self-contained deployment</span></span>
- <span data-ttu-id="b5c9d-110">Üçüncü taraf bağımlılıkları kendi içinde dağıtım</span><span class="sxs-lookup"><span data-stu-id="b5c9d-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="b5c9d-111">.NET Core uygulamaları geliştirmek için Visual Studio'yu kullanma hakkında daha fazla bilgi için bkz: [Windows üzerinde .NET Core önkoşulları](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).</span><span class="sxs-lookup"><span data-stu-id="b5c9d-111">For information on using Visual Studio to develop .NET Core applications, see [Prerequisites for .NET Core on Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="b5c9d-112">Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="b5c9d-112">Framework-dependent deployment</span></span>

<span data-ttu-id="b5c9d-113">Herhangi bir üçüncü taraf bağımlılıkları olan bir framework bağımlı dağıtımının oluşturmaya, sınamaya ve uygulama yayımlama yalnızca içerir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="b5c9d-114">C# dilinde yazılmış basit bir örnek işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-114">A simple example written in C# illustrates the process.</span></span>  

1. <span data-ttu-id="b5c9d-115">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-115">Create the project.</span></span>

   <span data-ttu-id="b5c9d-116">Seçin **dosya** > **yeni** > **proje**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="b5c9d-117">İçinde **yeni proje** iletişim kutusunda, dilinizin (C# veya Visual Basic) proje kategorilerde genişletin **yüklü** öğesini Proje Türleri bölmesinde **.NET Core**ve ardından seçin **Konsol uygulaması (.NET Core)** Orta bölmedeki şablonu.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="b5c9d-118">"FDD" gibi bir proje adı girin **adı** metin kutusu.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="b5c9d-119">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="b5c9d-120">Uygulamanın kaynak kodunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-120">Add the application's source code.</span></span>

   <span data-ttu-id="b5c9d-121">Açık *Program.cs* veya *Program.vb* Düzenleyicisi'nde dosya ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="b5c9d-122">Kullanıcının metin girmesini ister ve kullanıcı tarafından girilen kelimeler görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="b5c9d-123">Normal ifade kullanan `\w+` giriş metnindeki sözcükleri ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="b5c9d-124">Uygulamanızı hata ayıklama yapısını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="b5c9d-125">Seçin **derleme** > **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="b5c9d-126">Ayrıca derlemek ve seçerek uygulamanızı hata ayıklama yapısını çalıştırmak **hata ayıklama** > **hata ayıklamayı Başlat**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="b5c9d-127">Uygulamanızı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-127">Deploy your app.</span></span>

   <span data-ttu-id="b5c9d-128">Hata ayıklama ve test programı sonra uygulamanızla birlikte dağıtılacak dosyalar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="b5c9d-129">Visual Studio'dan yayımlamak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="b5c9d-130">Çözüm yapılandırmasını değiştirme **hata ayıklama** için **yayın** uygulamanızın derleme bir sürüm (yerine bir hata ayıklama) sürümü için araç çubuğundaki.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="b5c9d-131">Projede (çözümü değil) sağ tıklatın **Çözüm Gezgini** seçip **Yayımla**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="b5c9d-132">İçinde **Yayımla** sekmesinde **Yayımla**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="b5c9d-133">Visual Studio, uygulamanızın yerel dosya sistemine oluşturan dosyaların yazar.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="b5c9d-134">**Yayımla** sekmesi, artık tek bir profil gösterir **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="b5c9d-135">Profilin yapılandırma ayarları gösterilir **özeti** sekmesinin bölümünde.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="b5c9d-136">Ortaya çıkan dosyalar adlı bir dizinde yerleştirilir `Publish` Windows üzerinde ve `publish` bir proje alt dizinindeki UNIX sistemlerde *.\bin\release\netcoreapp2.1* alt.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="b5c9d-137">Uygulamanızın dosyaları ile birlikte uygulamanızı hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayımlama işlemi yayar.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="b5c9d-138">Dosya, öncelikle bir özel durum hata ayıklama için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="b5c9d-139">Bu paket, uygulamanızın dosyaları ile değil seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="b5c9d-140">Uygulamanızı yayın derlemesinin hatalarını ayıklamak istediğiniz olay, ancak kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="b5c9d-141">İstediğiniz gibi uygulama dosyalarını tam kümesini dağıtın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="b5c9d-142">Örneğin, bunları bir Zip dosyasına paketleyin, basit bir kullanın `copy` komutunu ya da bunları seçtiğiniz herhangi bir yükleme paketi ile birlikte dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="b5c9d-143">Yüklendikten sonra kullanıcılar daha sonra uygulamanızı kullanarak yürütebilirsiniz `dotnet` komut ve uygulama dosya adı gibi sağlama `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="b5c9d-144">Uygulama ikili dosyalarını ek olarak, yükleyicinizi de paylaşılan framework yükleyici paket veya uygulama yüklemesinin bir parçası olarak bir önkoşul olarak için kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="b5c9d-145">Makine genelinde olduğundan paylaşılan framework'ün yüklemesini yönetici/kök erişim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="b5c9d-146">Framework bağımlı dağıtım üçüncü taraf bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="b5c9d-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="b5c9d-147">Bir veya daha fazla üçüncü taraf bağımlılıkları olan bir framework bağımlı dağıtımının bağımlılıkları projenize kullanılabilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="b5c9d-148">Uygulamanızı oluşturmadan önce aşağıdaki ek adımlar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="b5c9d-149">Kullanım **NuGet Paket Yöneticisi** projenize; NuGet paketine başvuru eklemek ve paket zaten sisteminizde kullanılabilir değilse, yükleyin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="b5c9d-150">Paket Yöneticisi'ni açmak için seçmeniz **Araçları** > **NuGet Paket Yöneticisi** > **çözüm için NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="b5c9d-151">Onaylayın `Newtonsoft.Json` sisteminizde yüklü olduğundan ve yüklü değilse, yükleyin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-151">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="b5c9d-152">**Yüklü** sekmesi, sisteminizde yüklü olan NuGet paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="b5c9d-153">Varsa `Newtonsoft.Json` listelenmiyorsa, seçin **Gözat** sekmesinde ve arama kutusuna "Newtonsoft.Json".</span><span class="sxs-lookup"><span data-stu-id="b5c9d-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="b5c9d-154">Seçin `Newtonsoft.Json` seçip, sağ bölmede, projenizi seçmeden önce **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="b5c9d-155">Varsa `Newtonsoft.Json` olduğundan, sisteminizde yüklü, projenize sağ bölmede, proje seçerek eklemek **çözüm için paketlerini Yönet** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of hte **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="b5c9d-156">Üçüncü taraf bağımlılıkları olan bir framework bağımlı dağıtım yalnızca üçüncü taraf bağımlılıklarını olarak taşınabilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-156">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="b5c9d-157">Örneğin, bir üçüncü taraf kitaplığı yalnızca macOS destekliyorsa, uygulamayı Windows sistemleri için taşınabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="b5c9d-158">Bu, üçüncü taraf bağımlılığı yerel kodu bağımlı olması durumunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="b5c9d-159">Bunun iyi bir örnektir [Kestrel sunucu](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), üzerinde yerel bir bağımlılık gerektiren [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="b5c9d-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="b5c9d-160">Bu tür bir üçüncü taraf bağımlılığı bir uygulama için bir FDD oluşturulduğunda, yayımlanan çıktısını bir klasöre her biri için içeren [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) yerel bağımlılık destekleyen (ve kendi NuGet paketini var).</span><span class="sxs-lookup"><span data-stu-id="b5c9d-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="b5c9d-161">Üçüncü taraf bağımlılıkları olmadan kendi içinde dağıtım</span><span class="sxs-lookup"><span data-stu-id="b5c9d-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="b5c9d-162">Üçüncü taraf bağımlılıkları kendi içinde bir dağıtımla dağıtma içerir proje oluşturma değiştirme *csproj* oluşturmaya, sınamaya ve uygulama yayımlama dosyası.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="b5c9d-163">C# dilinde yazılmış basit bir örnek işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="b5c9d-164">Oluşturma, kodlama ve framework bağımlı dağıtım yaptığınız gibi projenizi sınamayı başlamadan:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="b5c9d-165">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-165">Create the project.</span></span>

   <span data-ttu-id="b5c9d-166">Seçin **dosya** > **yeni** > **proje**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="b5c9d-167">İçinde **yeni proje** iletişim kutusunda, dilinizin (C# veya Visual Basic) proje kategorilerde genişletin **yüklü** öğesini Proje Türleri bölmesinde **.NET Core**ve ardından seçin **Konsol uygulaması (.NET Core)** Orta bölmedeki şablonu.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="b5c9d-168">"SCD" gibi bir proje adı girin **adı** metin kutusu ve select **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="b5c9d-169">Uygulamanın kaynak kodunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-169">Add the application's source code.</span></span>

   <span data-ttu-id="b5c9d-170">Açık *Program.cs* veya dosya Düzenleyicisi'nde ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-170">Open the *Program.cs* or file in your editor, and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="b5c9d-171">Kullanıcının metin girmesini ister ve kullanıcı tarafından girilen kelimeler görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="b5c9d-172">Normal ifade kullanan `\w+` giriş metnindeki sözcükleri ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="b5c9d-173">Genelleştirme sabit modu kullanmak isteyip istemediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="b5c9d-174">Uygulamanızı Linux hedefliyorsa, özellikle, avantajlarından yararlanarak dağıtımınızın toplam boyutunu azaltabilirsiniz [Genelleştirme sabit modu](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="b5c9d-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="b5c9d-175">Genelleştirme sabit modu, genel olarak duyarlı değildir ve biçimlendirme kuralları, büyük/küçük harf kuralları ve dize karşılaştırma ve sıralama düzenini kullanabilen uygulamalar için kullanışlıdır [sabit kültür](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="b5c9d-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="b5c9d-176">Sabit modunu etkinleştirmek için projenize (çözümü değil) sağ **Çözüm Gezgini**seçip **Düzenle SCD.csproj** veya **Düzenle SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="b5c9d-177">Ardından aşağıdaki vurgulanan satırları dosyaya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-177">Then add the following highlighted lines to the file:</span></span>

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. <span data-ttu-id="b5c9d-178">Uygulamanızı hata ayıklama yapısını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="b5c9d-179">Seçin **derleme** > **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="b5c9d-180">Ayrıca derlemek ve seçerek uygulamanızı hata ayıklama yapısını çalıştırmak **hata ayıklama** > **hata ayıklamayı Başlat**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="b5c9d-181">Hata ayıklama Bu adım, ana bilgisayar platformu üzerinde çalışırken, uygulamanızdaki sorunları tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="b5c9d-182">Her hedef platformlar üzerinde test gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="b5c9d-183">Genelleştirme sabit modu etkinleştirdiyseniz, kültüre duyarlı veri olmaması, uygulamanız için uygun olup olmadığını sınamak özellikle emin olun.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="b5c9d-184">Hata ayıklama bitirdiğinizde, kendi içindeki dağıtımınızı yayımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="b5c9d-185">Visual Studio 15.6 ve önceki sürümleri</span><span class="sxs-lookup"><span data-stu-id="b5c9d-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="b5c9d-186">Hata ayıklama ve test programı sonra her platform için uygulamanızdan bu hedefler dağıtılacak dosyaların oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="b5c9d-187">Uygulamanızı Visual Studio'dan yayımlamak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="b5c9d-188">Uygulamanızı hedefleyen platformlar tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="b5c9d-189">Projenizde (çözümü değil) sağ tıklatın **Çözüm Gezgini** seçip **Düzenle SCD.csproj**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="b5c9d-190">Oluşturma bir `<RuntimeIdentifiers>` içindeki `<PropertyGroup>` bölümünü, *csproj* platformları kullanarak uygulamanızın hedeflediği tanımlayan dosyası ve hedeflediğiniz her platform için çalışma zamanı tanımlayıcı (RID) belirtin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="b5c9d-191">Aynı zamanda RID ayırmak için noktalı virgül eklemeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-191">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="b5c9d-192">Bkz: [çalışma zamanı tanımlayıcı Kataloğu](../rid-catalog.md) çalışma zamanı tanımlayıcılarının listesi.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="b5c9d-193">Örneğin, aşağıdaki örnekte uygulama 64-bit Windows 10 işletim sistemleri ve OS X sürüm 10.11 64-bit işletim sistemi üzerinde çalıştırıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="b5c9d-194">Unutmayın `<RuntimeIdentifiers>` öğesi hiçbir gidebilir `<PropertyGroup>` sahip olduğunuz, *csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-194">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="b5c9d-195">Eksiksiz bir örnek *csproj* dosyası bu bölümde daha sonra görünür.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="b5c9d-196">Uygulamanızı yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-196">Publish your app.</span></span>

   <span data-ttu-id="b5c9d-197">Hata ayıklama ve test programı sonra her platform için uygulamanızdan bu hedefler dağıtılacak dosyaların oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="b5c9d-198">Uygulamanızı Visual Studio'dan yayımlamak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="b5c9d-199">Çözüm yapılandırmasını değiştirme **hata ayıklama** için **yayın** uygulamanızın derleme bir sürüm (yerine bir hata ayıklama) sürümü için araç çubuğundaki.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="b5c9d-200">Projede (çözümü değil) sağ tıklatın **Çözüm Gezgini** seçip **Yayımla**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="b5c9d-201">İçinde **Yayımla** sekmesinde **Yayımla**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="b5c9d-202">Visual Studio, uygulamanızın yerel dosya sistemine oluşturan dosyaların yazar.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="b5c9d-203">**Yayımla** sekmesi, artık tek bir profil gösterir **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="b5c9d-204">Profilin yapılandırma ayarları gösterilir **özeti** sekmesinin bölümünde. **Hedef çalışma zamanı** hangi çalışma zamanı yayımlanan tanımlar ve **hedef konum** müstakil dağıtımı için dosyaların nerede yazılmış tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="b5c9d-205">Visual Studio varsayılan olarak, tüm dosyaları için tek bir dizin yayımlanan yazar.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="b5c9d-206">Kolaylık olması için her bir hedef çalışma zamanı için ayrı profiller oluşturun ve yayımlanan dosyaları bir platforma özgü dizinde yerleştirmek için en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="b5c9d-207">Bu, her hedef platformu için ayrı bir yayımlama profili oluşturmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="b5c9d-208">Aşağıdakileri yaparak her platform için uygulama şimdi yeniden oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="b5c9d-209">Seçin **yeni profil oluşturma** içinde **Yayımla** iletişim.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="b5c9d-210">İçinde **yayımlama hedefi seçin** iletişim kutusunda değişiklik **bir klasör seçin** konumuna *bin\Release\PublishOutput\win10 x64*.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="b5c9d-211">Seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-211">Select **OK**.</span></span>

         1. <span data-ttu-id="b5c9d-212">Yeni profili seçin (**FolderProfile1**) profilleri listesinde olduğundan emin olun **hedef çalışma zamanı** olduğu `win10-x64`.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="b5c9d-213">Aksi takdirde seçin **ayarları**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="b5c9d-214">İçinde **profil ayarları** iletişim kutusunda değişiklik **hedef çalışma zamanı** için `win10-x64` seçip **Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="b5c9d-215">Aksi takdirde seçin **iptal**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="b5c9d-216">Seçin **yayımlama** için 64 bit Windows 10 platformlarını kullanarak uygulamanızı yayımlama.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="b5c9d-217">Bir profili yeniden oluşturmak için önceki adımları `osx.10.11-x64` platform.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="b5c9d-218">**Hedef konum** olduğu *bin\Release\PublishOutput\osx.10.11-x64*ve **hedef çalışma zamanı** olduğu `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="b5c9d-219">Visual Studio bu profile atar adı **FolderProfile2**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="b5c9d-220">Her bir hedef konum uygulamanızı başlatmak için gerekli dosyaları (uygulama dosyalarınızı ve tüm .NET Core dosyaları) tam kümesini içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-220">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="b5c9d-221">Uygulamanızın dosyaları ile birlikte uygulamanızı hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayımlama işlemi yayar.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="b5c9d-222">Dosya, öncelikle bir özel durum hata ayıklama için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="b5c9d-223">Bu paket, uygulamanızın dosyaları ile değil seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="b5c9d-224">Uygulamanızı yayın derlemesinin hatalarını ayıklamak istediğiniz olay, ancak kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="b5c9d-225">Yayımlanan dosyaları istediğiniz herhangi bir şekilde dağıtın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="b5c9d-226">Örneğin, bunları bir Zip dosyasına paketleyin, basit bir kullanın `copy` komutunu ya da bunları seçtiğiniz herhangi bir yükleme paketi ile birlikte dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="b5c9d-227">Aşağıdaki tamamlandıktan *csproj* bu proje için dosya.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="b5c9d-228">Visual Studio 15.7 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="b5c9d-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="b5c9d-229">Hata ayıklama ve test programı sonra her platform için uygulamanızdan bu hedefler dağıtılacak dosyaların oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="b5c9d-230">Bu, her hedef platformu için ayrı bir profil oluşturmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="b5c9d-231">Her platform uygulama hedeflerinizi aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="b5c9d-232">Hedef platform için bir profil oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="b5c9d-233">Bu oluşturduğunuz ilk profil ise, projede (çözümü değil) sağ tıklatın **Çözüm Gezgini** seçip **Yayımla**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="b5c9d-234">Bir profil zaten oluşturduysanız, açmak için projeye sağ tıklayın **Yayımla** zaten açık değilse iletişim.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="b5c9d-235">Ardından **yeni profili**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="b5c9d-236">**Bir yayımlama hedefi seçin** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-236">The **Pick a Publish Target** dialog box opens.</span></span>
  
1. <span data-ttu-id="b5c9d-237">Visual Studio, uygulamanızın yayımladığı konumu seçin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="b5c9d-238">Yalnızca tek bir platformda yayınlıyorsanız, varsayılan değeri kabul edebilir **bir klasör seçin** metin kutusu; bunun için uygulamanızın framework bağımlı dağıtım yayımlar \*\<proje dizini > \ bin\Release\netcoreapp2.1\publish\* dizin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework dependent deployment of your application to the \*\<project-directory>\bin\Release\netcoreapp2.1\publish\* directory.</span></span>

   <span data-ttu-id="b5c9d-239">Birden fazla platforma yayınlıyorsanız, hedef platform tanımlayan bir dize ekler.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="b5c9d-240">Örneğin, "linux" dize dosya yolu ekleme, Visual Studio için uygulamanızın framework bağımlı dağıtım yayımlar  *\<proje dizini > \bin\Release\netcoreapp2.1\publish\linux*dizin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="b5c9d-241">Yanındaki aşağı açılan liste simgesini seçerek profili oluşturmak **Yayımla** düğmesine tıklayıp **profili oluştur**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="b5c9d-242">Ardından **profili oluştur** profili oluşturma düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="b5c9d-243">Kendi içinde bir dağıtım yayımladığınız belirtmek ve uygulamanızı hedefleyen bir platform tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="b5c9d-244">İçinde **Yayımla** iletişim kutusunda **yapılandırma** açmak için bağlantıyı **profil ayarları** iletişim.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="b5c9d-245">Seçin **müstakil** içinde **dağıtım modu** liste kutusu.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="b5c9d-246">İçinde **hedef çalışma zamanı** liste kutusunda, bir platform seçin, uygulama hedeflerinizi.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="b5c9d-247">Seçin **Kaydet** yaptığınız değişiklikleri kabul etmek ve iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="b5c9d-248">Profilinizi adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-248">Name your profile.</span></span>

   1. <span data-ttu-id="b5c9d-249">Seçin **eylemleri** > **profili Yeniden Adlandır** profilinizi adlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="b5c9d-250">Profilinizi hedef platform tanımlayan bir ad atayın ve ardından \**Kaydet*.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="b5c9d-251">Herhangi bir ek Hedef platformlar tanımlamak için bu adımları yineleyin, uygulama hedeflerinizi.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="b5c9d-252">Profillerinizi yapılandırdıktan ve uygulamanızı yayımlamak hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="b5c9d-253">Bunu yapmak için:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-253">To do this:</span></span>

   1. <span data-ttu-id="b5c9d-254">Varsa **Yayımla** penceresi açık değilse, proje üzerinde (çözümü değil) sağ tıklatın **Çözüm Gezgini** seçip **Yayımla**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="b5c9d-255">Yayımlama ve ardından istediğiniz profili seçin **Yayımla**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="b5c9d-256">Yayımlanacak her bir profil için bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="b5c9d-257">Unutmayın her bir hedef konum (Bizim örneğimizde, söz konusu olduğunda bin\release\netcoreapp2.1\publish\\*profil adı* uygulamanızı başlatmak için gereken dosyaları (uygulama dosyalarınızı ve tüm .NET Core dosyaları) kümesinin tamamını içerir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-257">Note that each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="b5c9d-258">Uygulamanızın dosyaları ile birlikte uygulamanızı hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayımlama işlemi yayar.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="b5c9d-259">Dosya, öncelikle bir özel durum hata ayıklama için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="b5c9d-260">Bu paket, uygulamanızın dosyaları ile değil seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="b5c9d-261">Uygulamanızı yayın derlemesinin hatalarını ayıklamak istediğiniz olay, ancak kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="b5c9d-262">Yayımlanan dosyaları istediğiniz herhangi bir şekilde dağıtın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="b5c9d-263">Örneğin, bunları bir Zip dosyasına paketleyin, basit bir kullanın `copy` komutunu ya da bunları seçtiğiniz herhangi bir yükleme paketi ile birlikte dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="b5c9d-264">Aşağıdaki tamamlandıktan *csproj* bu proje için dosya.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b5c9d-265">Ayrıca, Visual Studio ayrı bir yayımlama profili oluşturur (\*.pubxml) hedeflediğiniz her platform için.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="b5c9d-266">Örneğin, bizim linux profili (linux.pubxml) için dosya şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

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

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="b5c9d-267">Üçüncü taraf bağımlılıkları kendi içinde dağıtım</span><span class="sxs-lookup"><span data-stu-id="b5c9d-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="b5c9d-268">Bir veya daha fazla üçüncü taraf bağımlılıkları kendi içinde bir dağıtımının bağımlılıkları ekleme içerir.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="b5c9d-269">Uygulamanızı oluşturmadan önce aşağıdaki ek adımlar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="b5c9d-270">Kullanım **NuGet Paket Yöneticisi** projenize; NuGet paketine başvuru eklemek ve paket zaten sisteminizde kullanılabilir değilse, yükleyin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="b5c9d-271">Paket Yöneticisi'ni açmak için seçmeniz **Araçları** > **NuGet Paket Yöneticisi** > **çözüm için NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="b5c9d-272">Onaylayın `Newtonsoft.Json` sisteminizde yüklü olduğundan ve yüklü değilse, yükleyin.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-272">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="b5c9d-273">**Yüklü** sekmesi, sisteminizde yüklü olan NuGet paketlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="b5c9d-274">Varsa `Newtonsoft.Json` listelenmiyorsa, seçin **Gözat** sekmesinde ve arama kutusuna "Newtonsoft.Json".</span><span class="sxs-lookup"><span data-stu-id="b5c9d-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="b5c9d-275">Seçin `Newtonsoft.Json` seçip, sağ bölmede, projenizi seçmeden önce **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="b5c9d-276">Varsa `Newtonsoft.Json` olduğundan, sisteminizde yüklü, projenize sağ bölmede, proje seçerek eklemek **çözüm için paketlerini Yönet** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="b5c9d-277">Aşağıdaki tamamlandıktan *csproj* bu proje için dosya:</span><span class="sxs-lookup"><span data-stu-id="b5c9d-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="b5c9d-278">Visual Studio 15.6 ve önceki sürümleri</span><span class="sxs-lookup"><span data-stu-id="b5c9d-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

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

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="b5c9d-279">Visual Studio 15.7 ve üzeri</span><span class="sxs-lookup"><span data-stu-id="b5c9d-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

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

<span data-ttu-id="b5c9d-280">Uygulamanızı dağıttığınızda, uygulamanızda kullanılan herhangi bir üçüncü taraf bağımlılıkları ile uygulama dosyalarınızı de yer alır.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="b5c9d-281">Üçüncü taraf kitaplıklar, uygulama üzerinde çalıştığı sistemde gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="b5c9d-282">Yalnızca bir üçüncü taraf kitaplığı ile kendi içinde bir dağıtım için bu kitaplığı tarafından desteklenen platformlar dağıtabileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-282">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="b5c9d-283">Bu, daha önce yüklü sürece yerel bağımlılıkları hedef platformda nerede var olmaz yerel bağımlılıkları olan üçüncü taraf bağımlılıklarının framework bağımlı dağıtımınızda olması için benzer.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5c9d-284">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5c9d-284">See also</span></span>

* [<span data-ttu-id="b5c9d-285">.NET core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="b5c9d-285">.NET Core Application Deployment</span></span>](index.md)
* [<span data-ttu-id="b5c9d-286">.NET core çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="b5c9d-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
