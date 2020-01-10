---
title: Sürüm oluşturma ve .NET kitaplıkları
description: .NET kitaplıklarını sürüm oluşturma için en iyi yöntem önerileri.
ms.date: 12/10/2018
ms.openlocfilehash: 8ed3217e39b1fe0f330a650ec72cda224866e207
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706419"
---
# <a name="versioning"></a><span data-ttu-id="69528-103">Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="69528-103">Versioning</span></span>

<span data-ttu-id="69528-104">Yazılım kitaplığı sürüm 1,0 ' de nadiren tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="69528-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="69528-105">İyi kitaplıklar zaman içinde geliştikçe, özellikler ekleyerek, hataları düzelterek ve performansı artırdı.</span><span class="sxs-lookup"><span data-stu-id="69528-105">Good libraries evolve over time, adding features, fixing bugs and improving performance.</span></span> <span data-ttu-id="69528-106">Mevcut kullanıcıları bozmadan, her bir sürümle ek değer sağlayan bir .NET kitaplığının yeni sürümlerini yayınlanbilmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="69528-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="69528-107">Yeni değişiklikler</span><span class="sxs-lookup"><span data-stu-id="69528-107">Breaking changes</span></span>

<span data-ttu-id="69528-108">Sürümler arasındaki önemli değişiklikleri işleme hakkında daha fazla bilgi için bkz. [son değişiklikler](./breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="69528-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="69528-109">Sürüm numaraları</span><span class="sxs-lookup"><span data-stu-id="69528-109">Version numbers</span></span>

<span data-ttu-id="69528-110">.NET kitaplığı, bir sürümü belirtmek için birçok yol sunar.</span><span class="sxs-lookup"><span data-stu-id="69528-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="69528-111">Bu sürümler en önemli öneme sahiptir:</span><span class="sxs-lookup"><span data-stu-id="69528-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="69528-112">NuGet paket sürümü</span><span class="sxs-lookup"><span data-stu-id="69528-112">NuGet package version</span></span>

<span data-ttu-id="69528-113">[NuGet paket sürümü](/nuget/reference/package-versioning) , NuGet.org, Visual Studio NuGet Paket Yöneticisi ve paket kullanıldığında kaynak koda eklenir.</span><span class="sxs-lookup"><span data-stu-id="69528-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="69528-114">NuGet paket sürümü, kullanıcıların yaygın olarak görebilecekleri sürüm numarasıdır ve kullandıkları bir kitaplığın sürümü hakkında konuşduklarında bu bilgileri ifade eder.</span><span class="sxs-lookup"><span data-stu-id="69528-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="69528-115">NuGet paket sürümü NuGet tarafından kullanılır ve çalışma zamanı davranışını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="69528-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="69528-116">NuGet paket sürümü ile birlikte bulunan NuGet paket tanımlayıcısı, NuGet içindeki bir paketi tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69528-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="69528-117">Örneğin, `Newtonsoft.Json` + `11.0.2`.</span><span class="sxs-lookup"><span data-stu-id="69528-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="69528-118">Soneki olan bir paket yayın öncesi paketidir ve test için ideal hale getiren özel davranışları vardır.</span><span class="sxs-lookup"><span data-stu-id="69528-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="69528-119">Daha fazla bilgi için bkz. [yayın öncesi paketleri](./nuget.md#pre-release-packages).</span><span class="sxs-lookup"><span data-stu-id="69528-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="69528-120">NuGet paketi sürümü geliştiricilerin en çok görülebilen sürümü olduğu için, [anlamsal sürüm oluşturma (SemVer)](https://semver.org/)kullanılarak güncelleştirilmesi iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="69528-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="69528-121">SemVer, yayın arasındaki değişikliklerin önemini gösterir ve geliştiricilerin hangi sürümü kullanacağınızı seçerken bilinçli bir karar vermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="69528-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="69528-122">Örneğin, `1.0` `2.0`, olası büyük değişiklikler olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="69528-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="69528-123">**✔️** NuGet paketinizi sürüm Için [Semver 2.0.0](https://semver.org/) kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="69528-123">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="69528-124">**✔️** , kullanıcıların yaygın olarak göreceği sürüm numarası olduğundan, ortak belgelerde NuGet paketi sürümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="69528-124">**✔️ DO** use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="69528-125">kararlı olmayan bir paket yayınlarken yayın öncesi son eki dahil **✔️** .</span><span class="sxs-lookup"><span data-stu-id="69528-125">**✔️ DO** include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="69528-126">Kullanıcılar, yayın öncesi paketleri almak için kabul etmelidir, dolayısıyla paketin tamamlanmamış olduğunu anlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="69528-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="69528-127">Derleme sürümü</span><span class="sxs-lookup"><span data-stu-id="69528-127">Assembly version</span></span>

<span data-ttu-id="69528-128">Derleme sürümü, CLR 'nin hangi derleme sürümünü yükleneceğini seçmek için çalışma zamanında kullandığı şeydir.</span><span class="sxs-lookup"><span data-stu-id="69528-128">The assembly version is what the CLR uses at runtime to select which version of an assembly to load.</span></span> <span data-ttu-id="69528-129">Sürüm oluşturma kullanılarak bir derlemeyi seçmek, yalnızca güçlü bir ada sahip derlemeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="69528-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="69528-130">Windows .NET Framework CLR kesin bir adlandırılmış derlemeyi yüklemek için tam bir eşleşme talep ister.</span><span class="sxs-lookup"><span data-stu-id="69528-130">The Windows .NET Framework CLR demands an exact match to load a strong named assembly.</span></span> <span data-ttu-id="69528-131">Örneğin, `Libary1, Version=1.0.0.0` `Newtonsoft.Json, Version=11.0.0.0`bir başvuru ile derlendi.</span><span class="sxs-lookup"><span data-stu-id="69528-131">For example, `Libary1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="69528-132">.NET Framework yalnızca bu sürümü `11.0.0.0`yükleyecek.</span><span class="sxs-lookup"><span data-stu-id="69528-132">The .NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="69528-133">Çalışma zamanında farklı bir sürüm yüklemek için .NET uygulamasının yapılandırma dosyasına bir bağlama yeniden yönlendirmesi eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="69528-133">To load a different version at runtime, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="69528-134">Bütünleştirilmiş kod sürümüyle birlikte tanımlayıcı adlandırma [katı derleme sürümü yüklemeye](../assembly/versioning.md)izin vermez.</span><span class="sxs-lookup"><span data-stu-id="69528-134">Strong naming combined with assembly version enables [strict assembly version loading](../assembly/versioning.md).</span></span> <span data-ttu-id="69528-135">Bir kitaplıkta güçlü adlandırma bir dizi avantaja sahip olsa da, genellikle bir derlemenin bulunamaması ve `app.config`/`web.config` düzeltilmesi için bağlama yeniden [yönlendirmeleri gerektirdiğinden](../../framework/configure-apps/redirect-assembly-versions.md) çalışma zamanı özel durumları oluşur.</span><span class="sxs-lookup"><span data-stu-id="69528-135">While strong naming a library has a number of benefits, it often results in runtime exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config`/`web.config` to be fixed.</span></span> <span data-ttu-id="69528-136">.NET Core derleme yüklemesi gevşek bir şekilde geliştirilmiştir ve .NET Core CLR, derlemeleri daha yüksek bir sürüme sahip çalışma zamanında otomatik olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="69528-136">.NET Core assembly loading has been relaxed, and the .NET Core CLR will automatically load assemblies at runtime with a higher version.</span></span>

<span data-ttu-id="69528-137">✔️ yalnızca AssemblyVersion içinde önemli bir sürüm dahil olmak üzere **göz önünde bulundurun** .</span><span class="sxs-lookup"><span data-stu-id="69528-137">**✔️ CONSIDER** only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="69528-138">Örneğin, Library 1,0 ve Library 1.0.1 'in AssemblyVersion 'ı `1.0.0.0`vardır, ancak kitaplığı 2,0, `2.0.0.0`AssemblyVersion öğesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="69528-138">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="69528-139">Derleme sürümü genellikle daha az değiştiğinde bağlama yeniden yönlendirmelerini azaltır.</span><span class="sxs-lookup"><span data-stu-id="69528-139">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="69528-140">✔️ AssemblyVersion 'ın ana sürüm numarasını ve NuGet paket sürümünü eşitlenmiş halde tutmayı **göz önünde bulundurun** .</span><span class="sxs-lookup"><span data-stu-id="69528-140">**✔️ CONSIDER** keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="69528-141">AssemblyVersion, kullanıcıya görüntülenen bazı bilgilendirici iletilere, örneğin, özel durum iletilerinde derleme adı ve derleme nitelikli tür adlarına dahildir.</span><span class="sxs-lookup"><span data-stu-id="69528-141">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="69528-142">Sürümler arasındaki ilişkinin saklanması, geliştiriciler tarafından hangi sürümü kullandıkları hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="69528-142">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="69528-143">**❌** sabit bir AssemblyVersion yok.</span><span class="sxs-lookup"><span data-stu-id="69528-143">**❌ DO NOT** have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="69528-144">Bir AssemblyVersion, bağlama yeniden yönlendirmeleri gereksinimini ortadan kaldırdıkça, derlemenin yalnızca tek bir sürümünün genel derleme önbelleği 'ne (GAC) yüklenebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="69528-144">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="69528-145">Ayrıca, GAC 'de derlemeye başvuruda bulunan uygulamalar, başka bir uygulama GAC derlemesini bozan değişikliklerle güncelleştirmiş olursa kesilir.</span><span class="sxs-lookup"><span data-stu-id="69528-145">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="69528-146">Bütünleştirilmiş kod dosyası sürümü</span><span class="sxs-lookup"><span data-stu-id="69528-146">Assembly file version</span></span>

<span data-ttu-id="69528-147">Derleme dosyası sürümü, Windows 'ta bir dosya sürümünü göstermek için kullanılır ve çalışma zamanı davranışına hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="69528-147">The assembly file version is used to display a file version in Windows and has no effect on runtime behavior.</span></span> <span data-ttu-id="69528-148">Bu sürümün ayarlanması isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="69528-148">Setting this version is optional.</span></span> <span data-ttu-id="69528-149">Windows Gezgini 'nde dosya özellikleri iletişim kutusunda görünür:</span><span class="sxs-lookup"><span data-stu-id="69528-149">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="69528-150">![Windows Gezgini](./media/versioning/win-properties.png "Windows Gezgini")</span><span class="sxs-lookup"><span data-stu-id="69528-150">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

<span data-ttu-id="69528-151">✔️ AssemblyFileVersion düzeltmesi olarak bir sürekli tümleştirme yapı numarası dahil **etmeyi göz önünde bulundurun** .</span><span class="sxs-lookup"><span data-stu-id="69528-151">**✔️ CONSIDER** including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="69528-152">Örneğin, projenizin sürüm 1.0.0 derleniyor ve sürekli tümleştirme derleme numarası 99 ' dir; bu nedenle AssemblyFileVersion 1.0.0.99.</span><span class="sxs-lookup"><span data-stu-id="69528-152">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

<span data-ttu-id="69528-153">**✔️** dosya sürümü için `Major.Minor.Build.Revision` biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="69528-153">**✔️ DO** use the format `Major.Minor.Build.Revision` for file version.</span></span>

> <span data-ttu-id="69528-154">Dosya sürümü hiçbir şekilde .NET tarafından kullanılmadığından, [Windows dosya sürümünün](/windows/desktop/menurc/versioninfo-resource) `Major.Minor.Build.Revision` biçiminde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="69528-154">While the file version is never used by .NET, [Windows expects the file version](/windows/desktop/menurc/versioninfo-resource) to be in the `Major.Minor.Build.Revision` format.</span></span> <span data-ttu-id="69528-155">Sürüm bu biçimi izmezse bir uyarı tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="69528-155">A warning is raised if the version doesn't follow this format.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="69528-156">Derleme bilgilendirici sürümü</span><span class="sxs-lookup"><span data-stu-id="69528-156">Assembly informational version</span></span>

<span data-ttu-id="69528-157">Derleme bilgilendirici sürümü, ek sürüm bilgilerini kaydetmek için kullanılır ve çalışma zamanı davranışına hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="69528-157">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="69528-158">Bu sürümün ayarlanması isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="69528-158">Setting this version is optional.</span></span> <span data-ttu-id="69528-159">Kaynak bağlantısı kullanıyorsanız, bu sürüm NuGet paketi sürümü ve kaynak denetimi sürümü ile derleme üzerinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="69528-159">If you're using Source Link, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="69528-160">Örneğin `1.0.0-beta1+204ff0a`, derlemenin oluşturulduğu kaynak kodun COMMIT karmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="69528-160">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="69528-161">Daha fazla bilgi için bkz. [kaynak bağlantısı](./sourcelink.md).</span><span class="sxs-lookup"><span data-stu-id="69528-161">For more information, see [Source Link](./sourcelink.md).</span></span>

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> <span data-ttu-id="69528-162">Visual Studio 'nun eski sürümleri, bu sürüm `Major.Minor.Build.Revision`biçimini izmazsa derleme uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="69528-162">Older versions of Visual Studio raise a build warning if this version doesn't follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="69528-163">Uyarı güvenle yoksayılabilir.</span><span class="sxs-lookup"><span data-stu-id="69528-163">The warning can be safely ignored.</span></span>

<span data-ttu-id="69528-164">**❌** derleme bilgilendirici sürümünü kendi kendinize AYARLAMAKTAN kaçının.</span><span class="sxs-lookup"><span data-stu-id="69528-164">**❌ AVOID** setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="69528-165">SourceLink 'in NuGet ve kaynak denetimi meta verilerini içeren sürümü otomatik olarak oluşturmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="69528-165">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="69528-166">[Önceki](publish-nuget-package.md)
>[İleri](breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="69528-166">[Previous](publish-nuget-package.md)
[Next](breaking-changes.md)</span></span>
