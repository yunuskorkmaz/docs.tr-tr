---
title: .NET Framework ve .NET Core arasındaki farklar
description: Windows Presentation Foundation (WPF) ve .NET Core WPF'nin .NET Framework uygulaması arasındaki farkları açıklar. Uygulamanızı geçirerken, bu uyumsuzlukları göz önünde bulundurmalısınız.
author: thraka
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 341e576f17c522fbcbb9c417176e9d4a13ab1b18
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82072209"
---
# <a name="differences-in-wpf"></a><span data-ttu-id="d993d-104">WPF'deki farklar</span><span class="sxs-lookup"><span data-stu-id="d993d-104">Differences in WPF</span></span>

<span data-ttu-id="d993d-105">Bu makalede, .NET Core ve .NET Framework'de Windows Presentation Foundation (WPF) arasındaki farklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d993d-105">This article describes the differences between Windows Presentation Foundation (WPF) on .NET Core and .NET Framework.</span></span> <span data-ttu-id="d993d-106">.NET Core için WPF, .NET Framework kaynak kodu için orijinal WPF'den çatallanmış açık [kaynak](https://github.com/dotnet/wpf) çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="d993d-106">WPF for .NET Core is an [open-source framework](https://github.com/dotnet/wpf) forked from the original WPF for .NET Framework source code.</span></span>

<span data-ttu-id="d993d-107">.NET Framework'ün .NET Core'un desteklemediği birkaç özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="d993d-107">There are a few features of .NET Framework that .NET Core doesn't support.</span></span> <span data-ttu-id="d993d-108">Desteklenmeyen teknolojiler hakkında daha fazla bilgi için [.NET Core'da bulunmayan .NET Framework teknolojilerine](../../core/porting/net-framework-tech-unavailable.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d993d-108">For more information on unsupported technologies, see [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a><span data-ttu-id="d993d-109">SDK tarzı projeler</span><span class="sxs-lookup"><span data-stu-id="d993d-109">SDK-style projects</span></span>

<span data-ttu-id="d993d-110">.NET Core, SDK tarzı proje dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d993d-110">.NET Core uses SDK-style project files.</span></span> <span data-ttu-id="d993d-111">Bu proje dosyaları Visual Studio tarafından yönetilen geleneksel .NET Framework proje dosyalarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d993d-111">These project files are different from the traditional .NET Framework project files managed by Visual Studio.</span></span> <span data-ttu-id="d993d-112">.NET Framework WPF uygulamalarınızı .NET Core'a geçirmek için projelerinizi dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d993d-112">To migrate your .NET Framework WPF apps to .NET Core, you must convert your projects.</span></span> <span data-ttu-id="d993d-113">Daha fazla bilgi için [WPF uygulamalarını .NET Core 3.0'a geçirin.](convert-project-from-net-framework.md)</span><span class="sxs-lookup"><span data-stu-id="d993d-113">For more information, see [Migrate WPF apps to .NET Core 3.0](convert-project-from-net-framework.md).</span></span>

## <a name="nuget-package-references"></a><span data-ttu-id="d993d-114">NuPaket referansları alın</span><span class="sxs-lookup"><span data-stu-id="d993d-114">NuGet package references</span></span>

<span data-ttu-id="d993d-115">.NET Framework uygulamanız NuGet bağımlılıklarını *bir packages.config* dosyasında [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) listeliyorsa, biçime geçirin:</span><span class="sxs-lookup"><span data-stu-id="d993d-115">If your .NET Framework app lists its NuGet dependencies in a *packages.config* file, migrate to the [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) format:</span></span>

1. <span data-ttu-id="d993d-116">Visual Studio'da **Solution Explorer** bölmesini açın.</span><span class="sxs-lookup"><span data-stu-id="d993d-116">In Visual Studio, open the **Solution Explorer** pane.</span></span>
1. <span data-ttu-id="d993d-117">WPF projenizde **packagereference'a sağ tıkla.config** > **Migrate packages.config to PackageReference**.</span><span class="sxs-lookup"><span data-stu-id="d993d-117">In your WPF project, right-click **packages.config** > **Migrate packages.config to PackageReference**.</span></span>

