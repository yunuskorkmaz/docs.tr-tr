---
title: "Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 5fca42f3-bdce-4b81-a704-61e42c89d3ba
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 83b004934c303c95bdc4e6edb6031a86e2b1a6ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-and-disable-automatic-binding-redirection"></a><span data-ttu-id="24b8e-102">Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="24b8e-102">How to: Enable and Disable Automatic Binding Redirection</span></span>
<span data-ttu-id="24b8e-103">İle başlayarak [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], hedefleyen uygulamalar derlediğinizde [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], bağlama yeniden yönlendirmeleri otomatik olarak eklenebilir birleştirici derleme geçersiz kılmak için uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="24b8e-103">Starting with [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], when you compile apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], binding redirects may be automatically added to the app configuration file to override assembly unification.</span></span> <span data-ttu-id="24b8e-104">Uygulamanız veya bileşenleri, aynı derlemenin birden çok sürümüne başvurursa, uygulamanızın yapılandırma dosyasında bağlama yeniden yönlendirmelerini el ile belirtseniz de, bağlama yeniden yönlendirmeleri eklenir.</span><span class="sxs-lookup"><span data-stu-id="24b8e-104">Binding redirects are added if your app or its components reference more than one version of the same assembly, even if you manually specify binding redirects in the configuration file for your app.</span></span> <span data-ttu-id="24b8e-105">Otomatik bağlama yeniden yönlendirme özelliğini hedefleyen geleneksel masaüstü uygulamaları ve web uygulamaları etkiler [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], davranışı için bir web uygulaması biraz farklı olmasına rağmen.</span><span class="sxs-lookup"><span data-stu-id="24b8e-105">The automatic binding redirection feature affects traditional desktop apps and web apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], although the behavior is slightly different for a web app.</span></span> <span data-ttu-id="24b8e-106">.NET Framework'ün önceki sürümlerini hedefleyen var olan uygulamalarınız varsa otomatik bağlama yeniden yönlendirmesini etkinleştirebilir veya el ile yazılan bağlama yeniden yönlendirmelerini tutmak istiyorsanız bu özelliği devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24b8e-106">You can enable automatic binding redirection if you have existing apps that target previous versions of the .NET Framework, or you can disable this feature if you want to keep manually authored binding redirects.</span></span>  
  
## <a name="disabling-automatic-binding-redirects-in-desktop-apps"></a><span data-ttu-id="24b8e-107">Masaüstü uygulamalarında yönlendiren otomatik bağlama devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="24b8e-107">Disabling automatic binding redirects in desktop apps</span></span>  
 <span data-ttu-id="24b8e-108">Otomatik bağlama yeniden yönlendirmeleri hedef geleneksel masaüstü uygulamaları için varsayılan olarak etkin [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ve sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="24b8e-108">Automatic binding redirects are enabled by default for traditional desktop apps that target the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] and later versions.</span></span> <span data-ttu-id="24b8e-109">Bağlama yeniden yönlendirmeleri, uygulama derlendiğinde ve aksi takdirde gerçekleşebilecek derleme birleştirmeyi geçersiz kıldığında çıktı yapılandırma dosyasına (app.config) eklenir.</span><span class="sxs-lookup"><span data-stu-id="24b8e-109">The binding redirects are added to the output configuration (app.config) file when the app is compiled and overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="24b8e-110">Kaynak app.config dosyası değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="24b8e-110">The source app.config file is not modified.</span></span> <span data-ttu-id="24b8e-111">Uygulama için proje dosyasını değiştirerek, bu özelliği devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24b8e-111">You can disable this feature by modifying the project file for the app.</span></span>  
  
#### <a name="to-disable-automatic-binding-redirects"></a><span data-ttu-id="24b8e-112">Otomatik bağlama yeniden yönlendirmelerini devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="24b8e-112">To disable automatic binding redirects</span></span>  
  
