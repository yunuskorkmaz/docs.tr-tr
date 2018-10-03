---
title: 'Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma'
ms.date: 09/12/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9b9c9cbdb89ccf67942dcccee37ea410c6fa39a5
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036207"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="fae5b-102">Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="fae5b-102">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="fae5b-103">Uygulamaları Visual Studio'da hedefleyen derleme yaparken [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ve sonraki sürümlerinde, bağlama yönlendirmeleri, derleme birleştiriciyi geçersiz kılmak için uygulama yapılandırma dosyasına otomatik olarak da eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fae5b-103">When you compile apps in Visual Studio that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="fae5b-104">Uygulamanız veya bileşenleri, aynı derlemenin birden çok sürümüne başvurursa, uygulamanızın yapılandırma dosyasında bağlama yeniden yönlendirmelerini el ile belirtseniz de, bağlama yeniden yönlendirmeleri eklenir.</span><span class="sxs-lookup"><span data-stu-id="fae5b-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="fae5b-105">Otomatik bağlama yeniden yönlendirme özelliği hedefleyen geleneksel masaüstü uygulamaları ve web uygulamalarını etkiler [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] veya sonraki bir sürüm davranış web uygulaması için biraz farklı olmasına karşın.</span><span class="sxs-lookup"><span data-stu-id="fae5b-105">The automatic binding redirection feature affects traditional desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="fae5b-106">.NET Framework'ün önceki sürümlerini hedefleyen var olan uygulamalarınız varsa otomatik bağlama yeniden yönlendirmesini etkinleştirebilir veya el ile yazılan bağlama yeniden yönlendirmelerini tutmak istiyorsanız bu özelliği devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fae5b-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to keep manually authored binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="fae5b-107">Masaüstü uygulamalarında otomatik bağlama yeniden yönlendirmelerini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="fae5b-107">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="fae5b-108">Otomatik bağlama yeniden yönlendirmeleri hedefleyen geleneksel masaüstü uygulamaları için varsayılan olarak etkin [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ve sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="fae5b-108">Automatic binding redirects are enabled by default for traditional desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="fae5b-109">Bağlama yeniden yönlendirmeleri, uygulama derlendiğinde ve aksi takdirde gerçekleşebilecek derleme birleştirmeyi geçersiz kıldığında çıktı yapılandırma dosyasına (app.config) eklenir.</span><span class="sxs-lookup"><span data-stu-id="fae5b-109">The binding redirects are added to the output configuration (app.config) file when the app is compiled and overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="fae5b-110">Kaynak app.config dosyası değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="fae5b-110">The source app.config file is not modified.</span></span> <span data-ttu-id="fae5b-111">Uygulama için proje dosyasını değiştirerek, bu özelliği devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fae5b-111">You can disable this feature by modifying the project file for the app.</span></span>

