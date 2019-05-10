---
title: Taşınabilir Sınıf Kitaplığı ile Platformlar Arası Geliştirme
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5b6a32aa465700fb316bf2269c4d057ff823443
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590344"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a><span data-ttu-id="c3ef0-102">Taşınabilir sınıf kitaplığı ile platformlar arası geliştirme</span><span class="sxs-lookup"><span data-stu-id="c3ef0-102">Cross-platform development with the Portable Class Library</span></span>

<span data-ttu-id="c3ef0-103">Taşınabilir sınıf kitaplığı proje türü Visual Studio'da platformlar arası uygulamalar ve kitaplıklar Microsoft platformları için hızlı ve kolay bir şekilde oluşturmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-103">The Portable Class Library project type in Visual Studio helps you build cross-platform apps and libraries for Microsoft platforms quickly and easily.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

<span data-ttu-id="c3ef0-104">Taşınabilir sınıf kitaplıkları, saat ve geliştirme ve test maliyetlerini azaltmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-104">Portable class libraries can help you reduce the time and costs of developing and testing code.</span></span> <span data-ttu-id="c3ef0-105">Bu proje türü .NET Framework taşınabilir derlemeler yazmak ve oluşturmak için kullanın ve ardından bu derlemeler .NET Framework, iOS veya Mac gibi çoklu platformları hedefleyen uygulamalar başvuru</span><span class="sxs-lookup"><span data-stu-id="c3ef0-105">Use this project type to write and build portable .NET Framework assemblies, and then reference those assemblies from apps that target multiple platforms such as the .NET Framework, iOS, or Mac.</span></span>

<span data-ttu-id="c3ef0-106">Visual Studio'da bir taşınabilir sınıf kitaplığı projesi oluşturun ve bunu geliştirmeye başlayın bile sonra hedef platformlar değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-106">Even after you create a Portable Class Library project in Visual Studio and start developing it, you can change the target platforms.</span></span> <span data-ttu-id="c3ef0-107">Visual Studio, kodunuzda yapmanız gereken değişiklikleri belirlemenize yardımcı olur, yeni derlemeler kitaplığıyla derler.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-107">Visual Studio compiles your library with the new assemblies, which helps you identify the changes you need to make in your code.</span></span>

## <a name="create-a-portable-class-library-project"></a><span data-ttu-id="c3ef0-108">Taşınabilir sınıf kitaplığı projesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="c3ef0-108">Create a Portable Class Library project</span></span>

<span data-ttu-id="c3ef0-109">Taşınabilir sınıf kitaplığı oluşturmak için Visual Studio'da sağlanan şablonunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-109">To create a Portable Class Library, use the template provided in Visual Studio.</span></span> <span data-ttu-id="c3ef0-110">Yeni bir proje oluşturun (**dosya** > **yeni proje**) ve **yeni proje** iletişim kutusunda, programlama diliniz (Visual C# veya Visual Basic) seçin.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-110">Create a new project (**File** > **New Project**), and in the **New Project** dialog box, select your programming language (Visual C# or Visual Basic).</span></span> <span data-ttu-id="c3ef0-111">Ardından, **sınıf kitaplığı (eski taşınabilir)** şablonu.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-111">Then, select the **Class Library (Legacy Portable)** template.</span></span> <span data-ttu-id="c3ef0-112">Projeniz için bir ad girin ve seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-112">Enter a name for your project and choose **OK**.</span></span>

<span data-ttu-id="c3ef0-113">**Taşınabilir sınıf kitaplığı Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-113">The **Add Portable Class Library** dialog box appears.</span></span> <span data-ttu-id="c3ef0-114">İki veya daha fazla hedefleri seçin ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-114">Choose two or more targets, and then choose **OK**.</span></span>