1.  <span data-ttu-id="24b8e-113">Visual Studio'da projeye seçin **Çözüm Gezgini**ve ardından **dosya Gezgini'nde klasör Aç** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="24b8e-113">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="24b8e-114">Dosya Gezgini'nde, proje (.csproj veya .vbproj) dosyasını bulun ve Not Defteri'nde açın.</span><span class="sxs-lookup"><span data-stu-id="24b8e-114">In File Explorer, find the project (.csproj or .vbproj) file, and open it in Notepad.</span></span>  
  
3.  <span data-ttu-id="24b8e-115">Proje dosyasında aşağıdaki özellik girdisini bulun:</span><span class="sxs-lookup"><span data-stu-id="24b8e-115">In the project file, find the following property entry:</span></span>  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
4.  <span data-ttu-id="24b8e-116">Değişiklik `true` için `false`:</span><span class="sxs-lookup"><span data-stu-id="24b8e-116">Change `true` to `false`:</span></span>  
  
     `<AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>`  
  
## <a name="enabling-automatic-binding-redirects-manually"></a><span data-ttu-id="24b8e-117">Otomatik bağlama etkinleştirme el ile yeniden yönlendirir</span><span class="sxs-lookup"><span data-stu-id="24b8e-117">Enabling automatic binding redirects manually</span></span>  
 <span data-ttu-id="24b8e-118">Bu hedef eski sürümlerini .NET Framework'ün ya da nerede, otomatik olarak bir yeniden yönlendirme eklemeye istenmez durumlarda varolan uygulamalarda otomatik bağlama yeniden yönlendirmeleri etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24b8e-118">You can enable automatic binding redirects in existing apps that target older versions of the .NET Framework, or in cases where you are not automatically prompted to add a redirect.</span></span> <span data-ttu-id="24b8e-119">Framework'ün daha yeni bir sürümünü hedefleme ancak otomatik olarak yeniden yönlendirme eklemek istenmedi derlemeleri yeniden eşleme öneren yapı çıktı olasılıkla alırsınız.</span><span class="sxs-lookup"><span data-stu-id="24b8e-119">If you are targeting a newer version of the framework but do not get automatically prompted to add a redirect, you will likely get   build output that suggests you remap assemblies.</span></span>  
  
#### <a name="to-manually-add-an-automatic-binding-redirect-property"></a><span data-ttu-id="24b8e-120">Bir otomatik bağlama yeniden yönlendirme özelliğini el ile eklemek için</span><span class="sxs-lookup"><span data-stu-id="24b8e-120">To manually add an automatic binding redirect property</span></span>  
  
1.  <span data-ttu-id="24b8e-121">Visual Studio'da projeye seçin **Çözüm Gezgini**ve ardından **dosya Gezgini'nde klasör Aç** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="24b8e-121">In Visual Studio, select the project in **Solution Explorer**, and then choose **Open Folder in File Explorer** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="24b8e-122">Dosya Gezgini'nde, proje (.csproj veya .vbproj) dosyasını bulun ve Not Defteri'nde açın.</span><span class="sxs-lookup"><span data-stu-id="24b8e-122">In File Explorer, find the project (.csproj or .vbproj) file, and open it in Notepad.</span></span>  
  
3.  <span data-ttu-id="24b8e-123">İlk Yapılandırma özelliği grubuna aşağıdaki öğeyi ekleyin (altında \<PropertyGroup > etiketi):</span><span class="sxs-lookup"><span data-stu-id="24b8e-123">Add the following element to the first configuration property group (under the \<PropertyGroup> tag):</span></span>  
  
     `<AutoGenerateBindingRedirects>true</AutoGenerateBindingRedirects>`  
  
     <span data-ttu-id="24b8e-124">Aşağıdaki örnek proje dosyası eklenen öğeyle gösterir.</span><span class="sxs-lookup"><span data-stu-id="24b8e-124">The following shows an example project file with the element inserted.</span></span>  
  
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
  
4.  <span data-ttu-id="24b8e-125">Uygulamalarınızı derleyin.</span><span class="sxs-lookup"><span data-stu-id="24b8e-125">Compile your app.</span></span>  
  
