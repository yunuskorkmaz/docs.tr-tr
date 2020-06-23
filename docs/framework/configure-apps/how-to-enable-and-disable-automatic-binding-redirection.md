---
title: Yeniden oluşturulmuş bağlama yeniden yönlendirmelerini etkinleştir veya devre dışı bırak
description: Otomatik bağlama yeniden yönlendirmesini etkinleştirme veya devre dışı bırakma konusunu okuyun. Bu özellik, .NET 4.5.1 veya üstünü hedefleyen masaüstü uygulamalarını ve Web uygulamalarını etkiler.
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
ms.openlocfilehash: edee95f6c3b2c2d74c4f1b68e0a65e5cb0e85f54
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105397"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="36c05-104">Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="36c05-104">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="36c05-105">Visual Studio 'da .NET Framework 4.5.1 ve sonraki sürümleri hedefleyen uygulamalar derlerken, bağlama yeniden yönlendirmeleri, derleme birleşme işlemini geçersiz kılmak için uygulama yapılandırma dosyasına otomatik olarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="36c05-105">When you compile apps in Visual Studio that target the .NET Framework 4.5.1 and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="36c05-106">Uygulamanız veya bileşenleri, aynı derlemenin birden çok sürümüne başvurursa, uygulamanızın yapılandırma dosyasında bağlama yeniden yönlendirmelerini el ile belirtseniz de, bağlama yeniden yönlendirmeleri eklenir.</span><span class="sxs-lookup"><span data-stu-id="36c05-106">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="36c05-107">Otomatik bağlama yeniden yönlendirme özelliği, bir Web uygulaması için davranış biraz farklı olsa da, .NET Framework 4.5.1 veya sonraki bir sürümü hedefleyen masaüstü uygulamalarını ve Web uygulamalarını etkiler.</span><span class="sxs-lookup"><span data-stu-id="36c05-107">The automatic binding redirection feature affects desktop apps and web apps that target the .NET Framework 4.5.1 or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="36c05-108">.NET Framework önceki sürümlerini hedefleyen mevcut uygulamalarınız varsa otomatik bağlama yeniden yönlendirmesini etkinleştirebilir veya bağlama yeniden yönlendirmelerini el ile yazmak istiyorsanız bu özelliği devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36c05-108">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to manually author binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="36c05-109">Masaüstü uygulamalarında otomatik bağlama yeniden yönlendirmelerini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="36c05-109">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="36c05-110">Otomatik bağlama yeniden yönlendirmeleri, .NET Framework 4.5.1 ve sonraki sürümleri hedefleyen Windows Masaüstü uygulamaları için varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="36c05-110">Automatic binding redirects are enabled by default for Windows desktop apps that target the .NET Framework 4.5.1 and later versions.</span></span> <span data-ttu-id="36c05-111">Bağlama yeniden yönlendirmeleri, uygulama derlendikten sonra çıkış yapılandırması (**app.config**) dosyasına eklenir ve başka bir şekilde gerçekleşmiş olabilecek derleme birleşme işlemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="36c05-111">The binding redirects are added to the output configuration (**app.config**) file when the app is compiled and override the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="36c05-112">Kaynak **app.config** dosyası değiştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="36c05-112">The source **app.config** file is not modified.</span></span> <span data-ttu-id="36c05-113">Uygulama için proje dosyasını değiştirerek veya Visual Studio 'daki proje özelliklerinde bir onay kutusunun seçimini kaldırarak bu özelliği devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36c05-113">You can disable this feature by modifying the project file for the app or by deselecting a checkbox in the project's properties in Visual Studio.</span></span>

### <a name="disable-through-project-properties"></a><span data-ttu-id="36c05-114">Proje özellikleri aracılığıyla devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="36c05-114">Disable through project properties</span></span>

<span data-ttu-id="36c05-115">Visual Studio 2017 sürüm 15,7 veya sonraki bir sürümü varsa, projenin özellik sayfalarındaki otomatik olarak oluşturulan bağlamayı kolayca devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36c05-115">If you have Visual Studio 2017 version 15.7 or later, you can easily disable autogenerated binding redirects in the project's property pages.</span></span>

1. <span data-ttu-id="36c05-116">**Çözüm Gezgini** ' de projeye sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="36c05-116">Right-click the project in **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="36c05-117">**Uygulama** sayfasında **bağlama yeniden yönlendirmeleri otomatik oluştur** seçeneğinin işaretini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="36c05-117">On the **Application** page, uncheck the **Auto-generate binding redirects** option.</span></span>

3. <span data-ttu-id="36c05-118">**Ctrl** + Değişikliği kaydetmek için CTRL**S** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="36c05-118">Press **Ctrl**+**S** to save the change.</span></span>

### <a name="disable-manually-in-the-project-file"></a><span data-ttu-id="36c05-119">Proje dosyasında el ile devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="36c05-119">Disable manually in the project file</span></span>

