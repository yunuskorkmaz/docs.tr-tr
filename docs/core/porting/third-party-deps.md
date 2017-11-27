---
title: ".NET Core taşıma -, üçüncü taraf taraf bağımlılıkları analiz etme"
description: ".NET Core taşıma - üçüncü taraf bağımlılıkları analiz etme"
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
ms.openlocfilehash: a074978f2817abafa7b8a9fefe7c67c9c52195b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a><span data-ttu-id="c0f98-104">.NET Core taşıma -, üçüncü taraf taraf bağımlılıkları analiz etme</span><span class="sxs-lookup"><span data-stu-id="c0f98-104">Porting to .NET Core - Analyzing your Third-Party Party Dependencies</span></span>

<span data-ttu-id="c0f98-105">Taşıma işleminde ilk adım, üçüncü taraf bağımlılıkları anlamaktır.</span><span class="sxs-lookup"><span data-stu-id="c0f98-105">The first step in the porting process is to understand your third party dependencies.</span></span>  <span data-ttu-id="c0f98-106">Hangisinin, varsa, verme henüz .NET Core üzerinde çalıştırın ve hangi .NET Core üzerinde çalıştırmayın olanlar için yedek bir plan geliştirin tahmin gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0f98-106">You need to figure out which of them, if any, don't yet run on .NET Core, and develop a contingency plan for those which don't run on .NET Core.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c0f98-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c0f98-107">Prerequisites</span></span>

<span data-ttu-id="c0f98-108">Bu makalede varsayacak Windows ve Visual Studio kullanarak ve .NET Framework bugün çalışan koduna sahip.</span><span class="sxs-lookup"><span data-stu-id="c0f98-108">This article will assume you are using Windows and Visual Studio, and that you have code which runs on the .NET Framework today.</span></span>

## <a name="analyzing-nuget-packages"></a><span data-ttu-id="c0f98-109">NuGet paketleri analiz etme</span><span class="sxs-lookup"><span data-stu-id="c0f98-109">Analyzing NuGet Packages</span></span>

<span data-ttu-id="c0f98-110">Taşınabilirlik için NuGet paketleri analiz etme çok kolaydır.</span><span class="sxs-lookup"><span data-stu-id="c0f98-110">Analyzing NuGet packages for portability is very easy.</span></span>  <span data-ttu-id="c0f98-111">Bir NuGet paketi kendisini platforma özgü derlemeleri içeren klasör kümesi, tüm yapmanız gereken olmadığından bir .NET Core derleme içeren bir klasör olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c0f98-111">Because a NuGet package is itself a set of folders which contain platform-specific assemblies, all you have to do is check to see if there is a folder which contains a .NET Core assembly.</span></span>

