---
title: ".NET Framework'te Uygulama Uyumluluğu"
ms.custom: 
ms.date: 05/19/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
- app-compat
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
caps.latest.revision: "19"
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0144d75d7b158efb5ab205dfdd96884fb630eabc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="f2f5a-102">.NET Framework'te Uygulama Uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="f2f5a-102">Application Compatibility in the .NET Framework</span></span>

## <a name="introduction"></a><span data-ttu-id="f2f5a-103">Giriş</span><span class="sxs-lookup"><span data-stu-id="f2f5a-103">Introduction</span></span>
<span data-ttu-id="f2f5a-104">Uyumluluk her .NET sürüm çok önemli hedefidir.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-104">Compatibility is a very important goal of each .NET release.</span></span> <span data-ttu-id="f2f5a-105">Uyumluluk her sürümü olmasını sağlar eklenebilir, bu nedenle önceki sürümleri hala çalışır.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-105">Compatibility ensures that each version is additive, so previous versions will still work.</span></span> <span data-ttu-id="f2f5a-106">Diğer taraftan, (performansı, güvenlik sorunları gidermek veya hataları düzeltmek için) önceki işlevsellik değişiklikleri var olan kodu veya sonraki bir sürümünü altında çalışan uygulamalara uyumluluk sorunlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-106">On the other hand, changes to previous functionality (to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span> <span data-ttu-id="f2f5a-107">.NET Framework yeniden hedefleme değişiklikleri ve çalışma zamanı değişiklikleri algılar.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-107">The .NET Framework recognizes retargeting changes and runtime changes.</span></span> <span data-ttu-id="f2f5a-108">Yeniden hedefleme değişiklikleri belirli bir .NET Framework sürümünü hedef ancak sonraki bir sürümünde çalışan uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-108">Retargeting changes affect applications that target a specific version of the .NET Framework but are running on a later version.</span></span> <span data-ttu-id="f2f5a-109">Çalışma zamanı değişiklikleri belirli bir sürümünde çalışan tüm uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-109">Runtime changes affect all applications running on a particular version.</span></span>

<span data-ttu-id="f2f5a-110">Her uygulama belirli bir sürümü tarafından belirtilen .NET Framework'ün hedefler:</span><span class="sxs-lookup"><span data-stu-id="f2f5a-110">Each app targets a specific version of the .NET Framework, which can be specified by:</span></span>

* <span data-ttu-id="f2f5a-111">Bir hedef framework Visual Studio'da tanımlama.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-111">Defining a target framework in Visual Studio.</span></span>
* <span data-ttu-id="f2f5a-112">Hedef Framework'ü bir proje dosyasında belirtme.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-112">Specifying the target framework in a project file.</span></span>
* <span data-ttu-id="f2f5a-113">Uygulama bir <xref:System.Runtime.Versioning.TargetFrameworkAttribute> kaynak koduna.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-113">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="f2f5a-114">Ne hedeflenen daha yeni bir sürümü üzerinde çalışırken, .NET Framework hedeflenen sürümün taklit etmek üzere quirked davranışı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-114">When running on a newer version than what was targeted, the .NET Framework will use quirked behavior to mimic the older targeted version.</span></span> <span data-ttu-id="f2f5a-115">Diğer bir deyişle, uygulama Framework sürümü çalıştırın, ancak eski sürümünde çalışıyorsa gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-115">In other words, the app will run on the newer version of the Framework, but act as if it's running on the older version.</span></span> <span data-ttu-id="f2f5a-116">.NET Framework sürümleri arasındaki uyumluluk sorunları çoğunu bu quirking modeli aracılığıyla azalır.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-116">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span>

## <a name="runtime-changes"></a><span data-ttu-id="f2f5a-117">Çalışma zamanı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="f2f5a-117">Runtime changes</span></span>

