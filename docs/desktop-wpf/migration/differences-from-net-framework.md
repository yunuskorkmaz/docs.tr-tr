---
title: .NET Framework ve .NET Core arasındaki farklılıklar
description: Windows Presentation Foundation (WPF) ve .NET Core WPF .NET Framework uygulama arasındaki farkları açıklar. Uygulamanızı geçirirken, bu uyumsuzlukları göz önünde bulundurmanız gerekir.
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
# <a name="differences-in-wpf"></a><span data-ttu-id="1abd3-104">WPF farkları</span><span class="sxs-lookup"><span data-stu-id="1abd3-104">Differences in WPF</span></span>

<span data-ttu-id="1abd3-105">Bu makalede, .NET Core ve .NET Framework Windows Presentation Foundation (WPF) arasındaki farklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1abd3-105">This article describes the differences between Windows Presentation Foundation (WPF) on .NET Core and .NET Framework.</span></span> <span data-ttu-id="1abd3-106">.NET Core için WPF, .NET Framework kaynak kodu için özgün WPF tarafından ele alınan [Açık kaynaklı bir çerçevedir](https://github.com/dotnet/wpf) .</span><span class="sxs-lookup"><span data-stu-id="1abd3-106">WPF for .NET Core is an [open-source framework](https://github.com/dotnet/wpf) forked from the original WPF for .NET Framework source code.</span></span>