<span data-ttu-id="c0f98-112">NuGet paketi klasörleri inceleyerek ile kolay [NuGet paketi Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aracı.</span><span class="sxs-lookup"><span data-stu-id="c0f98-112">Inspecting NuGet Package folders is easiest with the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span>  <span data-ttu-id="c0f98-113">Bunun nasıl yapılacağı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c0f98-113">Here's how to do it.</span></span>

1. <span data-ttu-id="c0f98-114">Karşıdan yükleyip NuGet paketi Gezgini'ni açın.</span><span class="sxs-lookup"><span data-stu-id="c0f98-114">Download and open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="c0f98-115">"Çevrimiçi akış açık paketinden"'i tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c0f98-115">Click "Open package from online feed".</span></span>
3. <span data-ttu-id="c0f98-116">Paketin adını arayın.</span><span class="sxs-lookup"><span data-stu-id="c0f98-116">Search for the name of the package.</span></span>
4. <span data-ttu-id="c0f98-117">Sağ taraftaki "LIB" klasörünü genişletin ve klasör adları bakın.</span><span class="sxs-lookup"><span data-stu-id="c0f98-117">Expand the "lib" folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="c0f98-118">Bir paketi üzerinde destekler de görebilirsiniz [nuget.org](https://www.nuget.org/) altında **bağımlılıkları** o paket sayfasının bölümünde.</span><span class="sxs-lookup"><span data-stu-id="c0f98-118">You can also see what a package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the page for that package.</span></span>

<span data-ttu-id="c0f98-119">Her iki durumda da, bir klasör veya giriş arayın gerekir [nuget.org](https://www.nuget.org/) aşağıdaki adlarının herhangi biri ile:</span><span class="sxs-lookup"><span data-stu-id="c0f98-119">In either case, you'll need to look for a folder or entry on [nuget.org](https://www.nuget.org/) with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="c0f98-120">Hedef Framework adlar (hangi sürümlerine eşleme TFM) bunlar [.NET standart](../../standard/net-standard.md) ve .NET Core ile uyumlu olan geleneksel taşınabilir sınıf kitaplığı (PCL) profilleri.</span><span class="sxs-lookup"><span data-stu-id="c0f98-120">These are the Target Framework Monikers (TFM) which map to versions of the [.NET Standard](../../standard/net-standard.md) and traditional Portable Class Library (PCL) profiles which are compatible with .NET Core.</span></span>  <span data-ttu-id="c0f98-121">Unutmayın `netcoreapp1.0`, uyumlu iken, uygulamalar ve değil kitaplıkları içindir.</span><span class="sxs-lookup"><span data-stu-id="c0f98-121">Note that `netcoreapp1.0`, while compatible, is for applications and not libraries.</span></span>  <span data-ttu-id="c0f98-122">Olmasına karşın, bir kitaplık kullanılarak ile yanlış bir şey `netcoreapp1.0`-bağlı olarak, bu kitaplık için herhangi bir şey amaçlanmamış olabilir *diğer* diğer tüketimi daha `netcoreapp1.0` uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="c0f98-122">Although there's nothing wrong with using a library which is `netcoreapp1.0`-based, that library may not be intended for anything *other* than consumption by other `netcoreapp1.0` applications.</span></span>

<span data-ttu-id="c0f98-123">Uyumlu olabilir .NET Core yayın öncesi sürümlerini kullanılan bazı eski TFMs vardır:</span><span class="sxs-lookup"><span data-stu-id="c0f98-123">There are also some legacy TFMs used in pre-release versions of .NET Core that may also be compatible:</span></span>

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

<span data-ttu-id="c0f98-124">**Bu büyük olasılıkla kodunuzu ile çalışır durumdayken uyumluluk garantisi yoktur**.</span><span class="sxs-lookup"><span data-stu-id="c0f98-124">**While these will likely work with your code, there is no guarantee of compatibility**.</span></span>  <span data-ttu-id="c0f98-125">Bu TFMs paketlerle yayın öncesi .NET Core paketlerle oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="c0f98-125">Packages with these TFMs were built with pre-release .NET Core packages.</span></span>  <span data-ttu-id="c0f98-126">Zaman (veya varsa) not edin böyle paketleri güncel olmasını `netstandard`-tabanlı.</span><span class="sxs-lookup"><span data-stu-id="c0f98-126">Take note of when (or if) packages like this are updated to be `netstandard`-based.</span></span>

> [!NOTE]
> <span data-ttu-id="c0f98-127">Geleneksel PCL veya yayın öncesi .NET Core hedef hedefleme paketini kullanmak için kullanmanız gerekir `imports` yönergesini, `project.json` dosya.</span><span class="sxs-lookup"><span data-stu-id="c0f98-127">To use a package targeting a traditional PCL or pre-release .NET Core target, you must use the `imports` directive in your `project.json` file.</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="c0f98-128">NuGet paket bağımlılığı .NET Core üzerinde çalıştırdığınızda değil yapmanız gerekenler</span><span class="sxs-lookup"><span data-stu-id="c0f98-128">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="c0f98-129">Üzerinde bağımlı bir NuGet paketi .NET Core üzerinde çalışmaz, yapabileceğiniz birkaç şey vardır.</span><span class="sxs-lookup"><span data-stu-id="c0f98-129">There are a few things you can do if a NuGet package you depend on won't run on .NET Core.</span></span>

1. <span data-ttu-id="c0f98-130">Proje açık bir kaynaktır ve Github'da gibi herhangi bir yerde barındırılan, developer(s) doğrudan devreye.</span><span class="sxs-lookup"><span data-stu-id="c0f98-130">If the project is open source and hosted somewhere like GitHub, you can engage the developer(s) directly.</span></span>
2. <span data-ttu-id="c0f98-131">Yazarın doğrudan üzerinde başvurabilirsiniz [nuget.org](https://www.nuget.org/) paketi için arama ve paketin sayfasının sol tarafındaki "sahipleri başvurun" tıklatarak.</span><span class="sxs-lookup"><span data-stu-id="c0f98-131">You can contact the author directly on [nuget.org](https://www.nuget.org/) by searching for the package and clicking "Contact Owners" on the left hand side of the package's page.</span></span>
3. <span data-ttu-id="c0f98-132">Kullanmakta olduğunuz paket gibi aynı görevi gerçekleştirir .NET Core üzerinde çalışan başka bir paket arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0f98-132">You can look for another package that runs on .NET Core which accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="c0f98-133">Paket kendiniz yapmakta olduğu için kod yazma girişiminde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="c0f98-133">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="c0f98-134">En az işlevselliği, uygulamanızın değiştirerek paket bağımlılığını ortadan paket uyumlu bir sürümü kullanılabilir duruma gelinceye kadar.</span><span class="sxs-lookup"><span data-stu-id="c0f98-134">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="c0f98-135">Lütfen açık kaynaklı proje maintainers ve NuGet paketi yayıncıları genellikle çünkü bunlar belirli bir etki alanı hakkında dikkat edin, ücretsiz yapın ve genellikle farklı daytime iş sahip katkıda gönüllüsü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c0f98-135">Please remember that open source project maintainers and NuGet package publishers are often volunteers who contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="c0f98-136">Ulaşmak, .NET Core desteği hakkında isteyen önce pozitif deyimiyle Kitaplığı hakkında başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c0f98-136">If you do reach out, you might start with a positive statement about the library before asking about .NET Core support.</span></span>

<span data-ttu-id="c0f98-137">Yukarıdakilerden herhangi biri ile sorununuzu yapamıyorsanız, .NET Core bağlantı noktasına daha sonraki bir tarihte zorunda kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0f98-137">If you're unable to resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="c0f98-138">.NET ekibi hangi kitaplıkları ile .NET Core sonraki desteklemek en önemli olan bilmek ister misiniz?</span><span class="sxs-lookup"><span data-stu-id="c0f98-138">The .NET Team would like to know which libraries are the most important to support next with .NET Core.</span></span> <span data-ttu-id="c0f98-139">Ayrıca bize e-posta gönderebilirsiniz dotnet@microsoft.com kullanmak istediğiniz kitaplıklar hakkında.</span><span class="sxs-lookup"><span data-stu-id="c0f98-139">You can also send us mail at dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a><span data-ttu-id="c0f98-140">NuGet paketlerini bulunmayan bağımlılıklara analiz etme</span><span class="sxs-lookup"><span data-stu-id="c0f98-140">Analyzing Dependencies which aren't NuGet Packages</span></span>

<span data-ttu-id="c0f98-141">Dosya sistemi DLL'de gibi bir NuGet paketi olmayan bir bağımlılık olabilir.</span><span class="sxs-lookup"><span data-stu-id="c0f98-141">You may have a dependency that isn't a NuGet package, such as a DLL in the filesystem.</span></span>  <span data-ttu-id="c0f98-142">Bu bağımlılık taşınabilirlik belirlemek için tek yolu çalıştırmaktır [ApiPort aracı](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).</span><span class="sxs-lookup"><span data-stu-id="c0f98-142">The only way to determine the portability of that dependency is to run the [ApiPort tool](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c0f98-143">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c0f98-143">Next steps</span></span>

<span data-ttu-id="c0f98-144">Kitaplığa bağlantı noktası oluşturma, kullanıma [Kitaplıklarınızı taşıma](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="c0f98-144">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