![PackageReference'a yükseltme](media/differences-from-net-framework/package-reference-migration.png)

<span data-ttu-id="d993d-119">Hesaplanan üst düzey NuGet bağımlılıklarını gösteren ve hangi diğer NuGet paketlerinin en üst düzeye yükseltilmesi gerektiğini soran bir iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d993d-119">A dialog will appear showing calculated top-level NuGet dependencies and asking which other NuGet packages should be promoted to top level.</span></span> <span data-ttu-id="d993d-120">**Tamam'ı** seçin ve *packages.config* dosyası projeden kaldırılır ve `<PackageReference>` öğeler proje dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="d993d-120">Select **OK** and the *packages.config* file will be removed from the project and `<PackageReference>` elements will be added to the project file.</span></span>

<span data-ttu-id="d993d-121">Projeniz kullandığında, `<PackageReference>`paketler *paketler* paketler klasöründe yerel olarak depolanır, genel olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="d993d-121">When your project uses `<PackageReference>`, packages aren't stored locally in a *Packages* folder, they're stored globally.</span></span> <span data-ttu-id="d993d-122">Proje dosyasını açın `<Analyzer>` ve *Paketler* klasörüne yönlendirilen öğeleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d993d-122">Open the project file and remove any `<Analyzer>` elements that referred to the *Packages* folder.</span></span> <span data-ttu-id="d993d-123">Bu çözümleyiciler otomatik olarak NuGet paket başvurularına dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="d993d-123">These analyzers are automatically included with the NuGet package references.</span></span>

## <a name="code-access-security"></a><span data-ttu-id="d993d-124">Kod Erişimi Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d993d-124">Code Access Security</span></span>

<span data-ttu-id="d993d-125">Kod Erişim Güvenliği (CAS) .NET Core veya WPF tarafından .NET Core için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d993d-125">Code Access Security (CAS) is not supported by .NET Core or WPF for .NET Core.</span></span> <span data-ttu-id="d993d-126">CAS ile ilgili tüm işlevler tam güven varsayımı altında ele alının.</span><span class="sxs-lookup"><span data-stu-id="d993d-126">All CAS-related functionality is treated under the assumption of full-trust.</span></span> <span data-ttu-id="d993d-127">.NET Core için WPF, CAS ile ilgili kodu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d993d-127">WPF for .NET Core removes CAS-related code.</span></span> <span data-ttu-id="d993d-128">Bu tür deki çağrıların başarılı olduğundan emin olmak için bu tür lerin genel API yüzeyi hala mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="d993d-128">The public API surface of these types still exists to ensure that calls into these types succeed.</span></span>

<span data-ttu-id="d993d-129">Genel olarak tanımlanan CAS ile ilgili türler WPF derlemelerinden core .NET kitaplık derlemelerine taşındı.</span><span class="sxs-lookup"><span data-stu-id="d993d-129">Publicly defined CAS-related types were moved out of the WPF assemblies and into the Core .NET library assemblies.</span></span> <span data-ttu-id="d993d-130">WPF derlemeleri, taşınan türlerin yeni konumuna tür iletme kümesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d993d-130">The WPF assemblies have type-forwarding set to the new location of the moved types.</span></span>

| <span data-ttu-id="d993d-131">Kaynak derleme</span><span class="sxs-lookup"><span data-stu-id="d993d-131">Source assembly</span></span> | <span data-ttu-id="d993d-132">Hedef montaj</span><span class="sxs-lookup"><span data-stu-id="d993d-132">Target assembly</span></span> | <span data-ttu-id="d993d-133">Tür</span><span class="sxs-lookup"><span data-stu-id="d993d-133">Type</span></span>                |
| --------------- | --------------- | ------------------- |
| <span data-ttu-id="d993d-134">*WindowsBase.dll*</span><span class="sxs-lookup"><span data-stu-id="d993d-134">*WindowsBase.dll*</span></span> | <span data-ttu-id="d993d-135">*System.Security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="d993d-135">*System.Security.Permissions.dll*</span></span> | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| <span data-ttu-id="d993d-136">*Sistem.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="d993d-136">*System.Xaml.dll*</span></span> | <span data-ttu-id="d993d-137">*System.Security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="d993d-137">*System.Security.Permissions.dll*</span></span> | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| <span data-ttu-id="d993d-138">*Sistem.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="d993d-138">*System.Xaml.dll*</span></span> | <span data-ttu-id="d993d-139">*System.Windows.Extension.dll*</span><span class="sxs-lookup"><span data-stu-id="d993d-139">*System.Windows.Extension.dll*</span></span>    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> <span data-ttu-id="d993d-140">Taşıma sürtünmesini en aza indirmek için, aşağıdaki özelliklerle ilgili bilgilerin depolanması ve alınması `XamlAccessLevel` işlevi türde korunmuştur.</span><span class="sxs-lookup"><span data-stu-id="d993d-140">In order to minimize porting friction, the functionality for storing and retrieving information related to the following properties was retained in the `XamlAccessLevel` type.</span></span>
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a><span data-ttu-id="d993d-141">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="d993d-141">Next steps</span></span>

- [<span data-ttu-id="d993d-142">Bir .NET Framework WPF uygulamasını .NET Core'a nasıl ileteceklerini öğrenin.</span><span class="sxs-lookup"><span data-stu-id="d993d-142">Learn how to port a .NET Framework WPF app to .NET Core.</span></span>](convert-project-from-net-framework.md)
