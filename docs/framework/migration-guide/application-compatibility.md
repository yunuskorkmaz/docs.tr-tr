---
title: Çalışma zamanı ve yeniden hedefleme değişiklikleri-.NET Framework
description: .NET Framework 'de uygulama uyumluluğu ve başka bir sürüme geçiş yaparken çalışma zamanı ve yeniden hedefleme değişikliklerinin nasıl etkilendiğine ilişkin bilgi edinin.
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: 26f36dd34c6c5ecae8fc5ab373ff60d9e56f8245
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475495"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="a93dc-103">.NET Framework uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="a93dc-103">Application compatibility in the .NET Framework</span></span>

<span data-ttu-id="a93dc-104">Uyumluluk, her bir .NET sürümünün önemli bir hedefidir.</span><span class="sxs-lookup"><span data-stu-id="a93dc-104">Compatibility is an important goal of each .NET release.</span></span> <span data-ttu-id="a93dc-105">Uyumluluk, her sürümün eklenebilir olmasını sağlar, bu nedenle önceki sürümler çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="a93dc-105">Compatibility ensures that each version is additive, so previous versions will continue to work.</span></span> <span data-ttu-id="a93dc-106">Öte yandan, önceki işlevlerde yapılan değişiklikler (örneğin, performansı artırmak, güvenlik sorunlarını gidermek veya hataları gidermek için), mevcut koddaki veya sonraki bir sürümde çalışan mevcut uygulamalarda uyumluluk sorunlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a93dc-106">On the other hand, changes to previous functionality (for example, to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span>

<span data-ttu-id="a93dc-107">Her uygulama .NET Framework belirli bir sürümünü hedefler:</span><span class="sxs-lookup"><span data-stu-id="a93dc-107">Each app targets a specific version of the .NET Framework by:</span></span>

- <span data-ttu-id="a93dc-108">Visual Studio 'da hedef çerçeve tanımlama.</span><span class="sxs-lookup"><span data-stu-id="a93dc-108">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="a93dc-109">Hedef Framework bir proje dosyasında belirtiliyor.</span><span class="sxs-lookup"><span data-stu-id="a93dc-109">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="a93dc-110"><xref:System.Runtime.Versioning.TargetFrameworkAttribute>Kaynak koda uygulama.</span><span class="sxs-lookup"><span data-stu-id="a93dc-110">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="a93dc-111">.NET Framework bir sürümünden diğerine geçiş yaparken göz önünde bulundurmanız gereken iki tür değişiklik vardır:</span><span class="sxs-lookup"><span data-stu-id="a93dc-111">When migrating from one version of the .NET Framework to another, there are two types of changes to consider:</span></span>