## <a name="enabling-automatic-binding-redirects-in-web-apps"></a><span data-ttu-id="24b8e-126">Web uygulamalarında otomatik bağlama yeniden yönlendirmelerini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="24b8e-126">Enabling automatic binding redirects in web apps</span></span>  
 <span data-ttu-id="24b8e-127">Otomatik bağlama yeniden yönlendirmeleri, web uygulamaları için farklı şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="24b8e-127">Automatic binding redirects are implemented differently for web apps.</span></span> <span data-ttu-id="24b8e-128">Kaynak yapılandırma (web.config) dosyasının web uygulamaları için değiştirilmesi gerektiğinden, bağlama yeniden yönlendirmeleri, yapılandırma dosyasına otomatik olarak eklenmez.</span><span class="sxs-lookup"><span data-stu-id="24b8e-128">Because the source configuration (web.config) file must be modified for web apps, binding redirects are not automatically added to the configuration file.</span></span> <span data-ttu-id="24b8e-129">Ancak Visual Studio, bağlama çakışmalarını size bildirir ve çakışmaları çözümlemek için bağlama yeniden yönlendirmeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24b8e-129">However, Visual Studio notifies you of binding conflicts, and you can add binding redirects to resolve the conflicts.</span></span> <span data-ttu-id="24b8e-130">Her zaman bağlama yeniden yönlendirmeleri eklemeniz istendiğinden, web uygulaması için bu özelliği açıkça devre dışı bırakmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="24b8e-130">Because you are always prompted to add binding redirects, you do not need to explicitly disable this feature for a web app.</span></span>  
  
#### <a name="to-add-binding-redirects-to-a-webconfig-file"></a><span data-ttu-id="24b8e-131">Bir web.config dosyasına bağlama yeniden yönlendirmeleri eklemek için</span><span class="sxs-lookup"><span data-stu-id="24b8e-131">To add binding redirects to a web.config file</span></span>  
  
1.  <span data-ttu-id="24b8e-132">Visual Studio'da uygulamayı derleyin ve yapı uyarılarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="24b8e-132">In Visual Studio, compile the app, and check for build warnings.</span></span>  
  
     <span data-ttu-id="24b8e-133">![Derleme başvurusu çakışmaları için uyarı yapı](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span><span class="sxs-lookup"><span data-stu-id="24b8e-133">![Build warning for assembly reference conflicts](../../../docs/framework/configure-apps/media/clr-assemblyrefwarning.png "CLR_AssemblyRefWarning")</span></span>  
  
2.  <span data-ttu-id="24b8e-134">Derleme bağlama çakışmaları varsa bir uyarı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="24b8e-134">If there are assembly binding conflicts, a warning appears.</span></span> <span data-ttu-id="24b8e-135">Uyarıyı çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="24b8e-135">Double-click the warning.</span></span> <span data-ttu-id="24b8e-136">(Klavye: uyarı seçip tuşuna **Enter**.)</span><span class="sxs-lookup"><span data-stu-id="24b8e-136">(Keyboard: Select the warning and press **Enter**.)</span></span>  
  
     <span data-ttu-id="24b8e-137">Kaynak web.config dosyasına gerekli içeriğe yeniden yönlendirmelerini otomatik olarak eklemenize olanak sağlayan bir iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="24b8e-137">A dialog box that enables you to automatically add the necessary binding redirects to the source web.config file appears.</span></span>  
  
     <span data-ttu-id="24b8e-138">![Bağlama yeniden yönlendirme izni iletişim](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span><span class="sxs-lookup"><span data-stu-id="24b8e-138">![Binding redirect permission dialog](../../../docs/framework/configure-apps/media/clr-addbindingredirect.png "CLR_AddBindingRedirect")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b8e-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24b8e-139">See Also</span></span>  
 [<span data-ttu-id="24b8e-140">\<bindingRedirect > öğesi</span><span class="sxs-lookup"><span data-stu-id="24b8e-140">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [<span data-ttu-id="24b8e-141">Derleme sürümlerini yönlendirme</span><span class="sxs-lookup"><span data-stu-id="24b8e-141">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
