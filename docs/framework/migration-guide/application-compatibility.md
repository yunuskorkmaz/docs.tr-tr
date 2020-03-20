---
title: Çalışma süresi ve değişiklikleri yeniden hedefleme - .NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73196705"
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="02948-102">.NET Çerçevesi'nde uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="02948-102">Application compatibility in the .NET Framework</span></span>

<span data-ttu-id="02948-103">Uyumluluk her .NET sürümü için önemli bir hedeftir.</span><span class="sxs-lookup"><span data-stu-id="02948-103">Compatibility is an important goal of each .NET release.</span></span> <span data-ttu-id="02948-104">Uyumluluk, her sürümün katkı maddesi olmasını sağlar, böylece önceki sürümler çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="02948-104">Compatibility ensures that each version is additive, so previous versions will continue to work.</span></span> <span data-ttu-id="02948-105">Diğer taraftan, önceki işlevlerde yapılan değişiklikler (örneğin, performansı artırmak, güvenlik sorunlarını gidermek veya hataları gidermek için) varolan kodda veya daha sonraki bir sürüm altında çalışan varolan uygulamalarda uyumluluk sorunlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="02948-105">On the other hand, changes to previous functionality (for example, to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span>

<span data-ttu-id="02948-106">Her uygulama .NET Framework'ün belirli bir sürümünü şu şekilde hedefler:</span><span class="sxs-lookup"><span data-stu-id="02948-106">Each app targets a specific version of the .NET Framework by:</span></span>

- <span data-ttu-id="02948-107">Visual Studio'da bir hedef çerçevesi tanımlama.</span><span class="sxs-lookup"><span data-stu-id="02948-107">Defining a target framework in Visual Studio.</span></span>
- <span data-ttu-id="02948-108">Proje dosyasında hedef çerçevenin belirtilmesi.</span><span class="sxs-lookup"><span data-stu-id="02948-108">Specifying the target framework in a project file.</span></span>
- <span data-ttu-id="02948-109">Kaynak koduna a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> uygulama.</span><span class="sxs-lookup"><span data-stu-id="02948-109">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="02948-110">.NET Framework'ün bir sürümünden diğerine geçiş yaparken göz önünde bulundurulması gereken iki tür değişiklik vardır:</span><span class="sxs-lookup"><span data-stu-id="02948-110">When migrating from one version of the .NET Framework to another, there are two types of changes to consider:</span></span>

- [<span data-ttu-id="02948-111">Çalışma zamanı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="02948-111">Runtime changes</span></span>](#runtime-changes)
- [<span data-ttu-id="02948-112">Değişiklikleri yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="02948-112">Retargeting changes</span></span>](#retargeting-changes)

## <a name="runtime-changes"></a><span data-ttu-id="02948-113">Çalışma zamanı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="02948-113">Runtime changes</span></span>

<span data-ttu-id="02948-114">Çalışma zamanı sorunları, bir makineye yeni bir çalışma zamanı yerleştirildiğinde ve uygulamanın davranış değişiklikleri olduğunda ortaya çıkan sorunlardır.</span><span class="sxs-lookup"><span data-stu-id="02948-114">Runtime issues are those that arise when a new runtime is placed on a machine and an app's behavior changes.</span></span> <span data-ttu-id="02948-115">.NET Framework, hedeflenenden daha yeni bir sürümde çalışırken, eski hedeflenen sürümü taklit etmek için *tuhaf davranışları* kullanır.</span><span class="sxs-lookup"><span data-stu-id="02948-115">When running on a newer version than what was targeted, the .NET Framework uses *quirked* behavior to mimic the older targeted version.</span></span> <span data-ttu-id="02948-116">Uygulama yeni sürümde çalışır, ancak eski sürümde çalışıyormuş gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="02948-116">The app runs on the newer version but acts as if it's running on the older version.</span></span> <span data-ttu-id="02948-117">.NET Framework sürümleri arasındaki uyumluluk sorunlarının çoğu bu tuhafmodel aracılığıyla azaltılır.</span><span class="sxs-lookup"><span data-stu-id="02948-117">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span> <span data-ttu-id="02948-118">Örneğin, .NET Framework 4.0 için bir ikili derlenmişse ancak .NET Framework 4.5 veya sonraki bir makinede çalışıyorsa, .NET Framework 4.0 uyumluluk modunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="02948-118">For example, if a binary was compiled for .NET Framework 4.0 but runs on a machine with .NET Framework 4.5 or later, it runs in .NET Framework 4.0 compatibility mode.</span></span> <span data-ttu-id="02948-119">Bu, sonraki sürümdeki değişikliklerin çoğunun ikiliyi etkilemeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="02948-119">This means that many of the changes in the later version don't affect the binary.</span></span>

<span data-ttu-id="02948-120">.NET Framework'ün bir uygulamanın hedeflenebelirlediği sürümü, kodun çalıştığı uygulama etki alanı için giriş derlemesinin hedef sürümü tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="02948-120">The version of the .NET Framework that an application targets is determined by the target version of the entry assembly for the application domain that the code runs in.</span></span> <span data-ttu-id="02948-121">Bu uygulama etki alanına yüklenen tüm ek derlemeler bu sürümü hedeflemektedir.</span><span class="sxs-lookup"><span data-stu-id="02948-121">All additional assemblies loaded in that application domain target that version.</span></span> <span data-ttu-id="02948-122">Örneğin, yürütülebilir bir durumda, yürütülebilir hedeflerin sürümü, bu uygulama etki alanında çalışan tüm derlemeler uyumluluk modudur.</span><span class="sxs-lookup"><span data-stu-id="02948-122">For example, in the case of an executable, the version that the executable targets is the compatibility mode all assemblies in that application domain run under.</span></span>

<span data-ttu-id="02948-123">Ortamınız için geçerli olan çalışma zamanı değişikliklerinin listesini görmek için, şu anda hedeflemekte olduğunuz .NET Framework sürümünü ve daha sonra geçiş yapmak istediğiniz sürümü seçin:</span><span class="sxs-lookup"><span data-stu-id="02948-123">To see a list of runtime changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a><span data-ttu-id="02948-124">Yeniden hedefleme değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="02948-124">Retargeting changes</span></span>

<span data-ttu-id="02948-125">Yeniden hedefleme değişiklikleri, derleme yeni bir sürümü hedeflemek üzere yeniden derlendiğinde ortaya çıkan değişikliklerdir.</span><span class="sxs-lookup"><span data-stu-id="02948-125">Retargeting changes are those that arise when an assembly is recompiled to target a newer version.</span></span> <span data-ttu-id="02948-126">Daha yeni bir sürümü hedeflemek, derlemenin eski özellikler için olası uyumluluk sorunlarının yanı sıra yeni özellikleri de seçmesi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="02948-126">Targeting a newer version means the assembly opts into the new features as well as potential compatibility issues for old features.</span></span>

<span data-ttu-id="02948-127">Ortamınız için geçerli olan yeniden hedefleme değişikliklerinin listesini görmek için, şu anda hedeflemekte olduğunuz .NET Framework sürümünü ve daha sonra geçiş yapmak istediğiniz sürümü seçin:</span><span class="sxs-lookup"><span data-stu-id="02948-127">To see a list of retargeting changes that apply to your environment, select the .NET Framework version you're currently targeting and then the version you wish to migrate to:</span></span>

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a><span data-ttu-id="02948-128">Etki sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="02948-128">Impact classification</span></span>

<span data-ttu-id="02948-129">Çalışma zamanı ve değişiklikleri yeniden hedeflemeyi açıklayan konularda, örneğin, [4,7.2'den 4,8'e geçiş için değişiklikleri yeniden hedeflemek,](retargeting/4.7.2-4.8.md)tek tek öğeler beklenen etkilerine göre aşağıdaki gibi sınıflandırılır:</span><span class="sxs-lookup"><span data-stu-id="02948-129">In the topics that describe runtime and retargeting changes, for example, [Retargeting changes for migrating from 4.7.2 to 4.8](retargeting/4.7.2-4.8.md), individual items are classified by their expected impact as follows:</span></span>

<span data-ttu-id="02948-130">**Büyük**</span><span class="sxs-lookup"><span data-stu-id="02948-130">**Major**</span></span>\
<span data-ttu-id="02948-131">Çok sayıda uygulamayı etkileyen veya önemli ölçüde kod değişikliği gerektiren önemli bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="02948-131">A significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="02948-132">**Küçük**</span><span class="sxs-lookup"><span data-stu-id="02948-132">**Minor**</span></span>\
<span data-ttu-id="02948-133">Az sayıda uygulamayı etkileyen veya kodda küçük değişiklikler gerektiren bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="02948-133">A change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="02948-134">**Kenar kılıfı**</span><span class="sxs-lookup"><span data-stu-id="02948-134">**Edge case**</span></span>\
<span data-ttu-id="02948-135">Yaygın olmayan çok özel senaryolar altında uygulamaları etkileyen bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="02948-135">A change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="02948-136">**Şeffaf**</span><span class="sxs-lookup"><span data-stu-id="02948-136">**Transparent**</span></span>\
<span data-ttu-id="02948-137">Uygulamanın geliştiricisi veya kullanıcısı üzerinde gözle görülür bir etkisi olmayan bir değişiklik.</span><span class="sxs-lookup"><span data-stu-id="02948-137">A change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="02948-138">Bu değişiklik nedeniyle uygulamada bir düzenleme yapılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="02948-138">The app should not require modification because of this change.</span></span>

## <a name="see-also"></a><span data-ttu-id="02948-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02948-139">See also</span></span>

- [<span data-ttu-id="02948-140">Sürümler ve bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="02948-140">Versions and dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="02948-141">Yenilikler</span><span class="sxs-lookup"><span data-stu-id="02948-141">What's new</span></span>](../whats-new/index.md)
- [<span data-ttu-id="02948-142">Ne eski</span><span class="sxs-lookup"><span data-stu-id="02948-142">What's obsolete</span></span>](../whats-new/whats-obsolete.md)