- [<span data-ttu-id="a93dc-112">Çalışma zamanı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="a93dc-112">Runtime changes</span></span>](#runtime-changes)
- [<span data-ttu-id="a93dc-113">Yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="a93dc-113">Retargeting changes</span></span>](#retargeting-changes)

## <a name="runtime-changes"></a><span data-ttu-id="a93dc-114">Çalışma zamanı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="a93dc-114">Runtime changes</span></span>

<span data-ttu-id="a93dc-115">Çalışma zamanı sorunları, bir makineye yeni bir çalışma zamanı yerleştirildiğinde ve uygulamanın davranış değiştiğinde ortaya çıkabilecek olanlardır.</span><span class="sxs-lookup"><span data-stu-id="a93dc-115">Runtime issues are those that arise when a new runtime is placed on a machine and an app's behavior changes.</span></span> <span data-ttu-id="a93dc-116">Hedefe göre daha yeni bir sürümde çalışırken, .NET Framework, eski hedeflenen sürümü taklit etmek için *olağandışı* davranışı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a93dc-116">When running on a newer version than what was targeted, the .NET Framework uses *quirked* behavior to mimic the older targeted version.</span></span> <span data-ttu-id="a93dc-117">Uygulama daha yeni bir sürümde çalışır, ancak eski sürümde çalışıyor gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="a93dc-117">The app runs on the newer version but acts as if it's running on the older version.</span></span> <span data-ttu-id="a93dc-118">.NET Framework sürümleri arasındaki uyumluluk sorunlarının birçoğu, bu olağandışı model aracılığıyla azaltıldığında.</span><span class="sxs-lookup"><span data-stu-id="a93dc-118">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="a93dc-119">Örneğin, bir ikili dosya .NET Framework 4,0 için derlenmişse, ancak .NET Framework 4,5 veya sonraki bir sürüme sahip bir makinede çalışıyorsa, .NET Framework 4,0 uyumluluk modunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="a93dc-119">For example, if a binary was compiled for .NET Framework 4.0 but runs on a machine with .NET Framework 4.5 or later, it runs in .NET Framework 4.0 compatibility mode.</span></span> <span data-ttu-id="a93dc-120">Bu, sonraki sürümdeki birçok değişikliğin ikilisini etkilemediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a93dc-120">This means that many of the changes in the later version don't affect the binary.</span></span>

<span data-ttu-id="a93dc-121">Uygulamanın hedeflediği .NET Framework sürümü, kodun çalıştığı uygulama etki alanı için giriş derlemesinin hedef sürümü tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a93dc-121">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code runs in.</span></span> <span data-ttu-id="a93dc-122">Bu uygulama etki alanında yüklü olan tüm ek derlemeler bu sürümü hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="a93dc-122">All additional assemblies loaded in that application domain target that version.</span></span> <span data-ttu-id="a93dc-123">Örneğin, yürütülebilir dosya durumunda, yürütülebilir dosyanın hedeflediği sürüm, bu uygulama etki alanındaki tüm derlemeler altında çalışır.</span><span class="sxs-lookup"><span data-stu-id="a93dc-123">For example, in the case of an executable, the version that the executable targets is the compatibility mode all assemblies in that application domain run under.</span></span>

<span data-ttu-id="a93dc-124">Ortamınıza uygulanan çalışma zamanı değişikliklerinin bir listesini görmek için, şu anda hedeflediğiniz .NET Framework sürümünü ve ardından geçirmek istediğiniz sürümü seçin:</span><span class="sxs-lookup"><span data-stu-id="a93dc-124">To see a list of runtime changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a><span data-ttu-id="a93dc-125">Yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="a93dc-125">Retargeting changes</span></span>

<span data-ttu-id="a93dc-126">Yeniden hedefleme değişiklikleri, bir derleme daha yeni bir sürümü hedeflemek için yeniden derleniyorsa ortaya çıkabilecek olanlardır.</span><span class="sxs-lookup"><span data-stu-id="a93dc-126">Retargeting changes are those that arise when an assembly is recompiled to target a newer version.</span></span> <span data-ttu-id="a93dc-127">Daha yeni bir sürümü hedeflemek, derlemenin yeni özelliklerin yanı sıra eski özellikler için olası uyumluluk sorunlarını kabul etmesinin anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a93dc-127">Targeting a newer version means the assembly opts into the new features as well as potential compatibility issues for old features.</span></span>

<span data-ttu-id="a93dc-128">Ortamınız için geçerli olan yeniden hedefleme değişikliklerinin listesini görmek için, şu anda hedeflendiği .NET Framework sürümünü ve ardından geçiş yapmak istediğiniz sürümü seçin:</span><span class="sxs-lookup"><span data-stu-id="a93dc-128">To see a list of retargeting changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a><span data-ttu-id="a93dc-129">Etki sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="a93dc-129">Impact classification</span></span>

<span data-ttu-id="a93dc-130">Çalışma zamanı ve yeniden hedefleme değişikliklerini tanımlayan konularda, örneğin, [4.7.2 ' den 4,8 ' e geçiş Için yeniden hedefleme değişiklikleri](retargeting/4.7.2-4.8.md), tek tek öğeler aşağıdaki şekilde beklenen etkilerden sınıflandırılmaktadır:</span><span class="sxs-lookup"><span data-stu-id="a93dc-130">In the topics that describe runtime and retargeting changes, for example, [Retargeting changes for migrating from 4.7.2 to 4.8](retargeting/4.7.2-4.8.md), individual items are classified by their expected impact as follows:</span></span>

<span data-ttu-id="a93dc-131">**Leri**</span><span class="sxs-lookup"><span data-stu-id="a93dc-131">**Major**</span></span>\
<span data-ttu-id="a93dc-132">Çok sayıda uygulamayı etkileyen veya kodun önemli bir şekilde değiştirilmesini gerektiren önemli bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="a93dc-132">A significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="a93dc-133">**Bazı**</span><span class="sxs-lookup"><span data-stu-id="a93dc-133">**Minor**</span></span>\
<span data-ttu-id="a93dc-134">Az sayıda uygulamayı etkileyen veya küçük bir kod değişikliği gerektiren bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="a93dc-134">A change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="a93dc-135">**Kenar durumu**</span><span class="sxs-lookup"><span data-stu-id="a93dc-135">**Edge case**</span></span>\
<span data-ttu-id="a93dc-136">Uygulamaları, yaygın olmayan çok özel senaryolar altında etkileyen bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="a93dc-136">A change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="a93dc-137">**Gerçekletir**</span><span class="sxs-lookup"><span data-stu-id="a93dc-137">**Transparent**</span></span>\
<span data-ttu-id="a93dc-138">Uygulamanın geliştiricisi veya kullanıcısı üzerinde belirgin bir etkiye sahip olmayan bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="a93dc-138">A change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="a93dc-139">Bu değişiklik nedeniyle uygulamada bir düzenleme yapılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a93dc-139">The app should not require modification because of this change.</span></span>

## <a name="see-also"></a><span data-ttu-id="a93dc-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a93dc-140">See also</span></span>

- [<span data-ttu-id="a93dc-141">Sürümler ve bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="a93dc-141">Versions and dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="a93dc-142">Yenilikler</span><span class="sxs-lookup"><span data-stu-id="a93dc-142">What's new</span></span>](../whats-new/index.md)
- [<span data-ttu-id="a93dc-143">Artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="a93dc-143">What's obsolete</span></span>](../whats-new/whats-obsolete.md)
