---
title: .NET Framework'te Uygulama Uyumluluğu
ms.date: 05/19/2017
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31d14a8ef6a4b17eea1b9160e811bb92946d775b
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728647"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="e59d7-102">.NET Framework'te Uygulama Uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="e59d7-102">Application Compatibility in the .NET Framework</span></span>

## <a name="introduction"></a><span data-ttu-id="e59d7-103">Giriş</span><span class="sxs-lookup"><span data-stu-id="e59d7-103">Introduction</span></span>
<span data-ttu-id="e59d7-104">Uyumluluk her .NET sürüm çok önemli hedefidir.</span><span class="sxs-lookup"><span data-stu-id="e59d7-104">Compatibility is a very important goal of each .NET release.</span></span> <span data-ttu-id="e59d7-105">Uyumluluk her sürümü olmasını sağlar eklenebilir, bu nedenle önceki sürümleri hala çalışır.</span><span class="sxs-lookup"><span data-stu-id="e59d7-105">Compatibility ensures that each version is additive, so previous versions will still work.</span></span> <span data-ttu-id="e59d7-106">Diğer taraftan, (performansı, güvenlik sorunları gidermek veya hataları düzeltmek için) önceki işlevsellik değişiklikleri var olan kodu veya sonraki bir sürümünü altında çalışan uygulamalara uyumluluk sorunlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e59d7-106">On the other hand, changes to previous functionality (to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span> <span data-ttu-id="e59d7-107">.NET Framework yeniden hedefleme değişiklikleri ve çalışma zamanı değişiklikleri algılar.</span><span class="sxs-lookup"><span data-stu-id="e59d7-107">The .NET Framework recognizes retargeting changes and runtime changes.</span></span> <span data-ttu-id="e59d7-108">Yeniden hedefleme değişiklikleri belirli bir .NET Framework sürümünü hedef ancak sonraki bir sürümünde çalışan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="e59d7-108">Retargeting changes affect applications that target a specific version of the .NET Framework but are running on a later version.</span></span> <span data-ttu-id="e59d7-109">Çalışma zamanı değişiklikleri belirli bir sürümünde çalışan tüm uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="e59d7-109">Runtime changes affect all applications running on a particular version.</span></span>

<span data-ttu-id="e59d7-110">Her uygulama belirli bir sürümü tarafından belirtilen .NET Framework'ün hedefler:</span><span class="sxs-lookup"><span data-stu-id="e59d7-110">Each app targets a specific version of the .NET Framework, which can be specified by:</span></span>

* <span data-ttu-id="e59d7-111">Bir hedef framework Visual Studio'da tanımlama.</span><span class="sxs-lookup"><span data-stu-id="e59d7-111">Defining a target framework in Visual Studio.</span></span>
* <span data-ttu-id="e59d7-112">Hedef Framework'ü bir proje dosyasında belirtme.</span><span class="sxs-lookup"><span data-stu-id="e59d7-112">Specifying the target framework in a project file.</span></span>
* <span data-ttu-id="e59d7-113">Uygulama bir <xref:System.Runtime.Versioning.TargetFrameworkAttribute> kaynak koduna.</span><span class="sxs-lookup"><span data-stu-id="e59d7-113">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="e59d7-114">Ne hedeflenen daha yeni bir sürümü üzerinde çalışırken, .NET Framework hedeflenen sürümün taklit etmek üzere quirked davranışı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e59d7-114">When running on a newer version than what was targeted, the .NET Framework will use quirked behavior to mimic the older targeted version.</span></span> <span data-ttu-id="e59d7-115">Diğer bir deyişle, uygulama Framework sürümü çalıştırın, ancak eski sürümünde çalışıyorsa gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="e59d7-115">In other words, the app will run on the newer version of the Framework, but act as if it's running on the older version.</span></span> <span data-ttu-id="e59d7-116">.NET Framework sürümleri arasındaki uyumluluk sorunları çoğunu bu quirking modeli aracılığıyla azalır.</span><span class="sxs-lookup"><span data-stu-id="e59d7-116">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="e59d7-117">.NET Framework sürümünü, bir uygulama hedefleri girişi bütünleştirilmiş kodun çalışan uygulama etki alanı için hedef sürümü tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e59d7-117">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code is running in.</span></span> <span data-ttu-id="e59d7-118">Tüm ek derlemeler uygulama etki alanı hedefleyen, .NET Framework sürümü yüklü.</span><span class="sxs-lookup"><span data-stu-id="e59d7-118">All additional assemblies loaded in that application domain target that .NET Framework version.</span></span> <span data-ttu-id="e59d7-119">Örneğin, yürütülebilir olması durumunda çalıştırılabilir hedefleri çerçevedir, tüm derlemelerde AppDomain altında çalışacağı uyumluluk modu.</span><span class="sxs-lookup"><span data-stu-id="e59d7-119">For example, in the case of an executable, the framework the executable targets is the compatibility mode all assemblies in that AppDomain will run under.</span></span>