![Visual Studio'da taşınabilir sınıf kitaplığı hedefleri ekleme](media/add-portable-class-library.png)

## <a name="change-targets"></a><span data-ttu-id="c3ef0-116">Hedefleri Değiştir</span><span class="sxs-lookup"><span data-stu-id="c3ef0-116">Change targets</span></span>

<span data-ttu-id="c3ef0-117">Hedef platformları taşınabilir sınık kitaplık projesinin oluşturduğunuzda veya geliştirme başladıktan sonra değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-117">You can change the target platforms of a portable class library project when you create it or after you’ve started development.</span></span> <span data-ttu-id="c3ef0-118">İçinde projenizi oluşturduktan sonra hedeflerini değiştirmek istiyorsanız **Çözüm Gezgini**, taşınabilir sınıf kitaplığı projeniz (çözümü değil) için kısayol menüsünü açın ve ardından **özellikleri** .</span><span class="sxs-lookup"><span data-stu-id="c3ef0-118">If you want to change the targets after you’ve created your project, in **Solution Explorer**, open the shortcut menu for your Portable Class Library project (not the solution), and then choose **Properties**.</span></span> <span data-ttu-id="c3ef0-119">Proje özellikleri sayfasında **Kitaplığı** projeniz şu anda hedefler sekmesi platformları gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-119">On the project properties page, the **Library** tab shows the platforms that your project currently targets.</span></span>

![Visual Studio'da taşınabilir sınıf kitaplığı için proje özellikleri](media/pcl-project-properties.png)

<span data-ttu-id="c3ef0-121">Ekleme veya kaldırma hedefleri için seçin **değişiklik** düğmesini seçin ve uygun onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-121">To add or remove targets, choose the **Change** button, and then select and clear the appropriate check boxes.</span></span>

<span data-ttu-id="c3ef0-122">Hedefleri değiştirdiğinizde, projenizin geliştirmek için kullanabileceğiniz API'ler seçiminizi eşleşecek şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-122">When you change the targets, the APIs that are available to you for developing your project will change to match your selection.</span></span> <span data-ttu-id="c3ef0-123">Visual Studio değiştirme hedefleri sonucunda ortaya çıkabilecek uyarıları ve hataları bildirir.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-123">Visual Studio reports the errors and warnings that may occur as a result of the targets changing.</span></span>

<span data-ttu-id="c3ef0-124">Taşınabilirlik değerlendirmek istiyorsanız, önce derlemelerinizin Visual Studio'da değişiklik yapmak, kullanabilirsiniz [.NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).</span><span class="sxs-lookup"><span data-stu-id="c3ef0-124">If you want to evaluate the portability of your assemblies before you make changes in Visual Studio, you can use the [.NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).</span></span>

## <a name="supported-types-and-members"></a><span data-ttu-id="c3ef0-125">Desteklenen türler ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="c3ef0-125">Supported types and members</span></span>

<span data-ttu-id="c3ef0-126">Türler ve taşınabilir sınıf kitaplığı projesinde kullanılabilir üyeler çeşitli uyumluluk unsurları tarafından zorlanır:</span><span class="sxs-lookup"><span data-stu-id="c3ef0-126">The types and members that are available in Portable Class Library projects are constrained by several compatibility factors:</span></span>

- <span data-ttu-id="c3ef0-127">Bunlar, seçtiğiniz hedef arasında paylaşılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-127">They must be shared across the targets you selected.</span></span>

- <span data-ttu-id="c3ef0-128">Bu hedefler arasında benzer şekilde davranmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-128">The must behave similarly across those targets.</span></span>

- <span data-ttu-id="c3ef0-129">Kaldırılma için aday olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-129">They must not be candidates for deprecation.</span></span>

- <span data-ttu-id="c3ef0-130">Özellikle destekleyici üyeler taşınabilir olmadığında bunlar taşınabilir ortamda anlamlı olmalıdırlar.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-130">They must make sense in a portable environment, especially when supporting members are not portable.</span></span>

<span data-ttu-id="c3ef0-131">Üye taşınabilir sınıf kitaplığı ve seçili hedeflerinizi destekleniyorsa, projenizdeki ıntellisense'te görünür.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-131">If a member is supported in the Portable Class Library and for your selected targets, it will appear in your project in IntelliSense.</span></span> <span data-ttu-id="c3ef0-132">Bununla birlikte, bir API taşınabilir Sınıf Kitaplığı'nda desteklenmiyor olabilir, ancak API kullanıp kullanamayacağını bağlıdır hedeflerde, unutmayın seçin.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-132">However, remember that an API may be supported in the Portable Class Library, but whether you can use the API depends on the targets you select.</span></span>

## <a name="api-differences-in-the-portable-class-library"></a><span data-ttu-id="c3ef0-133">Taşınabilir Sınıf kitaplığındaki API farklılıkları</span><span class="sxs-lookup"><span data-stu-id="c3ef0-133">API differences in the Portable Class Library</span></span>

<span data-ttu-id="c3ef0-134">Bütün platformlar tarafından desteklenen taşınabilir sınıf kitaplığı derlemeleri uyumlu hale getirmek için bazı üyeler biraz taşınabilir Sınıf Kitaplığı'nda değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-134">To make Portable Class Library assemblies compatible across all supported platforms, some members have been slightly changed in the Portable Class Library.</span></span>

## <a name="use-the-portable-class-library"></a><span data-ttu-id="c3ef0-135">Taşınabilir sınıf kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="c3ef0-135">Use the Portable Class Library</span></span>

<span data-ttu-id="c3ef0-136">Taşınabilir sınıf kitaplığı projenizi derledikten sonra sadece bunu diğer projelerden başvuruda.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-136">After you build your Portable Class Library project, you just reference it from other projects.</span></span> <span data-ttu-id="c3ef0-137">Erişmek istediğiniz sınıfları içeren projeyi veya belirli derlemeleri projeye ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-137">You can reference either the project or specific assemblies that contain the classes you want to access.</span></span>

<span data-ttu-id="c3ef0-138">Bir taşınabilir sınıf kitaplığı derleme gerekli sürümü başvuran bir uygulamayı çalıştırmak için (veya üzeri) hedeflenen platformun bilgisayarınızda yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-138">To run an app that references a Portable Class Library assembly, the required version (or later) of the targeted platforms must be installed on your computer.</span></span> <span data-ttu-id="c3ef0-139">Visual Studio tüm gerekli framework'leri içerdiğinden, uygulamayı geliştirirken kullandığınız bilgisayarda daha fazla değişiklik gerekmeden uygulamayı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-139">Visual Studio contains all the required frameworks, so you can run the app without further modification on the computer that you used to develop the app.</span></span>

### <a name="deploy-a-universal-windows-app"></a><span data-ttu-id="c3ef0-140">Bir evrensel Windows uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="c3ef0-140">Deploy a Universal Windows app</span></span>

<span data-ttu-id="c3ef0-141">Bir evrensel Windows uygulaması oluştururken bir taşınabilir sınıf kitaplığı derleme başvuran, uygulamayı dağıtmak için ihtiyacınız olan her şey uygulama paketine dahildir ve başka bir adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-141">When you create a Universal Windows app that references a Portable Class Library assembly, everything you need to deploy the app is included in the app package, and no further steps are required.</span></span>

### <a name="deploy-a-net-framework-app"></a><span data-ttu-id="c3ef0-142">Dağıtma bir .NET Framework uygulaması</span><span class="sxs-lookup"><span data-stu-id="c3ef0-142">Deploy a .NET Framework app</span></span>

<span data-ttu-id="c3ef0-143">Taşınabilir sınıf kitaplığı derlemesine başvuran bir .NET Framework uygulamasını dağıtırken, bir bağımlılık '.NET Framework'ün doğru versiyonundaki belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-143">When you deploy a .NET Framework app that references a Portable Class Library assembly, you must specify a dependency on the correct version of the .NET Framework.</span></span> <span data-ttu-id="c3ef0-144">Bu bağımlılığı belirterek, gerekli sürümün uygulamanızla birlikte yüklü olup olmadığını garantiye almış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-144">By specifying this dependency, you ensure that the required version is installed with your app.</span></span>

- <span data-ttu-id="c3ef0-145">ClickOnce dağıtımı ile bir bağımlılık oluşturmak için: İçinde **Çözüm Gezgini**, yayımlamak istediğiniz proje için proje düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-145">To create a dependency with ClickOnce deployment: In **Solution Explorer**, choose the project node for the project you want to publish.</span></span> <span data-ttu-id="c3ef0-146">(Taşınabilir sınıf kitaplığı projesine başvuran proje budur.) Menü çubuğunda, **proje** > **özellikleri**ve ardından **Yayımla** sekmesi. Üzerinde **Yayımla** sayfasında **önkoşulları**.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-146">(This is the project that references the Portable Class Library project.) On the menu bar, choose **Project** > **Properties**, and then choose the **Publish** tab. On the **Publish** page, choose **Prerequisites**.</span></span> <span data-ttu-id="c3ef0-147">Önkoşul olarak gerekli .NET Framework sürümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-147">Select the required .NET Framework version as a prerequisite.</span></span>

- <span data-ttu-id="c3ef0-148">Bir kurulum projesi ile bir bağımlılık oluşturmak için: İçinde **Çözüm Gezgini**, Kurulum projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-148">To create a dependency with a setup project: In **Solution Explorer**, choose the setup project.</span></span> <span data-ttu-id="c3ef0-149">Menü çubuğunda, **proje** > **özellikleri** > **önkoşulları**.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-149">On the menu bar, choose **Project** > **Properties** > **Prerequisites**.</span></span> <span data-ttu-id="c3ef0-150">Önkoşul olarak gerekli .NET Framework sürümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-150">Select the required .NET Framework version as a prerequisite.</span></span>

<span data-ttu-id="c3ef0-151">.NET Framework uygulamalarını dağıtmak hakkında daha fazla bilgi için bkz. [geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="c3ef0-151">For more information about deploying .NET Framework apps, see [Deployment Guide for Developers](../../../docs/framework/deployment/deployment-guide-for-developers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3ef0-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3ef0-152">See also</span></span>

- [<span data-ttu-id="c3ef0-153">MVVM ile Taşınabilir Sınıf Kitaplığı Kullanma</span><span class="sxs-lookup"><span data-stu-id="c3ef0-153">Using Portable Class Library with MVVM</span></span>](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)
- [<span data-ttu-id="c3ef0-154">Çoklu Platformları Hedefleyen Kitaplıklar için Uygulama Kaynakları</span><span class="sxs-lookup"><span data-stu-id="c3ef0-154">App Resources for Libraries That Target Multiple Platforms</span></span>](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)
- [<span data-ttu-id="c3ef0-155">.NET taşınabilirlik Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="c3ef0-155">.NET Portability Analyzer</span></span>](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [<span data-ttu-id="c3ef0-156">Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği</span><span class="sxs-lookup"><span data-stu-id="c3ef0-156">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [<span data-ttu-id="c3ef0-157">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="c3ef0-157">Deployment</span></span>](../../../docs/framework/deployment/net-framework-applications.md)