<span data-ttu-id="f2f5a-118">Çalışma zamanı sorunlarına yeni bir çalışma zamanı bir makinede yerleştirilir ve aynı ikili dosyaları çalıştırın, ancak farklı bir davranış görülen ortaya olanlardır.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-118">Runtime issues are those that arise when a new runtime is placed on a machine and the same binaries are run, but different behavior is seen.</span></span> <span data-ttu-id="f2f5a-119">Bir ikili .NET Framework 4.0 için derlenmiş ise .NET Framework 4.0 uyumluluk modunda 4.5 veya sonraki sürümlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-119">If a binary was compiled for .NET Framework 4.0 it will run in .NET Framework 4.0 compatibility mode on 4.5 or later versions.</span></span> <span data-ttu-id="f2f5a-120">4.5 etkileyen değişiklikler çoğunu 4.0 için derlenmiş bir ikili etkilemez.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-120">Many of the changes that affect 4.5 will not affect a binary compiled for 4.0.</span></span> <span data-ttu-id="f2f5a-121">Bu uygulama etki alanına özgü ve giriş derleme ayarlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-121">This is specific to the AppDomain and depends on the settings of the entry assembly.</span></span>

## <a name="retargeting-changes"></a><span data-ttu-id="f2f5a-122">Yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="f2f5a-122">Retargeting changes</span></span>

<span data-ttu-id="f2f5a-123">Yeniden hedefleme sorunları 4.0 hedefleyen bir derlemeyi artık hedef 4.5 ayarlandığında ortaya çıkan olanlardır.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-123">Retargeting issues are those that arise when an assembly that was targeting 4.0 is now set to target 4.5.</span></span> <span data-ttu-id="f2f5a-124">Artık derleme yeni özelliklerin yanı sıra eski özelliklerin olası uyumluluk sorunlarına içine kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-124">Now the assembly opts into the new features as well as potential compatibility issues to old features.</span></span> <span data-ttu-id="f2f5a-125">Yeniden, bu girdi derlemesi tarafından böylece dikte edilir derleme kullanan konsol uygulaması veya bütünleştirilmiş koduna başvuruyor Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-125">Again, this is dictated by the entry assembly, so the console app that uses the assembly, or the website that references the assembly.</span></span>

## <a name="net-compatibility-diagnostics"></a><span data-ttu-id="f2f5a-126">.NET uyumluluğu tanılama</span><span class="sxs-lookup"><span data-stu-id="f2f5a-126">.NET Compatibility Diagnostics</span></span>

<span data-ttu-id="f2f5a-127">.NET uyumluluğu tanılama Roslyn destekli çözümleyiciler, .NET Framework sürümleri arasında uygulama uyumluluğu sorunları tanımlamaya yardımcı olan.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-127">The .NET Compatibility Diagnostics are Roslyn-powered analyzers that help identify application compatibility issues between versions of the .NET Framework.</span></span> <span data-ttu-id="f2f5a-128">Yalnızca bir alt özel tüm geçiş uygulanacak rağmen bu liste tüm kullanılabilir çözümleyiciler içerir.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-128">This list contains all of the analyzers available, although only a subset will apply to any specific migration.</span></span> <span data-ttu-id="f2f5a-129">Çözümleyiciler hangi sorunların planlanan geçiş için geçerlidir ve yalnızca bu belirir belirler.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-129">The analyzers will determine which issues are applicable for the planned migration and will only surface those.</span></span>

<span data-ttu-id="f2f5a-130">Her sorun aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="f2f5a-130">Each issue includes the following information:</span></span>

-   <span data-ttu-id="f2f5a-131">Önceki bir sürümden nelerin değiştiğini açıklaması.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-131">The description of what has changed from a previous version.</span></span>

-   <span data-ttu-id="f2f5a-132">Nasıl değişiklik müşteriler ve herhangi bir geçici çözüm sürümleri arasında uyumluluğu korumak kullanılabilir olup etkiler.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-132">How the change affects customers and whether any workarounds are available to preserve compatibility across versions.</span></span>