1. <span data-ttu-id="fae5b-112">Aşağıdaki yöntemlerden birini kullanarak düzenlemek için proje dosyasını açın:</span><span class="sxs-lookup"><span data-stu-id="fae5b-112">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="fae5b-113">Visual Studio'da projeye seçin **Çözüm Gezgini**ve ardından **klasörü dosya Gezgini'nde Aç** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="fae5b-113">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="fae5b-114">Dosya Gezgini'nde, proje (.csproj veya .vbproj) dosyasını bulun ve Not Defteri'nde açın.</span><span class="sxs-lookup"><span data-stu-id="fae5b-114">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="fae5b-115">Visual Studio içinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **projeyi**.</span><span class="sxs-lookup"><span data-stu-id="fae5b-115">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="fae5b-116">Yüklenmemiş proje tekrar sağ tıklayın ve ardından **[projectname.csproj] Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="fae5b-116">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="fae5b-117">Proje dosyasında aşağıdaki özellik girdisini bulun:</span><span class="sxs-lookup"><span data-stu-id="fae5b-117">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="fae5b-118">Değişiklik `true` için `false`:</span><span class="sxs-lookup"><span data-stu-id="fae5b-118">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="fae5b-119">Otomatik bağlama yeniden yönlendirmelerini el ile etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="fae5b-119">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="fae5b-120">Bu eski sürümlerini hedefleyen .NET Framework'ün veya burada, otomatik olarak yeniden yönlendirme eklemeniz istenir durumlarda var olan uygulamalarda otomatik bağlama yeniden yönlendirmelerini etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fae5b-120">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="fae5b-121">Framework'ün daha yeni bir sürümü hedefleme, ancak otomatik olarak yeniden yönlendirmeye eklemek için istenmiyor, büyük olasılıkla derlemeleri yeniden eşleme öneren yapı çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="fae5b-121">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="fae5b-122">Aşağıdaki yöntemlerden birini kullanarak düzenlemek için proje dosyasını açın:</span><span class="sxs-lookup"><span data-stu-id="fae5b-122">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="fae5b-123">Visual Studio'da projeye seçin **Çözüm Gezgini**ve ardından **klasörü dosya Gezgini'nde Aç** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="fae5b-123">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="fae5b-124">Dosya Gezgini'nde, proje (.csproj veya .vbproj) dosyasını bulun ve Not Defteri'nde açın.</span><span class="sxs-lookup"><span data-stu-id="fae5b-124">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="fae5b-125">Visual Studio içinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **projeyi**.</span><span class="sxs-lookup"><span data-stu-id="fae5b-125">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="fae5b-126">Yüklenmemiş proje tekrar sağ tıklayın ve ardından **[projectname.csproj] Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="fae5b-126">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="fae5b-127">Şu öğe için ilk yapılandırma özellik grubuna ekleyin (altında \<PropertyGroup > etiketinin):</span><span class="sxs-lookup"><span data-stu-id="fae5b-127">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="fae5b-128">Aşağıdaki örnek, bir proje dosyasını eklenen öğeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="fae5b-128">The following shows an example project file with the element inserted:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
       <PropertyGroup>
         <Configuration Condition=" '$(Configuration)' == ''     ">Debug</Configuration>
         <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
         <ProjectGuid>{123334}</ProjectGuid>
         ...
         <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
       </PropertyGroup>
     ...
   </Project>
   ```

3. <span data-ttu-id="fae5b-129">Uygulamalarınızı derleyin.</span><span class="sxs-lookup"><span data-stu-id="fae5b-129">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="fae5b-130">Web uygulamalarında otomatik bağlama yeniden yönlendirmelerini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="fae5b-130">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="fae5b-131">Otomatik bağlama yeniden yönlendirmeleri, web uygulamaları için farklı şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fae5b-131">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="fae5b-132">Kaynak yapılandırma (web.config) dosyasının web uygulamaları için değiştirilmesi gerektiğinden, bağlama yeniden yönlendirmeleri, yapılandırma dosyasına otomatik olarak eklenmez.</span><span class="sxs-lookup"><span data-stu-id="fae5b-132">Because the source configuration (web.config) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="fae5b-133">Ancak Visual Studio, bağlama çakışmalarını size bildirir ve çakışmaları çözümlemek için bağlama yeniden yönlendirmeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fae5b-133">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="fae5b-134">Her zaman bağlama yeniden yönlendirmeleri eklemeniz istenir çünkü bir web uygulaması için bu özelliği açıkça devre dışı bırakmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fae5b-134">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="fae5b-135">Bir web.config dosyasına bağlama yeniden yönlendirmeleri eklemek için:</span><span class="sxs-lookup"><span data-stu-id="fae5b-135">To add binding redirects to a web.config file:</span></span>

1. <span data-ttu-id="fae5b-136">Visual Studio'da uygulamayı derleyin ve yapı uyarılarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fae5b-136">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="fae5b-137">![Derleme uyarısı bütünleştirilmiş kod başvurusu çakışmaları](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="fae5b-137">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="fae5b-138">Derleme bağlama çakışmaları varsa bir uyarı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fae5b-138">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="fae5b-139">Uyarıyı çift tıklatın veya uyarı seçip ENTER tuşuna **Enter**.</span><span class="sxs-lookup"><span data-stu-id="fae5b-139">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="fae5b-140">Kaynak web.config dosyasına gerekli içeriğe yeniden yönlendirmelerini otomatik olarak eklemenize olanak sağlayan bir iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fae5b-140">A dialog box that enables you to automatically add the necessary binding redirects to the source web.config file appears.</span></span>

   <span data-ttu-id="fae5b-141">![Bağlama yeniden yönlendirmeye izin iletişim](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="fae5b-141">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="fae5b-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fae5b-142">See also</span></span>

- [<span data-ttu-id="fae5b-143">\<bindingRedirect > öğesi</span><span class="sxs-lookup"><span data-stu-id="fae5b-143">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="fae5b-144">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="fae5b-144">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