1. <span data-ttu-id="36c05-120">Aşağıdaki yöntemlerden birini kullanarak, proje dosyasını düzenlenmek üzere açın:</span><span class="sxs-lookup"><span data-stu-id="36c05-120">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="36c05-121">Visual Studio 'da **Çözüm Gezgini**' de projeyi seçin ve sonra kısayol menüsünden **klasörü dosya Gezgini 'nde aç** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="36c05-121">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="36c05-122">Dosya Gezgini 'nde, proje (. csproj veya. vbproj) dosyasını bulun ve Not defteri 'nde açın.</span><span class="sxs-lookup"><span data-stu-id="36c05-122">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="36c05-123">Visual Studio 'da, **Çözüm Gezgini**, projeye sağ tıklayın ve **Projeyi Kaldır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="36c05-123">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="36c05-124">Kaldırılmış projeyi yeniden sağ tıklatın ve ardından **Düzenle [ProjectName. csproj]** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="36c05-124">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="36c05-125">Proje dosyasında aşağıdaki özellik girdisini bulun:</span><span class="sxs-lookup"><span data-stu-id="36c05-125">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="36c05-126">Şu `true` şekilde değiştirin `false` :</span><span class="sxs-lookup"><span data-stu-id="36c05-126">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="36c05-127">Otomatik bağlama yeniden yönlendirmelerini el ile etkinleştir</span><span class="sxs-lookup"><span data-stu-id="36c05-127">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="36c05-128">.NET Framework eski sürümlerini hedefleyen mevcut uygulamalarda veya yeniden yönlendirme eklemeniz için otomatik olarak sorulmayan durumlarda otomatik bağlama yeniden yönlendirmelerini etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36c05-128">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="36c05-129">Framework 'ün daha yeni bir sürümünü hedefliyorsanız, ancak otomatik olarak yeniden yönlendirme eklemek isteyip istemediğiniz sorulduğunda, derlemeleri yeniden eşlemek için büyük olasılıkla derleme çıkışı alacaksınız.</span><span class="sxs-lookup"><span data-stu-id="36c05-129">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="36c05-130">Aşağıdaki yöntemlerden birini kullanarak, proje dosyasını düzenlenmek üzere açın:</span><span class="sxs-lookup"><span data-stu-id="36c05-130">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="36c05-131">Visual Studio 'da **Çözüm Gezgini**' de projeyi seçin ve sonra kısayol menüsünden **klasörü dosya Gezgini 'nde aç** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="36c05-131">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="36c05-132">Dosya Gezgini 'nde, proje (. csproj veya. vbproj) dosyasını bulun ve Not defteri 'nde açın.</span><span class="sxs-lookup"><span data-stu-id="36c05-132">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="36c05-133">Visual Studio 'da, **Çözüm Gezgini**, projeye sağ tıklayın ve **Projeyi Kaldır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="36c05-133">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="36c05-134">Kaldırılmış projeyi yeniden sağ tıklatın ve ardından **Düzenle [ProjectName. csproj]** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="36c05-134">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="36c05-135">Aşağıdaki öğeyi ilk yapılandırma özellik grubuna ekleyin ( \<PropertyGroup> etiketinin altına):</span><span class="sxs-lookup"><span data-stu-id="36c05-135">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="36c05-136">Aşağıda, ekli öğe içeren örnek bir proje dosyası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="36c05-136">The following shows an example project file with the element inserted:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project ToolsVersion="12.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
     <PropertyGroup>
       <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
       <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
       <ProjectGuid>{123334}</ProjectGuid>
       ...
       <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
     </PropertyGroup>
     ...
   </Project>
   ```

3. <span data-ttu-id="36c05-137">Uygulamalarınızı derleyin.</span><span class="sxs-lookup"><span data-stu-id="36c05-137">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="36c05-138">Web uygulamalarında otomatik bağlama yeniden yönlendirmelerini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="36c05-138">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="36c05-139">Otomatik bağlama yeniden yönlendirmeleri, web uygulamaları için farklı şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="36c05-139">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="36c05-140">Kaynak yapılandırma (**web.config**) dosyasının Web uygulamaları için değiştirilmesi gerektiğinden, bağlama yeniden yönlendirmeleri yapılandırma dosyasına otomatik olarak eklenmez.</span><span class="sxs-lookup"><span data-stu-id="36c05-140">Because the source configuration (**web.config**) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="36c05-141">Ancak Visual Studio, bağlama çakışmalarını size bildirir ve çakışmaları çözümlemek için bağlama yeniden yönlendirmeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36c05-141">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="36c05-142">Her zaman bağlama yeniden yönlendirmeleri eklemeniz istentiğinden, bir Web uygulaması için bu özelliği açıkça devre dışı bırakmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="36c05-142">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="36c05-143">Bir **web.config** dosyasına bağlama yeniden yönlendirmeleri eklemek için:</span><span class="sxs-lookup"><span data-stu-id="36c05-143">To add binding redirects to a **web.config** file:</span></span>

1. <span data-ttu-id="36c05-144">Visual Studio'da uygulamayı derleyin ve yapı uyarılarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="36c05-144">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="36c05-145">![Derleme başvurusu çakışmaları için derleme uyarısı](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="36c05-145">![Build warning for assembly reference conflicts](./media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="36c05-146">Derleme bağlama çakışmaları varsa bir uyarı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="36c05-146">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="36c05-147">Uyarıya çift tıklayın veya uyarıyı seçin ve **ENTER**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="36c05-147">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="36c05-148">Kaynak **web.config** dosyasına gerekli bağlama yeniden yönlendirmelerini otomatik olarak eklemenize olanak sağlayan bir iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="36c05-148">A dialog box that enables you to automatically add the necessary binding redirects to the source **web.config** file appears.</span></span>

   <span data-ttu-id="36c05-149">![Bağlama yeniden yönlendirme izni iletişim kutusu](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="36c05-149">![Binding redirect permission dialog](./media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="36c05-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36c05-150">See also</span></span>

- [<span data-ttu-id="36c05-151">\<bindingRedirect>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="36c05-151">\<bindingRedirect> Element</span></span>](./file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="36c05-152">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="36c05-152">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