-   <span data-ttu-id="f2f5a-133">Değişikliğin ne kadar önemli olduğunu'nin bir değerlendirme.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-133">An assessment of how important the change is.</span></span> <span data-ttu-id="f2f5a-134">Uygulama uyumluluk sorunu kategorilere gibi:</span><span class="sxs-lookup"><span data-stu-id="f2f5a-134">Application compatibility issue are categorized as follows:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="f2f5a-135">Ana</span><span class="sxs-lookup"><span data-stu-id="f2f5a-135">Major</span></span>|<span data-ttu-id="f2f5a-136">Çok sayıda uygulamaları etkiler veya önemli kodunun değiştirilmesini gerektirir önemli bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-136">A significant change that affects a large number of apps or requires substantial modification of code.</span></span>|
    |<span data-ttu-id="f2f5a-137">Küçük</span><span class="sxs-lookup"><span data-stu-id="f2f5a-137">Minor</span></span>|<span data-ttu-id="f2f5a-138">Az sayıda uygulamaları etkiler veya ikincil kodunun değiştirilmesini gerektiren bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-138">A change that affects a small number of apps or that requires minor modification of code.</span></span>|
    |<span data-ttu-id="f2f5a-139">Uç durum</span><span class="sxs-lookup"><span data-stu-id="f2f5a-139">Edge case</span></span>|<span data-ttu-id="f2f5a-140">Uygulamalar belirli, genel olarak görülmez senaryoları altında etkileyen bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-140">A change that affects apps under very specific, uncommon scenarios.</span></span>|
    |<span data-ttu-id="f2f5a-141">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="f2f5a-141">Transparent</span></span>|<span data-ttu-id="f2f5a-142">Bir değişiklik uygulama geliştiricisi veya kullanıcı belirgin hiçbir etkisi olmadan.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-142">A change with no noticeable effect on the application's developer or user.</span></span>|

-   <span data-ttu-id="f2f5a-143">Sürüm değişikliği ilk framework görüntülendiğinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-143">Version indicates when the change first appears in the framework.</span></span> <span data-ttu-id="f2f5a-144">Bazı değişiklikler belirli bir sürümünde sunulan ve bir sonraki sürümde geri; Bu da gösterilir.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-144">Some of the changes are introduced in a particular version and reverted in a later version; that is indicated as well.</span></span>

-   <span data-ttu-id="f2f5a-145">Değişiklik türü:</span><span class="sxs-lookup"><span data-stu-id="f2f5a-145">The type of change:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="f2f5a-146">Yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="f2f5a-146">Retargeting</span></span>|<span data-ttu-id="f2f5a-147">Değişiklik yeni bir .NET Framework sürümünü hedefleyecek şekilde derlenir uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-147">The change affects apps that are recompiled to target a new version of the .NET Framework.</span></span>|
    |<span data-ttu-id="f2f5a-148">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="f2f5a-148">Runtime</span></span>|<span data-ttu-id="f2f5a-149">Bu değişiklik, .NET Framework'ün önceki bir sürümünü hedefleyen ancak sonraki bir sürümünü çalıştıran mevcut bir uygulamayı etkiler.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-149">The change affects an existing app that targets a previous version of the .NET Framework but runs on a later version.</span></span>|

-   <span data-ttu-id="f2f5a-150">Etkilenen API'leri, varsa.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-150">The affected APIS, if any.</span></span>

-   <span data-ttu-id="f2f5a-151">Kullanılabilir tanılama kimlikleri</span><span class="sxs-lookup"><span data-stu-id="f2f5a-151">The IDs of the available diagnostics</span></span>

## <a name="usage"></a><span data-ttu-id="f2f5a-152">Kullanım</span><span class="sxs-lookup"><span data-stu-id="f2f5a-152">Usage</span></span>
<span data-ttu-id="f2f5a-153">Başlamak için aşağıdaki uyumluluk değişiklik türünü seçin:</span><span class="sxs-lookup"><span data-stu-id="f2f5a-153">To begin, select the type of compatibility change below:</span></span>

* [<span data-ttu-id="f2f5a-154">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="f2f5a-154">Retargeting Changes</span></span>](./retargeting/index.md)
* [<span data-ttu-id="f2f5a-155">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="f2f5a-155">Runtime Changes</span></span>](./runtime/index.md)


## <a name="see-also"></a><span data-ttu-id="f2f5a-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2f5a-156">See Also</span></span>

* [<span data-ttu-id="f2f5a-157">Sürümler ve Bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="f2f5a-157">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
* [<span data-ttu-id="f2f5a-158">Yenilikler</span><span class="sxs-lookup"><span data-stu-id="f2f5a-158">What's New</span></span>](../../../docs/framework/whats-new/index.md)
* [<span data-ttu-id="f2f5a-159">Sınıf Kitaplığında Artık Kullanılmayanlar</span><span class="sxs-lookup"><span data-stu-id="f2f5a-159">What's Obsolete in the Class Library</span></span>](../../../docs/framework/whats-new/whats-obsolete.md)
