---
title: Taşınabilir Sınıf Kitaplığı ile Platformlar Arası Geliştirme
description: .NET 'teki taşınabilir sınıf kitaplığı proje türünü kullanarak, Microsoft platformları için platformlar arası uygulamaları ve kitaplıkları hızlı ve kolay bir şekilde oluşturun.
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: be1a49f7da7ce98f9e5e3ff8d927ce5230bfa8d8
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769151"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a><span data-ttu-id="dfe84-103">Taşınabilir sınıf kitaplığı ile platformlar arası geliştirme</span><span class="sxs-lookup"><span data-stu-id="dfe84-103">Cross-platform development with the Portable Class Library</span></span>

<span data-ttu-id="dfe84-104">Visual Studio 'daki taşınabilir sınıf kitaplığı proje türü, Microsoft platformları için platformlar arası uygulamaları ve kitaplıkları hızlı ve kolay bir şekilde oluşturmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="dfe84-104">The Portable Class Library project type in Visual Studio helps you build cross-platform apps and libraries for Microsoft platforms quickly and easily.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

<span data-ttu-id="dfe84-105">Taşınabilir sınıf kitaplıkları, kod geliştirme ve test etme süresini ve maliyetlerini azaltmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="dfe84-105">Portable class libraries can help you reduce the time and costs of developing and testing code.</span></span> <span data-ttu-id="dfe84-106">Taşınabilir .NET Framework derlemeleri yazmak ve derlemek ve sonra .NET Framework, iOS veya Mac gibi birden çok platformu hedefleyen uygulamalardan bu derlemelere başvurmak için bu proje türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="dfe84-106">Use this project type to write and build portable .NET Framework assemblies, and then reference those assemblies from apps that target multiple platforms such as the .NET Framework, iOS, or Mac.</span></span>

<span data-ttu-id="dfe84-107">Visual Studio 'da taşınabilir bir sınıf kitaplığı projesi oluşturup geliştirmeye başladıktan sonra bile hedef platformları değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfe84-107">Even after you create a Portable Class Library project in Visual Studio and start developing it, you can change the target platforms.</span></span> <span data-ttu-id="dfe84-108">Visual Studio, kitaplığınızı yeni Derlemelerle derler ve bu da kodunuzda yapmanız gereken değişiklikleri belirlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="dfe84-108">Visual Studio compiles your library with the new assemblies, which helps you identify the changes you need to make in your code.</span></span>

## <a name="create-a-portable-class-library-project"></a><span data-ttu-id="dfe84-109">Taşınabilir sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="dfe84-109">Create a Portable Class Library project</span></span>

<span data-ttu-id="dfe84-110">Taşınabilir bir sınıf kitaplığı oluşturmak için, Visual Studio 'da sunulan şablonu kullanın.</span><span class="sxs-lookup"><span data-stu-id="dfe84-110">To create a Portable Class Library, use the template provided in Visual Studio.</span></span> <span data-ttu-id="dfe84-111">Yeni bir proje (**Dosya**  >  **Yeni proje**) oluşturun ve **Yeni proje** iletişim kutusunda, programlama dilinizi (Visual C# veya Visual Basic) seçin.</span><span class="sxs-lookup"><span data-stu-id="dfe84-111">Create a new project (**File** > **New Project**), and in the **New Project** dialog box, select your programming language (Visual C# or Visual Basic).</span></span> <span data-ttu-id="dfe84-112">Ardından, **sınıf kitaplığı (eski taşınabilir)** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="dfe84-112">Then, select the **Class Library (Legacy Portable)** template.</span></span> <span data-ttu-id="dfe84-113">Projeniz için bir ad girin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="dfe84-113">Enter a name for your project and choose **OK**.</span></span>

<span data-ttu-id="dfe84-114">**Taşınabilir sınıf kitaplığı Ekle** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="dfe84-114">The **Add Portable Class Library** dialog box appears.</span></span> <span data-ttu-id="dfe84-115">İki veya daha fazla hedef seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="dfe84-115">Choose two or more targets, and then choose **OK**.</span></span>

