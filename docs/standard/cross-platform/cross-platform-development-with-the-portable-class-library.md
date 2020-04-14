---
title: Taşınabilir Sınıf Kitaplığı ile Platformlar Arası Geliştirme
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 7caddd7361b8f364762fb4357e35cb918ae99263
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242809"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a><span data-ttu-id="dedca-102">Taşınabilir Sınıf Kitaplığı ile platform ötesi geliştirme</span><span class="sxs-lookup"><span data-stu-id="dedca-102">Cross-platform development with the Portable Class Library</span></span>

<span data-ttu-id="dedca-103">Visual Studio'daki Taşınabilir Sınıf Kitaplığı proje türü, Microsoft platformları için platformlar arası uygulamaları ve kitaplıkları hızlı ve kolay bir şekilde oluşturmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="dedca-103">The Portable Class Library project type in Visual Studio helps you build cross-platform apps and libraries for Microsoft platforms quickly and easily.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

<span data-ttu-id="dedca-104">Taşınabilir sınıf kitaplıkları, kod geliştirme ve test etme süresini ve maliyetlerini azaltmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="dedca-104">Portable class libraries can help you reduce the time and costs of developing and testing code.</span></span> <span data-ttu-id="dedca-105">Taşınabilir .NET Framework derlemeleri yazmak ve oluşturmak için bu proje türünü kullanın ve ardından .NET Framework, iOS veya Mac gibi birden çok platformu hedefleyen uygulamalardan bu derlemelere başvurun.</span><span class="sxs-lookup"><span data-stu-id="dedca-105">Use this project type to write and build portable .NET Framework assemblies, and then reference those assemblies from apps that target multiple platforms such as the .NET Framework, iOS, or Mac.</span></span>

<span data-ttu-id="dedca-106">Visual Studio'da taşınabilir sınıf kitaplığı projesi oluşturup geliştirmeye başladıktan sonra bile hedef platformları değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dedca-106">Even after you create a Portable Class Library project in Visual Studio and start developing it, you can change the target platforms.</span></span> <span data-ttu-id="dedca-107">Visual Studio kitaplığınızı yeni derlemelerle derler ve bu da kodunuzda yapmanız gereken değişiklikleri belirlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="dedca-107">Visual Studio compiles your library with the new assemblies, which helps you identify the changes you need to make in your code.</span></span>

## <a name="create-a-portable-class-library-project"></a><span data-ttu-id="dedca-108">Taşınabilir Sınıf Kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="dedca-108">Create a Portable Class Library project</span></span>

<span data-ttu-id="dedca-109">Taşınabilir Sınıf Kitaplığı oluşturmak için Visual Studio'da sağlanan şablonu kullanın.</span><span class="sxs-lookup"><span data-stu-id="dedca-109">To create a Portable Class Library, use the template provided in Visual Studio.</span></span> <span data-ttu-id="dedca-110">Yeni bir proje **(Dosya** > **Yeni Proje)** oluşturun ve Yeni **Proje** iletişim kutusunda programlama dilinizi (Visual C# veya Visual Basic) seçin.</span><span class="sxs-lookup"><span data-stu-id="dedca-110">Create a new project (**File** > **New Project**), and in the **New Project** dialog box, select your programming language (Visual C# or Visual Basic).</span></span> <span data-ttu-id="dedca-111">Ardından, **Sınıf Kitaplığı (Eski Taşınabilir)** şablonu'nu seçin.</span><span class="sxs-lookup"><span data-stu-id="dedca-111">Then, select the **Class Library (Legacy Portable)** template.</span></span> <span data-ttu-id="dedca-112">Projeniz için bir ad girin ve **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="dedca-112">Enter a name for your project and choose **OK**.</span></span>

<span data-ttu-id="dedca-113">**Taşınabilir Sınıf Kitaplığı Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="dedca-113">The **Add Portable Class Library** dialog box appears.</span></span> <span data-ttu-id="dedca-114">İki veya daha fazla hedef seçin ve sonra **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="dedca-114">Choose two or more targets, and then choose **OK**.</span></span>