<span data-ttu-id="1abd3-107">.NET Core 'un desteklemediği .NET Framework birkaç özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="1abd3-107">There are a few features of .NET Framework that .NET Core doesn't support.</span></span> <span data-ttu-id="1abd3-108">Desteklenmeyen teknolojiler hakkında daha fazla bilgi için bkz. [.NET Core 'da .NET Framework teknolojileri kullanılamıyor](../../core/porting/net-framework-tech-unavailable.md).</span><span class="sxs-lookup"><span data-stu-id="1abd3-108">For more information on unsupported technologies, see [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a><span data-ttu-id="1abd3-109">SDK stili projeler</span><span class="sxs-lookup"><span data-stu-id="1abd3-109">SDK-style projects</span></span>

<span data-ttu-id="1abd3-110">.NET Core, SDK stili proje dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1abd3-110">.NET Core uses SDK-style project files.</span></span> <span data-ttu-id="1abd3-111">Bu proje dosyaları, Visual Studio tarafından yönetilen geleneksel .NET Framework proje dosyalarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="1abd3-111">These project files are different from the traditional .NET Framework project files managed by Visual Studio.</span></span> <span data-ttu-id="1abd3-112">.NET Framework WPF uygulamalarınızı .NET Core 'a geçirmek için projelerinizi dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1abd3-112">To migrate your .NET Framework WPF apps to .NET Core, you must convert your projects.</span></span> <span data-ttu-id="1abd3-113">Daha fazla bilgi için bkz. [WPF uygulamalarını .NET Core 3,0 'ye geçirme](convert-project-from-net-framework.md).</span><span class="sxs-lookup"><span data-stu-id="1abd3-113">For more information, see [Migrate WPF apps to .NET Core 3.0](convert-project-from-net-framework.md).</span></span>

## <a name="nuget-package-references"></a><span data-ttu-id="1abd3-114">NuGet paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="1abd3-114">NuGet package references</span></span>

<span data-ttu-id="1abd3-115">.NET Framework uygulamanız, NuGet bağımlılıklarını bir *Packages. config* dosyasında listelediğinden şu [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) biçime geçin:</span><span class="sxs-lookup"><span data-stu-id="1abd3-115">If your .NET Framework app lists its NuGet dependencies in a *packages.config* file, migrate to the [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) format:</span></span>

1. <span data-ttu-id="1abd3-116">Visual Studio 'da **Çözüm Gezgini** bölmesini açın.</span><span class="sxs-lookup"><span data-stu-id="1abd3-116">In Visual Studio, open the **Solution Explorer** pane.</span></span>
1. <span data-ttu-id="1abd3-117">WPF projenizde **Packages. config** > Packages. config 'i**packagereference**' a geçirin.</span><span class="sxs-lookup"><span data-stu-id="1abd3-117">In your WPF project, right-click **packages.config** > **Migrate packages.config to PackageReference**.</span></span>

![PackageReference 'a yükseltme](media/differences-from-net-framework/package-reference-migration.png)

<span data-ttu-id="1abd3-119">Hesaplanan en üst düzey NuGet bağımlılıklarını gösteren bir iletişim kutusu görünür ve diğer NuGet paketlerinin en üst düzeye yükseltilmesi gerektiğini sorar.</span><span class="sxs-lookup"><span data-stu-id="1abd3-119">A dialog will appear showing calculated top-level NuGet dependencies and asking which other NuGet packages should be promoted to top level.</span></span> <span data-ttu-id="1abd3-120">**Tamam** ' ı seçtiğinizde, *Packages. config* dosyası projeden kaldırılacak ve `<PackageReference>` öğeler proje dosyasına eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="1abd3-120">Select **OK** and the *packages.config* file will be removed from the project and `<PackageReference>` elements will be added to the project file.</span></span>

<span data-ttu-id="1abd3-121">Projeniz kullandığında `<PackageReference>`, paketler yerel olarak bir *paketler* klasöründe depolanmaz.</span><span class="sxs-lookup"><span data-stu-id="1abd3-121">When your project uses `<PackageReference>`, packages aren't stored locally in a *Packages* folder, they're stored globally.</span></span> <span data-ttu-id="1abd3-122">Proje dosyasını açın ve *paketler* klasörüne başvuruda `<Analyzer>` bulunan tüm öğeleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1abd3-122">Open the project file and remove any `<Analyzer>` elements that referred to the *Packages* folder.</span></span> <span data-ttu-id="1abd3-123">Bu çözümleyiciler, NuGet paket başvurularına otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="1abd3-123">These analyzers are automatically included with the NuGet package references.</span></span>

## <a name="code-access-security"></a><span data-ttu-id="1abd3-124">Kod Erişimi Güvenliği</span><span class="sxs-lookup"><span data-stu-id="1abd3-124">Code Access Security</span></span>

<span data-ttu-id="1abd3-125">.NET Core için .NET Core veya WPF tarafından kod erişim güvenliği (CAS) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1abd3-125">Code Access Security (CAS) is not supported by .NET Core or WPF for .NET Core.</span></span> <span data-ttu-id="1abd3-126">Tüm CA 'larla ilgili işlevler tam güven varsayımına göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1abd3-126">All CAS-related functionality is treated under the assumption of full-trust.</span></span> <span data-ttu-id="1abd3-127">.NET Core için WPF, CA ile ilgili kodu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1abd3-127">WPF for .NET Core removes CAS-related code.</span></span> <span data-ttu-id="1abd3-128">Bu türlerin ortak API 'SI yüzeyi, bu türlere yapılan çağrıların başarılı olduğundan emin olmak için hala var.</span><span class="sxs-lookup"><span data-stu-id="1abd3-128">The public API surface of these types still exists to ensure that calls into these types succeed.</span></span>

<span data-ttu-id="1abd3-129">Ortak olarak tanımlanan CA 'larla ilgili türler WPF derlemelerinden ve çekirdek .NET kitaplığı derlemelerinden taşındı.</span><span class="sxs-lookup"><span data-stu-id="1abd3-129">Publicly defined CAS-related types were moved out of the WPF assemblies and into the Core .NET library assemblies.</span></span> <span data-ttu-id="1abd3-130">WPF derlemelerinin tür iletme türü, taşınan türlerin yeni konumuna ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1abd3-130">The WPF assemblies have type-forwarding set to the new location of the moved types.</span></span>

| <span data-ttu-id="1abd3-131">Kaynak derleme</span><span class="sxs-lookup"><span data-stu-id="1abd3-131">Source assembly</span></span> | <span data-ttu-id="1abd3-132">Hedef derleme</span><span class="sxs-lookup"><span data-stu-id="1abd3-132">Target assembly</span></span> | <span data-ttu-id="1abd3-133">Tür</span><span class="sxs-lookup"><span data-stu-id="1abd3-133">Type</span></span>                |
| --------------- | --------------- | ------------------- |
| <span data-ttu-id="1abd3-134">*WindowsBase. dll*</span><span class="sxs-lookup"><span data-stu-id="1abd3-134">*WindowsBase.dll*</span></span> | <span data-ttu-id="1abd3-135">*System. Security. Permissions. dll*</span><span class="sxs-lookup"><span data-stu-id="1abd3-135">*System.Security.Permissions.dll*</span></span> | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| <span data-ttu-id="1abd3-136">*System. xaml. dll*</span><span class="sxs-lookup"><span data-stu-id="1abd3-136">*System.Xaml.dll*</span></span> | <span data-ttu-id="1abd3-137">*System. Security. Permissions. dll*</span><span class="sxs-lookup"><span data-stu-id="1abd3-137">*System.Security.Permissions.dll*</span></span> | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| <span data-ttu-id="1abd3-138">*System. xaml. dll*</span><span class="sxs-lookup"><span data-stu-id="1abd3-138">*System.Xaml.dll*</span></span> | <span data-ttu-id="1abd3-139">*System. Windows. Extension. dll*</span><span class="sxs-lookup"><span data-stu-id="1abd3-139">*System.Windows.Extension.dll*</span></span>    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> <span data-ttu-id="1abd3-140">Savunma savunma durumunu en aza indirmek için, aşağıdaki özelliklerle ilgili bilgileri depolama ve alma işlevleri `XamlAccessLevel` türünde tutulur.</span><span class="sxs-lookup"><span data-stu-id="1abd3-140">In order to minimize porting friction, the functionality for storing and retrieving information related to the following properties was retained in the `XamlAccessLevel` type.</span></span>
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a><span data-ttu-id="1abd3-141">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1abd3-141">Next steps</span></span>

- [<span data-ttu-id="1abd3-142">.NET Framework WPF uygulamasının .NET Core 'a nasıl bağlantı sağladığını öğrenin.</span><span class="sxs-lookup"><span data-stu-id="1abd3-142">Learn how to port a .NET Framework WPF app to .NET Core.</span></span>](convert-project-from-net-framework.md)
