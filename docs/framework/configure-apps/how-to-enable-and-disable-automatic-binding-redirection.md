---
title: Etkinleştirmek veya devre dışı otomatik bağlama yeniden yönlendirmeleri
ms.date: 10/30/2018
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 284c2a08f2b78d2c6a1ab9752a3f2283e87fd734
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50980839"
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="def38-102">Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="def38-102">How to: Enable and Disable Automatic Binding Redirection</span></span>

<span data-ttu-id="def38-103">Uygulamaları Visual Studio'da hedefleyen derleme yaparken [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ve sonraki sürümlerinde, bağlama yönlendirmeleri, derleme birleştiriciyi geçersiz kılmak için uygulama yapılandırma dosyasına otomatik olarak da eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="def38-103">When you compile apps in Visual Studio that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions, binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="def38-104">Uygulamanız veya bileşenleri, aynı derlemenin birden çok sürümüne başvurursa, uygulamanızın yapılandırma dosyasında bağlama yeniden yönlendirmelerini el ile belirtseniz de, bağlama yeniden yönlendirmeleri eklenir.</span><span class="sxs-lookup"><span data-stu-id="def38-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="def38-105">Otomatik bağlama yeniden yönlendirme özelliği hedefleyen Masaüstü uygulamaları ve web uygulamalarını etkiler [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] veya sonraki bir sürüm davranış web uygulaması için biraz farklı olmasına karşın.</span><span class="sxs-lookup"><span data-stu-id="def38-105">The automatic binding redirection feature affects desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] or a later version, although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="def38-106">Bu önceki sürümlerini hedefleyen .NET Framework'ün var olan uygulamaların bulunduğu ya da bağlama yeniden yönlendirmelerini el ile oluşturmak istiyorsanız bu özelliği devre dışı bırakabilirsiniz, otomatik bağlama yeniden yönlendirmesini etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="def38-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to manually author binding redirects.</span></span>

## <a name="disable-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="def38-107">Masaüstü uygulamalarında otomatik bağlama yeniden yönlendirmelerini devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="def38-107">Disable automatic binding redirects in desktop apps</span></span>