![Visual Studio 'da taşınabilir sınıf kitaplığı hedefleri ekleme](media/add-portable-class-library.png)

## <a name="change-targets"></a><span data-ttu-id="dfe84-117">Değişiklik hedefleri</span><span class="sxs-lookup"><span data-stu-id="dfe84-117">Change targets</span></span>

<span data-ttu-id="dfe84-118">Bir taşınabilir sınıf kitaplığı projesinin hedef platformlarını oluştururken veya geliştirmeye başladıktan sonra değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfe84-118">You can change the target platforms of a portable class library project when you create it or after you've started development.</span></span> <span data-ttu-id="dfe84-119">Projenizi oluşturduktan sonra hedefleri değiştirmek istiyorsanız, **Çözüm Gezgini**' de, taşınabilir sınıf kitaplığı projeniz (çözüm değil) için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="dfe84-119">If you want to change the targets after you've created your project, in **Solution Explorer**, open the shortcut menu for your Portable Class Library project (not the solution), and then choose **Properties**.</span></span> <span data-ttu-id="dfe84-120">Proje Özellikleri sayfasında, **kitaplık** sekmesi projenizin şu anda hedeflediği platformları gösterir.</span><span class="sxs-lookup"><span data-stu-id="dfe84-120">On the project properties page, the **Library** tab shows the platforms that your project currently targets.</span></span>

![Visual Studio 'da taşınabilir sınıf kitaplığı için proje özellikleri](media/pcl-project-properties.png)

<span data-ttu-id="dfe84-122">Hedefleri eklemek veya kaldırmak için, **Değiştir** düğmesini seçin ve ardından uygun onay kutularını seçin ve temizleyin.</span><span class="sxs-lookup"><span data-stu-id="dfe84-122">To add or remove targets, choose the **Change** button, and then select and clear the appropriate check boxes.</span></span>

<span data-ttu-id="dfe84-123">Hedefleri değiştirdiğinizde, projenizi geliştirirken kullanabileceğiniz API 'Ler seçiminizle eşleşecek şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="dfe84-123">When you change the targets, the APIs that are available to you for developing your project will change to match your selection.</span></span> <span data-ttu-id="dfe84-124">Visual Studio, hedeflerin değişme sonucu olarak oluşabilecek hataları ve uyarıları raporlar.</span><span class="sxs-lookup"><span data-stu-id="dfe84-124">Visual Studio reports the errors and warnings that may occur as a result of the targets changing.</span></span>

<span data-ttu-id="dfe84-125">Visual Studio 'da değişiklik yapmadan önce derlemelerinizin taşınabilirliği değerlendirmek istiyorsanız [.net taşınabilirlik Çözümleyicisi](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)' ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfe84-125">If you want to evaluate the portability of your assemblies before you make changes in Visual Studio, you can use the [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span></span>

## <a name="supported-types-and-members"></a><span data-ttu-id="dfe84-126">Desteklenen türler ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="dfe84-126">Supported types and members</span></span>

<span data-ttu-id="dfe84-127">Taşınabilir sınıf kitaplığı projelerinde kullanılabilir olan türler ve Üyeler çeşitli uyumluluk faktörlerine göre kısıtlanıyor:</span><span class="sxs-lookup"><span data-stu-id="dfe84-127">The types and members that are available in Portable Class Library projects are constrained by several compatibility factors:</span></span>

- <span data-ttu-id="dfe84-128">Seçtiğiniz hedefler arasında paylaşılmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="dfe84-128">They must be shared across the targets you selected.</span></span>

- <span data-ttu-id="dfe84-129">Bu hedefler arasında benzer şekilde davranmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfe84-129">The must behave similarly across those targets.</span></span>

- <span data-ttu-id="dfe84-130">Kaldırılma için aday olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfe84-130">They must not be candidates for deprecation.</span></span>

- <span data-ttu-id="dfe84-131">Özellikle destekleyici üyeler taşınabilir olmadığında bunlar taşınabilir ortamda anlamlı olmalıdırlar.</span><span class="sxs-lookup"><span data-stu-id="dfe84-131">They must make sense in a portable environment, especially when supporting members are not portable.</span></span>

<span data-ttu-id="dfe84-132">Taşınabilir sınıf kitaplığında ve seçtiğiniz hedeflerde bir üye destekleniyorsa, IntelliSense 'de projenizde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="dfe84-132">If a member is supported in the Portable Class Library and for your selected targets, it will appear in your project in IntelliSense.</span></span> <span data-ttu-id="dfe84-133">Ancak, taşınabilir sınıf kitaplığında bir API 'nin desteklenip desteklenmediğini unutmayın, ancak API 'YI kullanıp kullanmayacağınızı seçtiğiniz hedeflere göre değişir.</span><span class="sxs-lookup"><span data-stu-id="dfe84-133">However, remember that an API may be supported in the Portable Class Library, but whether you can use the API depends on the targets you select.</span></span>

## <a name="api-differences-in-the-portable-class-library"></a><span data-ttu-id="dfe84-134">Taşınabilir Sınıf kitaplığındaki API farklılıkları</span><span class="sxs-lookup"><span data-stu-id="dfe84-134">API differences in the Portable Class Library</span></span>

<span data-ttu-id="dfe84-135">Taşınabilir sınıf kitaplığı derlemelerini desteklenen tüm platformlarda uyumlu hale getirmek için bazı Üyeler taşınabilir sınıf kitaplığı 'nda biraz değişmiş.</span><span class="sxs-lookup"><span data-stu-id="dfe84-135">To make Portable Class Library assemblies compatible across all supported platforms, some members have been slightly changed in the Portable Class Library.</span></span>

## <a name="use-the-portable-class-library"></a><span data-ttu-id="dfe84-136">Taşınabilir sınıf kitaplığını kullanma</span><span class="sxs-lookup"><span data-stu-id="dfe84-136">Use the Portable Class Library</span></span>

<span data-ttu-id="dfe84-137">Taşınabilir sınıf kitaplığı projenizi oluşturduktan sonra, yalnızca diğer projelerden başvuru yapmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="dfe84-137">After you build your Portable Class Library project, you just reference it from other projects.</span></span> <span data-ttu-id="dfe84-138">Erişmek istediğiniz sınıfları içeren projeyi veya belirli derlemeleri projeye ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfe84-138">You can reference either the project or specific assemblies that contain the classes you want to access.</span></span>

<span data-ttu-id="dfe84-139">Taşınabilir bir sınıf kitaplığı derlemesine başvuran bir uygulamayı çalıştırmak için, hedeflenen platformların gerekli sürümü (veya üzeri) bilgisayarınızda yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfe84-139">To run an app that references a Portable Class Library assembly, the required version (or later) of the targeted platforms must be installed on your computer.</span></span> <span data-ttu-id="dfe84-140">Visual Studio tüm gerekli çerçeveleri içerir, bu nedenle uygulamayı geliştirmek için kullandığınız bilgisayarda daha fazla değişiklik yapmadan uygulamayı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dfe84-140">Visual Studio contains all the required frameworks, so you can run the app without further modification on the computer that you used to develop the app.</span></span>

### <a name="deploy-a-universal-windows-app"></a><span data-ttu-id="dfe84-141">Evrensel Windows uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="dfe84-141">Deploy a Universal Windows app</span></span>

<span data-ttu-id="dfe84-142">Taşınabilir bir sınıf kitaplığı derlemesine başvuran bir Evrensel Windows uygulaması oluşturduğunuzda, uygulamayı dağıtmak için ihtiyacınız olan her şey uygulama paketine dahil edilir ve başka bir adım gerekmez.</span><span class="sxs-lookup"><span data-stu-id="dfe84-142">When you create a Universal Windows app that references a Portable Class Library assembly, everything you need to deploy the app is included in the app package, and no further steps are required.</span></span>

### <a name="deploy-a-net-framework-app"></a><span data-ttu-id="dfe84-143">.NET Framework uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="dfe84-143">Deploy a .NET Framework app</span></span>

<span data-ttu-id="dfe84-144">Taşınabilir bir sınıf kitaplığı derlemesine başvuran bir .NET Framework uygulaması dağıttığınızda, .NET Framework doğru sürümünde bir bağımlılık belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dfe84-144">When you deploy a .NET Framework app that references a Portable Class Library assembly, you must specify a dependency on the correct version of the .NET Framework.</span></span> <span data-ttu-id="dfe84-145">Bu bağımlılığı belirterek, gerekli sürümün uygulamanızla birlikte yüklü olup olmadığını garantiye almış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="dfe84-145">By specifying this dependency, you ensure that the required version is installed with your app.</span></span>

- <span data-ttu-id="dfe84-146">ClickOnce dağıtımı ile bir bağımlılık oluşturmak için: **Çözüm Gezgini**, yayımlamak istediğiniz projenin proje düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="dfe84-146">To create a dependency with ClickOnce deployment: In **Solution Explorer**, choose the project node for the project you want to publish.</span></span> <span data-ttu-id="dfe84-147">(Bu, taşınabilir sınıf kitaplığı projesine başvuruda bulunan projem.) Menü çubuğunda, **Proje**  >  **özellikleri**' ni ve ardından **Yayımla** sekmesini seçin. **Yayımla** sayfasında, **Önkoşullar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="dfe84-147">(This is the project that references the Portable Class Library project.) On the menu bar, choose **Project** > **Properties**, and then choose the **Publish** tab. On the **Publish** page, choose **Prerequisites**.</span></span> <span data-ttu-id="dfe84-148">Önkoşul olarak gerekli .NET Framework sürümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="dfe84-148">Select the required .NET Framework version as a prerequisite.</span></span>

- <span data-ttu-id="dfe84-149">Bir kurulum projesi ile bir bağımlılık oluşturmak için: **Çözüm Gezgini**, Kurulum projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="dfe84-149">To create a dependency with a setup project: In **Solution Explorer**, choose the setup project.</span></span> <span data-ttu-id="dfe84-150">Menü çubuğunda, **Proje**  >  **özellikleri**  >  **önkoşulları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="dfe84-150">On the menu bar, choose **Project** > **Properties** > **Prerequisites**.</span></span> <span data-ttu-id="dfe84-151">Önkoşul olarak gerekli .NET Framework sürümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="dfe84-151">Select the required .NET Framework version as a prerequisite.</span></span>

<span data-ttu-id="dfe84-152">.NET Framework uygulamalarını dağıtma hakkında daha fazla bilgi için bkz. [geliştiriciler Için dağıtım kılavuzu](../../framework/deployment/deployment-guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="dfe84-152">For more information about deploying .NET Framework apps, see [Deployment Guide for Developers](../../framework/deployment/deployment-guide-for-developers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dfe84-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfe84-153">See also</span></span>

- [<span data-ttu-id="dfe84-154">MVVM ile Taşınabilir Sınıf Kitaplığı Kullanma</span><span class="sxs-lookup"><span data-stu-id="dfe84-154">Using Portable Class Library with MVVM</span></span>](using-portable-class-library-with-model-view-view-model.md)
- [<span data-ttu-id="dfe84-155">Birden çok platformu hedefleyen kitaplıklar için uygulama kaynakları</span><span class="sxs-lookup"><span data-stu-id="dfe84-155">App Resources for Libraries That Target Multiple Platforms</span></span>](app-resources-for-libraries-that-target-multiple-platforms.md)
- [<span data-ttu-id="dfe84-156">.NET taşınabilirlik Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="dfe84-156">.NET Portability Analyzer</span></span>](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [<span data-ttu-id="dfe84-157">Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği</span><span class="sxs-lookup"><span data-stu-id="dfe84-157">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](support-for-windows-store-apps-and-windows-runtime.md)
- [<span data-ttu-id="dfe84-158">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="dfe84-158">Deployment</span></span>](../../framework/deployment/net-framework-applications.md)