![Visual Studio'da taşınabilir sınıf kitaplığı hedefleri ekleme](media/add-portable-class-library.png)

## <a name="change-targets"></a><span data-ttu-id="dedca-116">Hedefleri değiştirme</span><span class="sxs-lookup"><span data-stu-id="dedca-116">Change targets</span></span>

<span data-ttu-id="dedca-117">Taşınabilir sınıf kitaplığı projesinin hedef platformlarını oluşturduğunuzda veya geliştirmeye başladıktan sonra değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dedca-117">You can change the target platforms of a portable class library project when you create it or after you've started development.</span></span> <span data-ttu-id="dedca-118">**Projenizi**oluşturduktan sonra hedefleri değiştirmek istiyorsanız, Solution Explorer'da Taşınabilir Sınıf Kitaplığı projenizin kısayol menüsünü açın (çözüm değil) ve ardından **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="dedca-118">If you want to change the targets after you've created your project, in **Solution Explorer**, open the shortcut menu for your Portable Class Library project (not the solution), and then choose **Properties**.</span></span> <span data-ttu-id="dedca-119">Proje özellikleri sayfasında **Kitaplık** sekmesi, projenizin şu anda hedeflenen platformları gösterir.</span><span class="sxs-lookup"><span data-stu-id="dedca-119">On the project properties page, the **Library** tab shows the platforms that your project currently targets.</span></span>

![Visual Studio Taşınabilir Sınıf Kitaplığı için proje özellikleri](media/pcl-project-properties.png)

<span data-ttu-id="dedca-121">Hedefler eklemek veya kaldırmak için **Değiştir** düğmesini seçin ve ardından uygun onay kutularını seçip temizleyin.</span><span class="sxs-lookup"><span data-stu-id="dedca-121">To add or remove targets, choose the **Change** button, and then select and clear the appropriate check boxes.</span></span>

<span data-ttu-id="dedca-122">Hedefleri değiştirdiğinizde, projenizi geliştirmek için kullanabileceğiniz API'ler seçiminize uyacak şekilde değişecektir.</span><span class="sxs-lookup"><span data-stu-id="dedca-122">When you change the targets, the APIs that are available to you for developing your project will change to match your selection.</span></span> <span data-ttu-id="dedca-123">Visual Studio, hedeflerin değişmesi sonucu oluşabilecek hataları ve uyarıları bildirir.</span><span class="sxs-lookup"><span data-stu-id="dedca-123">Visual Studio reports the errors and warnings that may occur as a result of the targets changing.</span></span>

<span data-ttu-id="dedca-124">Visual Studio'da değişiklik yapmadan önce derlemelerinizin taşınabilirliğini değerlendirmek istiyorsanız [,.NET Taşınabilirlik Çözümleyicisini](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dedca-124">If you want to evaluate the portability of your assemblies before you make changes in Visual Studio, you can use the [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span></span>

## <a name="supported-types-and-members"></a><span data-ttu-id="dedca-125">Desteklenen türler ve üyeler</span><span class="sxs-lookup"><span data-stu-id="dedca-125">Supported types and members</span></span>

<span data-ttu-id="dedca-126">Taşınabilir Sınıf Kitaplığı projelerinde bulunan türleri ve üyeleri çeşitli uyumluluk faktörleri ile sınırlandırılmıştır:</span><span class="sxs-lookup"><span data-stu-id="dedca-126">The types and members that are available in Portable Class Library projects are constrained by several compatibility factors:</span></span>

- <span data-ttu-id="dedca-127">Bunlar seçtiğiniz hedefler arasında paylaşılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dedca-127">They must be shared across the targets you selected.</span></span>

- <span data-ttu-id="dedca-128">Bu hedefler arasında benzer şekilde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dedca-128">The must behave similarly across those targets.</span></span>

- <span data-ttu-id="dedca-129">Kaldırılma için aday olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="dedca-129">They must not be candidates for deprecation.</span></span>

- <span data-ttu-id="dedca-130">Özellikle destekleyici üyeler taşınabilir olmadığında bunlar taşınabilir ortamda anlamlı olmalıdırlar.</span><span class="sxs-lookup"><span data-stu-id="dedca-130">They must make sense in a portable environment, especially when supporting members are not portable.</span></span>

<span data-ttu-id="dedca-131">Taşınabilir Sınıf Kitaplığı'nda ve seçtiğiniz hedefler için bir üye desteklenirse, IntelliSense'deki projenizde görünür.</span><span class="sxs-lookup"><span data-stu-id="dedca-131">If a member is supported in the Portable Class Library and for your selected targets, it will appear in your project in IntelliSense.</span></span> <span data-ttu-id="dedca-132">Ancak, Taşınabilir Sınıf Kitaplığı'nda bir API'nin desteklenebileceğini, ancak API'yi kullanıp kullanamayacağınız seçtiğiniz hedeflere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dedca-132">However, remember that an API may be supported in the Portable Class Library, but whether you can use the API depends on the targets you select.</span></span>

## <a name="api-differences-in-the-portable-class-library"></a><span data-ttu-id="dedca-133">Taşınabilir Sınıf Kitaplığı'ndaki API farkları</span><span class="sxs-lookup"><span data-stu-id="dedca-133">API differences in the Portable Class Library</span></span>

<span data-ttu-id="dedca-134">Desteklenen tüm platformlarda Taşınabilir Sınıf Kitaplığı derlemelerini uyumlu hale getirmek için, bazı üyeler Taşınabilir Sınıf Kitaplığı'nda biraz değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="dedca-134">To make Portable Class Library assemblies compatible across all supported platforms, some members have been slightly changed in the Portable Class Library.</span></span>

## <a name="use-the-portable-class-library"></a><span data-ttu-id="dedca-135">Taşınabilir Sınıf Kitaplığını Kullanma</span><span class="sxs-lookup"><span data-stu-id="dedca-135">Use the Portable Class Library</span></span>

<span data-ttu-id="dedca-136">Taşınabilir Sınıf Kitaplığı projenizi yaptıktan sonra, diğer projelerden başvurusunuz.</span><span class="sxs-lookup"><span data-stu-id="dedca-136">After you build your Portable Class Library project, you just reference it from other projects.</span></span> <span data-ttu-id="dedca-137">Erişmek istediğiniz sınıfları içeren projeyi veya belirli derlemeleri projeye ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dedca-137">You can reference either the project or specific assemblies that contain the classes you want to access.</span></span>

<span data-ttu-id="dedca-138">Taşınabilir Sınıf Kitaplığı derlemesine başvuran bir uygulamayı çalıştırmak için, hedeflenen platformların gerekli sürümünün (veya sonraki) bilgisayarınıza yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dedca-138">To run an app that references a Portable Class Library assembly, the required version (or later) of the targeted platforms must be installed on your computer.</span></span> <span data-ttu-id="dedca-139">Visual Studio gerekli tüm çerçeveleri içerir, böylece uygulamayı geliştirmek için kullandığınız bilgisayarda daha fazla değişiklik yapmadan uygulamayı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dedca-139">Visual Studio contains all the required frameworks, so you can run the app without further modification on the computer that you used to develop the app.</span></span>

### <a name="deploy-a-universal-windows-app"></a><span data-ttu-id="dedca-140">Evrensel Windows uygulamasını dağıtma</span><span class="sxs-lookup"><span data-stu-id="dedca-140">Deploy a Universal Windows app</span></span>

<span data-ttu-id="dedca-141">Taşınabilir Sınıf Kitaplığı derlemesine başvuran bir Evrensel Windows uygulaması oluşturduğunuzda, uygulamayı dağıtmak için gereken her şey uygulama paketine dahil edilir ve başka bir adım gerekmez.</span><span class="sxs-lookup"><span data-stu-id="dedca-141">When you create a Universal Windows app that references a Portable Class Library assembly, everything you need to deploy the app is included in the app package, and no further steps are required.</span></span>

### <a name="deploy-a-net-framework-app"></a><span data-ttu-id="dedca-142">Bir .NET Framework uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="dedca-142">Deploy a .NET Framework app</span></span>

<span data-ttu-id="dedca-143">Taşınabilir Sınıf Kitaplığı derlemesi başvurur bir .NET Framework uygulaması dağıttığınızda, .NET Framework'ün doğru sürümüne bir bağımlılık belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dedca-143">When you deploy a .NET Framework app that references a Portable Class Library assembly, you must specify a dependency on the correct version of the .NET Framework.</span></span> <span data-ttu-id="dedca-144">Bu bağımlılığı belirterek, gerekli sürümün uygulamanızla birlikte yüklü olup olmadığını garantiye almış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="dedca-144">By specifying this dependency, you ensure that the required version is installed with your app.</span></span>

- <span data-ttu-id="dedca-145">ClickOnce dağıtım: **Solution Explorer'da,** yayımlamak istediğiniz proje için proje düğümlerini seçin.</span><span class="sxs-lookup"><span data-stu-id="dedca-145">To create a dependency with ClickOnce deployment: In **Solution Explorer**, choose the project node for the project you want to publish.</span></span> <span data-ttu-id="dedca-146">(Bu, Taşınabilir Sınıf Kitaplığı projesine başvuran projedir.) Menü çubuğunda **Project** > **Properties'i**seçin ve ardından **Yayımla** sekmesini seçin. **Yayımla** sayfasında **Önkoşullar'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="dedca-146">(This is the project that references the Portable Class Library project.) On the menu bar, choose **Project** > **Properties**, and then choose the **Publish** tab. On the **Publish** page, choose **Prerequisites**.</span></span> <span data-ttu-id="dedca-147">Önkoşul olarak gerekli .NET Framework sürümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="dedca-147">Select the required .NET Framework version as a prerequisite.</span></span>

- <span data-ttu-id="dedca-148">Bir kurulum projesiyle bağımlılık oluşturmak için: **Solution Explorer'da**kurulum projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="dedca-148">To create a dependency with a setup project: In **Solution Explorer**, choose the setup project.</span></span> <span data-ttu-id="dedca-149">Menü çubuğunda **Project** > **Properties** > **Önkoşulları'nı**seçin.</span><span class="sxs-lookup"><span data-stu-id="dedca-149">On the menu bar, choose **Project** > **Properties** > **Prerequisites**.</span></span> <span data-ttu-id="dedca-150">Önkoşul olarak gerekli .NET Framework sürümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="dedca-150">Select the required .NET Framework version as a prerequisite.</span></span>

<span data-ttu-id="dedca-151">.NET Framework uygulamalarını dağıtma hakkında daha fazla bilgi için [Geliştiriciler için Dağıtım Kılavuzu'na](../../../docs/framework/deployment/deployment-guide-for-developers.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="dedca-151">For more information about deploying .NET Framework apps, see [Deployment Guide for Developers](../../../docs/framework/deployment/deployment-guide-for-developers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dedca-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dedca-152">See also</span></span>

- [<span data-ttu-id="dedca-153">MVVM ile Taşınabilir Sınıf Kitaplığı Kullanma</span><span class="sxs-lookup"><span data-stu-id="dedca-153">Using Portable Class Library with MVVM</span></span>](using-portable-class-library-with-model-view-view-model.md)
- [<span data-ttu-id="dedca-154">Birden Çok Platformu Hedefleyen Kütüphaneler için Uygulama Kaynakları</span><span class="sxs-lookup"><span data-stu-id="dedca-154">App Resources for Libraries That Target Multiple Platforms</span></span>](app-resources-for-libraries-that-target-multiple-platforms.md)
- [<span data-ttu-id="dedca-155">.NET Taşınabilirlik Analizörü</span><span class="sxs-lookup"><span data-stu-id="dedca-155">.NET Portability Analyzer</span></span>](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [<span data-ttu-id="dedca-156">Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği</span><span class="sxs-lookup"><span data-stu-id="dedca-156">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [<span data-ttu-id="dedca-157">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="dedca-157">Deployment</span></span>](../../../docs/framework/deployment/net-framework-applications.md)