<span data-ttu-id="def38-108">Otomatik bağlama yeniden yönlendirmeleri hedefleyen Windows Masaüstü uygulamaları için varsayılan olarak etkin [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ve sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="def38-108">Automatic binding redirects are enabled by default for Windows desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="def38-109">Çıktı yapılandırma için bağlama yeniden yönlendirmeleri eklenir (**app.config**) dosya uygulama derlendiğinde ve aksi halde yer alabilen Birleştirici derlemesini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="def38-109">The binding redirects are added to the output configuration (**app.config**) file when the app is compiled and override the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="def38-110">Kaynak **app.config** dosya değiştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="def38-110">The source **app.config** file is not modified.</span></span> <span data-ttu-id="def38-111">Uygulama için proje dosyasını değiştirerek veya bir onay kutusu Visual Studio Proje özelliklerinde seçimini tarafından bu özelliği devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="def38-111">You can disable this feature by modifying the project file for the app or by deselecting a checkbox in the project's properties in Visual Studio.</span></span>

### <a name="disable-through-project-properties"></a><span data-ttu-id="def38-112">Proje özellikleri devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="def38-112">Disable through project properties</span></span>

<span data-ttu-id="def38-113">Visual Studio 2017 sürüm 15.7 veya sonraki bir sürümü varsa, otomatik bağlama yeniden yönlendirmeleri projenin özellik sayfalarındaki kolayca devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="def38-113">If you have Visual Studio 2017 version 15.7 or later, you can easily disable autogenerated binding redirects in the project's property pages.</span></span>

1. <span data-ttu-id="def38-114">Projeye sağ **Çözüm Gezgini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="def38-114">Right-click the project in **Solution Explorer** and select **Properties**.</span></span>

2. <span data-ttu-id="def38-115">Üzerinde **uygulama** sayfasında, onay kutusunu temizleyin **otomatik oluştur bağlama yönlendirmeleri** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="def38-115">On the **Application** page, uncheck the **Auto-generate binding redirects** option.</span></span>

3. <span data-ttu-id="def38-116">Tuşuna **Ctrl**+**S** yapılan değişiklik kaydedilemiyor.</span><span class="sxs-lookup"><span data-stu-id="def38-116">Press **Ctrl**+**S** to save the change.</span></span>

### <a name="disable-manually-in-the-project-file"></a><span data-ttu-id="def38-117">Proje dosyasında el ile devre dışı</span><span class="sxs-lookup"><span data-stu-id="def38-117">Disable manually in the project file</span></span>

1. <span data-ttu-id="def38-118">Aşağıdaki yöntemlerden birini kullanarak düzenlemek için proje dosyasını açın:</span><span class="sxs-lookup"><span data-stu-id="def38-118">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="def38-119">Visual Studio'da projeye seçin **Çözüm Gezgini**ve ardından **klasörü dosya Gezgini'nde Aç** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="def38-119">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="def38-120">Dosya Gezgini'nde, proje (.csproj veya .vbproj) dosyasını bulun ve Not Defteri'nde açın.</span><span class="sxs-lookup"><span data-stu-id="def38-120">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="def38-121">Visual Studio içinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **projeyi**.</span><span class="sxs-lookup"><span data-stu-id="def38-121">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="def38-122">Yüklenmemiş proje tekrar sağ tıklayın ve ardından **[projectname.csproj] Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="def38-122">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="def38-123">Proje dosyasında aşağıdaki özellik girdisini bulun:</span><span class="sxs-lookup"><span data-stu-id="def38-123">In the project file, find the following property entry:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

3. <span data-ttu-id="def38-124">Değişiklik `true` için `false`:</span><span class="sxs-lookup"><span data-stu-id="def38-124">Change `true` to `false`:</span></span>

   ```xml
   <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>
   ```

## <a name="enable-automatic-binding-redirects-manually"></a><span data-ttu-id="def38-125">Otomatik bağlama yeniden yönlendirmelerini el ile etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="def38-125">Enable automatic binding redirects manually</span></span>

<span data-ttu-id="def38-126">Bu eski sürümlerini hedefleyen .NET Framework'ün veya burada, otomatik olarak yeniden yönlendirme eklemeniz istenir durumlarda var olan uygulamalarda otomatik bağlama yeniden yönlendirmelerini etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="def38-126">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you're not automatically prompted to add a redirect.</span></span> <span data-ttu-id="def38-127">Framework'ün daha yeni bir sürümü hedefleme, ancak otomatik olarak yeniden yönlendirmeye eklemek için istenmiyor, büyük olasılıkla derlemeleri yeniden eşleme öneren yapı çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="def38-127">If you're targeting a newer version of the framework but do not get automatically prompted to add a redirect, you'll likely get build output that suggests you remap assemblies.</span></span>

1. <span data-ttu-id="def38-128">Aşağıdaki yöntemlerden birini kullanarak düzenlemek için proje dosyasını açın:</span><span class="sxs-lookup"><span data-stu-id="def38-128">Open the project file for editing using one of the following methods:</span></span>

   - <span data-ttu-id="def38-129">Visual Studio'da projeye seçin **Çözüm Gezgini**ve ardından **klasörü dosya Gezgini'nde Aç** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="def38-129">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span> <span data-ttu-id="def38-130">Dosya Gezgini'nde, proje (.csproj veya .vbproj) dosyasını bulun ve Not Defteri'nde açın.</span><span class="sxs-lookup"><span data-stu-id="def38-130">In File Explorer, find the project (.csproj or .vbproj) file and open it in Notepad.</span></span>
   - <span data-ttu-id="def38-131">Visual Studio içinde **Çözüm Gezgini**, projeye sağ tıklayıp seçin **projeyi**.</span><span class="sxs-lookup"><span data-stu-id="def38-131">In Visual Studio, in **Solution Explorer**, right-click the project and choose **Unload Project**.</span></span> <span data-ttu-id="def38-132">Yüklenmemiş proje tekrar sağ tıklayın ve ardından **[projectname.csproj] Düzenle**.</span><span class="sxs-lookup"><span data-stu-id="def38-132">Right-click the unloaded project again, and then choose **Edit [projectname.csproj]**.</span></span>

2. <span data-ttu-id="def38-133">Şu öğe için ilk yapılandırma özellik grubuna ekleyin (altında \<PropertyGroup > etiketinin):</span><span class="sxs-lookup"><span data-stu-id="def38-133">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>

   ```xml
   <AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>
   ```

   <span data-ttu-id="def38-134">Aşağıdaki örnek, bir proje dosyasını eklenen öğeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="def38-134">The following shows an example project file with the element inserted:</span></span>

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

3. <span data-ttu-id="def38-135">Uygulamalarınızı derleyin.</span><span class="sxs-lookup"><span data-stu-id="def38-135">Compile your app.</span></span>

## <a name="enable-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="def38-136">Web uygulamalarında otomatik bağlama yeniden yönlendirmelerini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="def38-136">Enable automatic binding redirects in web apps</span></span>

<span data-ttu-id="def38-137">Otomatik bağlama yeniden yönlendirmeleri, web uygulamaları için farklı şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="def38-137">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="def38-138">Çünkü kaynak yapılandırma (**web.config**) dosyası için web apps değiştirilmelidir, bağlama yeniden yönlendirmelerini otomatik yapılandırma dosyasına eklenmez.</span><span class="sxs-lookup"><span data-stu-id="def38-138">Because the source configuration (**web.config**) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="def38-139">Ancak Visual Studio, bağlama çakışmalarını size bildirir ve çakışmaları çözümlemek için bağlama yeniden yönlendirmeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="def38-139">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="def38-140">Her zaman bağlama yeniden yönlendirmeleri eklemeniz istenir çünkü bir web uygulaması için bu özelliği açıkça devre dışı bırakmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="def38-140">Because you're always prompted to add binding redirects, you don't need to explicitly disable this feature for a web app.</span></span>

<span data-ttu-id="def38-141">İçin bağlama yeniden yönlendirmeleri eklemek için bir **web.config** dosyası:</span><span class="sxs-lookup"><span data-stu-id="def38-141">To add binding redirects to a **web.config** file:</span></span>

1. <span data-ttu-id="def38-142">Visual Studio'da uygulamayı derleyin ve yapı uyarılarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="def38-142">In Visual Studio, compile the app, and check for build warnings.</span></span>

   <span data-ttu-id="def38-143">![Derleme uyarısı bütünleştirilmiş kod başvurusu çakışmaları](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="def38-143">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>

2. <span data-ttu-id="def38-144">Derleme bağlama çakışmaları varsa bir uyarı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="def38-144">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="def38-145">Uyarıyı çift tıklatın veya uyarı seçip ENTER tuşuna **Enter**.</span><span class="sxs-lookup"><span data-stu-id="def38-145">Double-click the warning, or select the warning and press **Enter**.</span></span>

   <span data-ttu-id="def38-146">Gerekli bağlama otomatik olarak eklemenize olanak sağlayan bir iletişim kutusu kaynağına yönlendiren **web.config** dosyası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="def38-146">A dialog box that enables you to automatically add the necessary binding redirects to the source **web.config** file appears.</span></span>

   <span data-ttu-id="def38-147">![Bağlama yeniden yönlendirmeye izin iletişim](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="def38-147">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>

## <a name="see-also"></a><span data-ttu-id="def38-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="def38-148">See also</span></span>

- [<span data-ttu-id="def38-149">\<bindingRedirect > öğesi</span><span class="sxs-lookup"><span data-stu-id="def38-149">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="def38-150">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="def38-150">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