## <a name="runtime-changes"></a><span data-ttu-id="e59d7-120">{1&gt;Çalışma zamanı değişiklikleri&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e59d7-120">Runtime changes</span></span>

<span data-ttu-id="e59d7-121">Çalışma zamanı sorunlarına yeni bir çalışma zamanı bir makinede yerleştirilir ve aynı ikili dosyaları çalıştırın, ancak farklı bir davranış görülen ortaya olanlardır.</span><span class="sxs-lookup"><span data-stu-id="e59d7-121">Runtime issues are those that arise when a new runtime is placed on a machine and the same binaries are run, but different behavior is seen.</span></span> <span data-ttu-id="e59d7-122">Bir ikili .NET Framework 4.0 için derlenmiş ise .NET Framework 4.0 uyumluluk modunda 4.5 veya sonraki sürümlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e59d7-122">If a binary was compiled for .NET Framework 4.0 it will run in .NET Framework 4.0 compatibility mode on 4.5 or later versions.</span></span> <span data-ttu-id="e59d7-123">4.5 etkileyen değişiklikler çoğunu 4.0 için derlenmiş bir ikili etkilemez.</span><span class="sxs-lookup"><span data-stu-id="e59d7-123">Many of the changes that affect 4.5 will not affect a binary compiled for 4.0.</span></span> <span data-ttu-id="e59d7-124">Bu uygulama etki alanına özgü ve giriş derleme ayarlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e59d7-124">This is specific to the AppDomain and depends on the settings of the entry assembly.</span></span>

## <a name="retargeting-changes"></a><span data-ttu-id="e59d7-125">Yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="e59d7-125">Retargeting changes</span></span>

<span data-ttu-id="e59d7-126">Yeniden hedefleme sorunları 4.0 hedefleyen bir derlemeyi artık hedef 4.5 ayarlandığında ortaya çıkan olanlardır.</span><span class="sxs-lookup"><span data-stu-id="e59d7-126">Retargeting issues are those that arise when an assembly that was targeting 4.0 is now set to target 4.5.</span></span> <span data-ttu-id="e59d7-127">Artık derleme yeni özelliklerin yanı sıra eski özelliklerin olası uyumluluk sorunlarına içine kabul eder.</span><span class="sxs-lookup"><span data-stu-id="e59d7-127">Now the assembly opts into the new features as well as potential compatibility issues to old features.</span></span> <span data-ttu-id="e59d7-128">Yeniden, bu girdi derlemesi tarafından böylece dikte edilir derleme kullanan konsol uygulaması veya bütünleştirilmiş koduna başvuruyor Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="e59d7-128">Again, this is dictated by the entry assembly, so the console app that uses the assembly, or the website that references the assembly.</span></span>

## <a name="net-compatibility-diagnostics"></a><span data-ttu-id="e59d7-129">.NET uyumluluğu tanılama</span><span class="sxs-lookup"><span data-stu-id="e59d7-129">.NET Compatibility Diagnostics</span></span>

<span data-ttu-id="e59d7-130">.NET uyumluluğu tanılama Roslyn destekli çözümleyiciler, .NET Framework sürümleri arasında uygulama uyumluluğu sorunları tanımlamaya yardımcı olan.</span><span class="sxs-lookup"><span data-stu-id="e59d7-130">The .NET Compatibility Diagnostics are Roslyn-powered analyzers that help identify application compatibility issues between versions of the .NET Framework.</span></span> <span data-ttu-id="e59d7-131">Yalnızca bir alt özel tüm geçiş uygulanacak rağmen bu liste tüm kullanılabilir çözümleyiciler içerir.</span><span class="sxs-lookup"><span data-stu-id="e59d7-131">This list contains all of the analyzers available, although only a subset will apply to any specific migration.</span></span> <span data-ttu-id="e59d7-132">Çözümleyiciler hangi sorunların planlanan geçiş için geçerlidir ve yalnızca bu belirir belirler.</span><span class="sxs-lookup"><span data-stu-id="e59d7-132">The analyzers will determine which issues are applicable for the planned migration and will only surface those.</span></span>

<span data-ttu-id="e59d7-133">Her sorun aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="e59d7-133">Each issue includes the following information:</span></span>

-   <span data-ttu-id="e59d7-134">Önceki bir sürümden nelerin değiştiğini açıklaması.</span><span class="sxs-lookup"><span data-stu-id="e59d7-134">The description of what has changed from a previous version.</span></span>

-   <span data-ttu-id="e59d7-135">Nasıl değişiklik müşteriler ve herhangi bir geçici çözüm sürümleri arasında uyumluluğu korumak kullanılabilir olup etkiler.</span><span class="sxs-lookup"><span data-stu-id="e59d7-135">How the change affects customers and whether any workarounds are available to preserve compatibility across versions.</span></span>

