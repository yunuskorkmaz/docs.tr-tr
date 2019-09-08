---
title: Fusion Genel Statik İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a8f15bc862c0486311960f7567c49424859846e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795320"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="385e3-102">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="385e3-102">Fusion Global Static Functions</span></span>
<span data-ttu-id="385e3-103">Bu bölümde Fusion API 'sinin kullandığı yönetilmeyen genel statik işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="385e3-103">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="385e3-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="385e3-104">In This Section</span></span>  
 [<span data-ttu-id="385e3-105">ClearDownloadCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-105">ClearDownloadCache Function</span></span>](cleardownloadcache-function.md)  
 <span data-ttu-id="385e3-106">İndirilen derlemelerin genel derleme önbelleğini temizler.</span><span class="sxs-lookup"><span data-stu-id="385e3-106">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="385e3-107">CompareAssemblyIdentity İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-107">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)  
 <span data-ttu-id="385e3-108">, Eşdeğer olup olmadıklarını anlamak için iki derleme kimliğini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="385e3-108">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="385e3-109">CreateApplicationContext İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-109">CreateApplicationContext Function</span></span>](createapplicationcontext-function.md)  
 <span data-ttu-id="385e3-110">Yalnızca dahili.</span><span class="sxs-lookup"><span data-stu-id="385e3-110">Internal only.</span></span> <span data-ttu-id="385e3-111">(Bu işlev .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="385e3-111">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="385e3-112">CreateAssemblyCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-112">CreateAssemblyCache Function</span></span>](createassemblycache-function.md)  
 <span data-ttu-id="385e3-113">Genel derleme önbelleğini temsil eden yeni bir [IAssemblyCache](iassemblycache-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="385e3-113">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="385e3-114">CreateAssemblyEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-114">CreateAssemblyEnum Function</span></span>](createassemblyenum-function.md)  
 <span data-ttu-id="385e3-115">Belirtilen derlemede bulunan nesnelerin listesini temsil eden bir [IAssemblyEnum](iassemblyenum-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="385e3-115">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="385e3-116">CreateAssemblyNameObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-116">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)  
 <span data-ttu-id="385e3-117">Belirtilen ada sahip derlemenin benzersiz kimliğini temsil eden bir [IAssemblyName](iassemblyname-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="385e3-117">Gets a pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="385e3-118">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-118">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)  
 <span data-ttu-id="385e3-119">Belirtilen dosya için bir geçmiş okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="385e3-119">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="385e3-120">CreateInstallReferenceEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-120">CreateInstallReferenceEnum Function</span></span>](createinstallreferenceenum-function.md)  
 <span data-ttu-id="385e3-121">Belirtilen derlemeye ait başvuruların bir listesini temsil eden bir [IInstallReferenceEnum](iinstallreferenceenum-interface.md) örneği için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="385e3-121">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="385e3-122">GetAppIdAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-122">GetAppIdAuthority Function</span></span>](getappidauthority-function.md)  
 <span data-ttu-id="385e3-123">Uygulama kimlikleri ve başvuruları için anahtarları yöneten bir [ıappidaduthority](iappidauthority-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="385e3-123">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="385e3-124">GetAssemblyIdentityFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-124">GetAssemblyIdentityFromFile Function</span></span>](getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="385e3-125">Belirtilen dosya yolundaki derlemede belirtilen `IUnknown` `IID` bir nesneye yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="385e3-125">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="385e3-126">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-126">GetCachePath Function</span></span>](getcachepath-function.md)  
 <span data-ttu-id="385e3-127">Belirtilen bayrakları kullanarak önbelleğe alınmış derlemenin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="385e3-127">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="385e3-128">GetHistoryFileDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-128">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)  
 <span data-ttu-id="385e3-129">Uygulama geçmişi dizininin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="385e3-129">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="385e3-130">GetIdentityAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-130">GetIdentityAuthority Function</span></span>](getidentityauthority-function.md)  
 <span data-ttu-id="385e3-131">Kod nesneleri için anahtarları yöneten bir [IIdentityAuthority](iidentityauthority-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="385e3-131">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="385e3-132">IsFrameworkAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-132">IsFrameworkAssembly Function</span></span>](isframeworkassembly-function.md)  
 <span data-ttu-id="385e3-133">Belirtilen derlemenin yönetilip yönetilmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="385e3-133">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="385e3-134">NukeDownloadedCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-134">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)  
 <span data-ttu-id="385e3-135">Ortak dil çalışma zamanı indirme önbelleğini siler.</span><span class="sxs-lookup"><span data-stu-id="385e3-135">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="385e3-136">PreBindAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="385e3-136">PreBindAssemblyEx Function</span></span>](prebindassemblyex-function.md)  
 <span data-ttu-id="385e3-137">Bir derlemenin ilke sonrası görünen adını alır.</span><span class="sxs-lookup"><span data-stu-id="385e3-137">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="385e3-138">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="385e3-138">Related Sections</span></span>  
 [<span data-ttu-id="385e3-139">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="385e3-139">Fusion Interfaces</span></span>](fusion-interfaces.md)  
  
 [<span data-ttu-id="385e3-140">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="385e3-140">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="385e3-141">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="385e3-141">Fusion Structures</span></span>](fusion-structures.md)  
  
 [<span data-ttu-id="385e3-142">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="385e3-142">Global Assembly Cache</span></span>](../../app-domains/gac.md)
