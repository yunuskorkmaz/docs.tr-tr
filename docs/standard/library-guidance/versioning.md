---
title: Sürüm ve .NET kitaplıkları
description: .NET kitaplıklarını sürümleme için en iyi uygulama önerileri.
ms.date: 12/10/2018
ms.openlocfilehash: a274410714791e2790da0e3deb2a595390ee9389
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400402"
---
# <a name="versioning"></a><span data-ttu-id="86698-103">Sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="86698-103">Versioning</span></span>

<span data-ttu-id="86698-104">Bir yazılım kitaplığı nadiren sürüm 1.0 tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="86698-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="86698-105">İyi kitaplıklar zaman içinde gelişir, özellikler ekleyerek, hataları gidererek ve performansı artırarak.</span><span class="sxs-lookup"><span data-stu-id="86698-105">Good libraries evolve over time, adding features, fixing bugs and improving performance.</span></span> <span data-ttu-id="86698-106">Varolan kullanıcıları bozmadan, her sürümde ek değer sağlayan bir .NET kitaplığın yeni sürümlerini serbest bırakabilirsiniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="86698-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="86698-107">Yeni değişiklikler</span><span class="sxs-lookup"><span data-stu-id="86698-107">Breaking changes</span></span>

<span data-ttu-id="86698-108">Sürümler arasındaki son kesme değişikliklerini işleme hakkında bilgi [için](./breaking-changes.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="86698-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="86698-109">Sürüm numaraları</span><span class="sxs-lookup"><span data-stu-id="86698-109">Version numbers</span></span>

<span data-ttu-id="86698-110">.NET kitaplığı bir sürümü belirtmenin birçok yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="86698-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="86698-111">Bu sürümler en önemlileridir:</span><span class="sxs-lookup"><span data-stu-id="86698-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="86698-112">NuGet paket sürümü</span><span class="sxs-lookup"><span data-stu-id="86698-112">NuGet package version</span></span>

<span data-ttu-id="86698-113">[NuGet paket sürümü](/nuget/reference/package-versioning) Visual Studio NuGet paket yöneticisi NuGet.org'da görüntülenir ve paket kullanıldığında kaynak koduna eklenir.</span><span class="sxs-lookup"><span data-stu-id="86698-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="86698-114">NuGet paket sürümü, kullanıcıların sık göreceği sürüm numarasıdır ve kullandıkları kitaplığın sürümühakkında konuştukları zaman bu sürüme atıfta bulunurlar.</span><span class="sxs-lookup"><span data-stu-id="86698-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="86698-115">NuGet paket sürümü NuGet tarafından kullanılır ve çalışma zamanı davranışı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="86698-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="86698-116">NuGet paket sürümü ile birlikte NuGet paket tanımlayıcısı, NuGet'deki bir paketi tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86698-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="86698-117">Örneğin, `Newtonsoft.Json` + `11.0.2`.</span><span class="sxs-lookup"><span data-stu-id="86698-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="86698-118">Sonekli bir paket, sürüm öncesi bir pakettir ve bunu sınama için ideal kılan özel bir davranışa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="86698-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="86698-119">Daha fazla bilgi için [ön sürüm paketlerine](./nuget.md#pre-release-packages)bakın.</span><span class="sxs-lookup"><span data-stu-id="86698-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="86698-120">NuGet paket sürümü geliştiriciler için en görünür sürüm olduğundan, [Anlamsal Sürüm (SemVer)](https://semver.org/)kullanarak güncellemek için iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="86698-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="86698-121">SemVer, sürüm arasındaki değişikliklerin önemini belirtir ve geliştiricilerin hangi sürümü kullanacaklarını seçerken bilinçli bir karar vermelerine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="86698-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="86698-122">Örneğin, gitmek, `1.0` `2.0` büyük ölçüde kırılma değişiklikleri olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="86698-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="86698-123">✔️ NuGet paketinizi kullanmak için [SemVer 2.0.0'ı](https://semver.org/) kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="86698-123">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="86698-124">✔️ Kullanıcıların sık göreceği sürüm numarası olduğu için NuGet paket sürümünü herkese açık belgelerde kullanın.</span><span class="sxs-lookup"><span data-stu-id="86698-124">✔️ DO use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="86698-125">✔️ DURAĞAN olmayan bir paket serbest bırakıldığında bir ön sürüm soneki içerir.</span><span class="sxs-lookup"><span data-stu-id="86698-125">✔️ DO include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="86698-126">Kullanıcılar, paketin tamamlanmadığını anlayabilmeleri için ön sürüm paketleri almayı seçmelidir.</span><span class="sxs-lookup"><span data-stu-id="86698-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="86698-127">Montaj sürümü</span><span class="sxs-lookup"><span data-stu-id="86698-127">Assembly version</span></span>

<span data-ttu-id="86698-128">Derleme sürümü, CLR'nin bir derlemenin hangi sürümünün yüklenmesini seçmek için çalışma zamanında kullandığı sürümdür.</span><span class="sxs-lookup"><span data-stu-id="86698-128">The assembly version is what the CLR uses at runtime to select which version of an assembly to load.</span></span> <span data-ttu-id="86698-129">Sürüm kullanarak bir derleme seçmek yalnızca güçlü bir ada sahip derlemeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="86698-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="86698-130">Windows .NET Framework CLR güçlü bir adlandırılmış derleme yüklemek için tam bir eşleşme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="86698-130">The Windows .NET Framework CLR demands an exact match to load a strong named assembly.</span></span> <span data-ttu-id="86698-131">Örneğin, `Libary1, Version=1.0.0.0` bir başvuru ile `Newtonsoft.Json, Version=11.0.0.0`derlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="86698-131">For example, `Libary1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="86698-132">.NET Framework yalnızca bu tam `11.0.0.0`sürümü yükler.</span><span class="sxs-lookup"><span data-stu-id="86698-132">The .NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="86698-133">Çalışma zamanında farklı bir sürüm yüklemek için .NET uygulamasının config dosyasına bağlama yönlendirmesi eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="86698-133">To load a different version at runtime, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="86698-134">Montaj sürümü ile birlikte güçlü adlandırma [sıkı montaj sürümü yükleme](../assembly/versioning.md)sağlar.</span><span class="sxs-lookup"><span data-stu-id="86698-134">Strong naming combined with assembly version enables [strict assembly version loading](../assembly/versioning.md).</span></span> <span data-ttu-id="86698-135">Kitaplığı güçlü adlandırmanın bir dizi faydası olsa da, genellikle derlemenin bulunamayacağı çalışma zamanı özel durumları `app.config` / `web.config` ile sonuçlanır ve düzeltilmesi için [bağlama yönlendirmesi gerekir.](../../framework/configure-apps/redirect-assembly-versions.md)</span><span class="sxs-lookup"><span data-stu-id="86698-135">While strong naming a library has a number of benefits, it often results in runtime exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config`/`web.config` to be fixed.</span></span> <span data-ttu-id="86698-136">.NET Core montaj yüklemesi gevşetildi ve .NET Core CLR montajları çalışma zamanında daha yüksek bir sürümle otomatik olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="86698-136">.NET Core assembly loading has been relaxed, and the .NET Core CLR will automatically load assemblies at runtime with a higher version.</span></span>

<span data-ttu-id="86698-137">✔️ Yalnızca AssemblyVersion'da önemli bir sürümü de içeren düşünün.</span><span class="sxs-lookup"><span data-stu-id="86698-137">✔️ CONSIDER only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="86698-138">örneğin Kütüphane 1.0 ve Kütüphane 1.0.1'in her `1.0.0.0`ikisi de AssemblyVersion'a `2.0.0.0`sahipken, Kütüphane 2.0'ın AssemblyVersion'u vardır.</span><span class="sxs-lookup"><span data-stu-id="86698-138">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="86698-139">Derleme sürümü daha az sıklıkta değiştiğinde, bağlama yönlendirmelerini azaltır.</span><span class="sxs-lookup"><span data-stu-id="86698-139">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="86698-140">✔️ AssemblyVersion ve NuGet paket sürümünün ana sürüm numarasını senkronize tutmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="86698-140">✔️ CONSIDER keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="86698-141">AssemblyVersion kullanıcıya görüntülenen bazı bilgilendirme iletileri (örneğin, özel durum iletileri montaj adı ve montaj nitelikli tür adları) dahildir.</span><span class="sxs-lookup"><span data-stu-id="86698-141">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="86698-142">Sürümler arasındaki ilişkiyi sürdürmek, geliştiricilere hangi sürümü kullandıkları hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="86698-142">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="86698-143">❌Sabit bir AssemblyVersion'u YOKTUR.</span><span class="sxs-lookup"><span data-stu-id="86698-143">❌ DO NOT have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="86698-144">Değişmeyen Bir AssemblyVersion bağlama yönlendirmeleri gereksinimini önler, ancak derlemenin yalnızca tek bir sürümünün Genel Derleme Önbelleğine (GAC) yüklenebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="86698-144">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="86698-145">Ayrıca, başka bir uygulama GAC derlemesini kesme değişiklikleriyle güncelleştirirse, GAC'deki derlemeye başvuran uygulamalar da bozulur.</span><span class="sxs-lookup"><span data-stu-id="86698-145">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="86698-146">Derleme dosya sürümü</span><span class="sxs-lookup"><span data-stu-id="86698-146">Assembly file version</span></span>

<span data-ttu-id="86698-147">Derleme dosyası sürümü, Windows'ta bir dosya sürümünü görüntülemek için kullanılır ve çalışma zamanı davranışı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="86698-147">The assembly file version is used to display a file version in Windows and has no effect on runtime behavior.</span></span> <span data-ttu-id="86698-148">Bu sürümü ayarlamak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="86698-148">Setting this version is optional.</span></span> <span data-ttu-id="86698-149">Windows Gezgini'ndeki Dosya Özellikleri iletişim kutusunda görülebilir:</span><span class="sxs-lookup"><span data-stu-id="86698-149">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="86698-150">![Windows Gezgini](./media/versioning/win-properties.png "Windows Gezgini")</span><span class="sxs-lookup"><span data-stu-id="86698-150">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

<span data-ttu-id="86698-151">✔️ AssemblyFileVersion revizyonu olarak sürekli bir entegrasyon yapı numarası dahil düşünün.</span><span class="sxs-lookup"><span data-stu-id="86698-151">✔️ CONSIDER including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="86698-152">Örneğin, projenizin 1.0.0 sürümünü oluşturuyorsunuz ve sürekli tümleştirme yapı numarası 99 olduğundan AssemblyFileVersion'unuz 1.0.0.99'dur.</span><span class="sxs-lookup"><span data-stu-id="86698-152">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

<span data-ttu-id="86698-153">✔️ DO dosya `Major.Minor.Build.Revision` sürümü için biçimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="86698-153">✔️ DO use the format `Major.Minor.Build.Revision` for file version.</span></span>

> <span data-ttu-id="86698-154">Dosya sürümü .NET tarafından hiçbir zaman kullanılmazken, Windows `Major.Minor.Build.Revision` dosya sürümünün biçimde olmasını [bekler.](/windows/desktop/menurc/versioninfo-resource)</span><span class="sxs-lookup"><span data-stu-id="86698-154">While the file version is never used by .NET, [Windows expects the file version](/windows/desktop/menurc/versioninfo-resource) to be in the `Major.Minor.Build.Revision` format.</span></span> <span data-ttu-id="86698-155">Sürüm bu biçimi izlemezse bir uyarı yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="86698-155">A warning is raised if the version doesn't follow this format.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="86698-156">Derleme bilgilendirme sürümü</span><span class="sxs-lookup"><span data-stu-id="86698-156">Assembly informational version</span></span>

<span data-ttu-id="86698-157">Derleme bilgilendirme sürümü ek sürüm bilgilerini kaydetmek için kullanılır ve çalışma zamanı davranışı üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="86698-157">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="86698-158">Bu sürümü ayarlamak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="86698-158">Setting this version is optional.</span></span> <span data-ttu-id="86698-159">Kaynak Bağlantı kullanıyorsanız, bu sürüm NuGet paket sürümü artı bir kaynak denetim sürümü ile yapıya ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="86698-159">If you're using Source Link, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="86698-160">Örneğin, `1.0.0-beta1+204ff0a` derlemenin oluşturduğu kaynak kodun işleyiş karmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="86698-160">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="86698-161">Daha fazla bilgi için [Kaynak Bağlantı'ya](./sourcelink.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="86698-161">For more information, see [Source Link](./sourcelink.md).</span></span>

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> <span data-ttu-id="86698-162">Visual Studio'nun eski sürümleri, bu sürüm biçimi `Major.Minor.Build.Revision`izlemezse bir yapı uyarısı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="86698-162">Older versions of Visual Studio raise a build warning if this version doesn't follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="86698-163">Uyarı güvenle yoksayılabilir.</span><span class="sxs-lookup"><span data-stu-id="86698-163">The warning can be safely ignored.</span></span>

<span data-ttu-id="86698-164">❌Derleme bilgilendirme sürümünü kendiniz ayarlamakTAN kaçının.</span><span class="sxs-lookup"><span data-stu-id="86698-164">❌ AVOID setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="86698-165">SourceLink'in NuGet ve kaynak denetimi meta verilerini içeren sürümü otomatik olarak oluşturmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="86698-165">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="86698-166">[Önceki](publish-nuget-package.md)
>[Sonraki](breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="86698-166">[Previous](publish-nuget-package.md)
[Next](breaking-changes.md)</span></span>