-   <span data-ttu-id="e59d7-136">Değişikliğin ne kadar önemli olduğunu'nin bir değerlendirme.</span><span class="sxs-lookup"><span data-stu-id="e59d7-136">An assessment of how important the change is.</span></span> <span data-ttu-id="e59d7-137">Uygulama uyumluluk sorunu kategorilere gibi:</span><span class="sxs-lookup"><span data-stu-id="e59d7-137">Application compatibility issue are categorized as follows:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="e59d7-138">Ana</span><span class="sxs-lookup"><span data-stu-id="e59d7-138">Major</span></span>|<span data-ttu-id="e59d7-139">Çok sayıda uygulamaları etkiler veya önemli kodunun değiştirilmesini gerektirir önemli bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="e59d7-139">A significant change that affects a large number of apps or requires substantial modification of code.</span></span>|
    |<span data-ttu-id="e59d7-140">Küçük</span><span class="sxs-lookup"><span data-stu-id="e59d7-140">Minor</span></span>|<span data-ttu-id="e59d7-141">Az sayıda uygulamaları etkiler veya ikincil kodunun değiştirilmesini gerektiren bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="e59d7-141">A change that affects a small number of apps or that requires minor modification of code.</span></span>|
    |<span data-ttu-id="e59d7-142">Uç durum</span><span class="sxs-lookup"><span data-stu-id="e59d7-142">Edge case</span></span>|<span data-ttu-id="e59d7-143">Uygulamalar belirli, genel olarak görülmez senaryoları altında etkileyen bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="e59d7-143">A change that affects apps under very specific, uncommon scenarios.</span></span>|
    |<span data-ttu-id="e59d7-144">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="e59d7-144">Transparent</span></span>|<span data-ttu-id="e59d7-145">Bir değişiklik uygulama geliştiricisi veya kullanıcı belirgin hiçbir etkisi olmadan.</span><span class="sxs-lookup"><span data-stu-id="e59d7-145">A change with no noticeable effect on the application's developer or user.</span></span>|

-   <span data-ttu-id="e59d7-146">Sürüm değişikliği ilk framework görüntülendiğinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="e59d7-146">Version indicates when the change first appears in the framework.</span></span> <span data-ttu-id="e59d7-147">Bazı değişiklikler belirli bir sürümünde sunulan ve bir sonraki sürümde geri; Bu da gösterilir.</span><span class="sxs-lookup"><span data-stu-id="e59d7-147">Some of the changes are introduced in a particular version and reverted in a later version; that is indicated as well.</span></span>

-   <span data-ttu-id="e59d7-148">Değişiklik türü:</span><span class="sxs-lookup"><span data-stu-id="e59d7-148">The type of change:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="e59d7-149">Yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="e59d7-149">Retargeting</span></span>|<span data-ttu-id="e59d7-150">Değişiklik yeni bir .NET Framework sürümünü hedefleyecek şekilde derlenir uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="e59d7-150">The change affects apps that are recompiled to target a new version of the .NET Framework.</span></span>|
    |<span data-ttu-id="e59d7-151">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="e59d7-151">Runtime</span></span>|<span data-ttu-id="e59d7-152">Bu değişiklik, .NET Framework'ün önceki bir sürümünü hedefleyen ancak sonraki bir sürümünü çalıştıran mevcut bir uygulamayı etkiler.</span><span class="sxs-lookup"><span data-stu-id="e59d7-152">The change affects an existing app that targets a previous version of the .NET Framework but runs on a later version.</span></span>|

-   <span data-ttu-id="e59d7-153">Etkilenen API'leri, varsa.</span><span class="sxs-lookup"><span data-stu-id="e59d7-153">The affected APIS, if any.</span></span>

-   <span data-ttu-id="e59d7-154">Kullanılabilir tanılama kimlikleri</span><span class="sxs-lookup"><span data-stu-id="e59d7-154">The IDs of the available diagnostics</span></span>

## <a name="usage"></a><span data-ttu-id="e59d7-155">Kullanım</span><span class="sxs-lookup"><span data-stu-id="e59d7-155">Usage</span></span>
<span data-ttu-id="e59d7-156">Başlamak için aşağıdaki uyumluluk değişiklik türünü seçin:</span><span class="sxs-lookup"><span data-stu-id="e59d7-156">To begin, select the type of compatibility change below:</span></span>

* [<span data-ttu-id="e59d7-157">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="e59d7-157">Retargeting Changes</span></span>](./retargeting/index.md)
* [<span data-ttu-id="e59d7-158">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="e59d7-158">Runtime Changes</span></span>](./runtime/index.md)


## <a name="see-also"></a><span data-ttu-id="e59d7-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e59d7-159">See Also</span></span>

* [<span data-ttu-id="e59d7-160">Sürümler ve Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="e59d7-160">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
* [<span data-ttu-id="e59d7-161">Yenilikler</span><span class="sxs-lookup"><span data-stu-id="e59d7-161">What's New</span></span>](../../../docs/framework/whats-new/index.md)
* [<span data-ttu-id="e59d7-162">Sınıf Kitaplığında Artık Kullanılmayanlar</span><span class="sxs-lookup"><span data-stu-id="e59d7-162">What's Obsolete in the Class Library</span></span>](../../../docs/framework/whats-new/whats-obsolete.md)
