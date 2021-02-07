---
description: 'Daha fazla bilgi edinin: Fusion genel statik Işlevleri'
title: Fusion Genel Statik İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
ms.openlocfilehash: c696908f72d67ecff5e7383e7a2754dd5436b819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761089"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="9cafe-103">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9cafe-103">Fusion Global Static Functions</span></span>

<span data-ttu-id="9cafe-104">Bu bölümde Fusion API 'sinin kullandığı yönetilmeyen genel statik işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9cafe-104">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9cafe-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9cafe-105">In This Section</span></span>  

 [<span data-ttu-id="9cafe-106">ClearDownloadCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-106">ClearDownloadCache Function</span></span>](cleardownloadcache-function.md)  
 <span data-ttu-id="9cafe-107">İndirilen derlemelerin genel derleme önbelleğini temizler.</span><span class="sxs-lookup"><span data-stu-id="9cafe-107">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="9cafe-108">CompareAssemblyIdentity İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-108">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)  
 <span data-ttu-id="9cafe-109">, Eşdeğer olup olmadıklarını anlamak için iki derleme kimliğini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="9cafe-109">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="9cafe-110">CreateApplicationContext İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-110">CreateApplicationContext Function</span></span>](createapplicationcontext-function.md)  
 <span data-ttu-id="9cafe-111">Sadece dahili.</span><span class="sxs-lookup"><span data-stu-id="9cafe-111">Internal only.</span></span> <span data-ttu-id="9cafe-112">(Bu işlev .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)</span><span class="sxs-lookup"><span data-stu-id="9cafe-112">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="9cafe-113">CreateAssemblyCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-113">CreateAssemblyCache Function</span></span>](createassemblycache-function.md)  
 <span data-ttu-id="9cafe-114">Genel derleme önbelleğini temsil eden yeni bir [IAssemblyCache](iassemblycache-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="9cafe-114">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="9cafe-115">CreateAssemblyEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-115">CreateAssemblyEnum Function</span></span>](createassemblyenum-function.md)  
 <span data-ttu-id="9cafe-116">Belirtilen derlemede bulunan nesnelerin listesini temsil eden bir [IAssemblyEnum](iassemblyenum-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="9cafe-116">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="9cafe-117">CreateAssemblyNameObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-117">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)  
 <span data-ttu-id="9cafe-118">Belirtilen ada sahip derlemenin benzersiz kimliğini temsil eden bir [IAssemblyName](iassemblyname-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="9cafe-118">Gets a pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="9cafe-119">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-119">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)  
 <span data-ttu-id="9cafe-120">Belirtilen dosya için bir geçmiş okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9cafe-120">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="9cafe-121">CreateInstallReferenceEnum İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-121">CreateInstallReferenceEnum Function</span></span>](createinstallreferenceenum-function.md)  
 <span data-ttu-id="9cafe-122">Belirtilen derlemeye ait başvuruların bir listesini temsil eden bir [IInstallReferenceEnum](iinstallreferenceenum-interface.md) örneği için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="9cafe-122">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="9cafe-123">GetAppIdAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-123">GetAppIdAuthority Function</span></span>](getappidauthority-function.md)  
 <span data-ttu-id="9cafe-124">Uygulama kimlikleri ve başvuruları için anahtarları yöneten bir [ıappidaduthority](iappidauthority-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="9cafe-124">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="9cafe-125">GetAssemblyIdentityFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-125">GetAssemblyIdentityFromFile Function</span></span>](getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="9cafe-126">`IUnknown`Belirtilen dosya yolundaki derlemede belirtilen bir nesneye yönelik bir işaretçi alır `IID` .</span><span class="sxs-lookup"><span data-stu-id="9cafe-126">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="9cafe-127">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-127">GetCachePath Function</span></span>](getcachepath-function.md)  
 <span data-ttu-id="9cafe-128">Belirtilen bayrakları kullanarak önbelleğe alınmış derlemenin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="9cafe-128">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="9cafe-129">GetHistoryFileDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-129">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)  
 <span data-ttu-id="9cafe-130">Uygulama geçmişi dizininin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="9cafe-130">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="9cafe-131">GetIdentityAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-131">GetIdentityAuthority Function</span></span>](getidentityauthority-function.md)  
 <span data-ttu-id="9cafe-132">Kod nesneleri için anahtarları yöneten bir [IIdentityAuthority](iidentityauthority-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="9cafe-132">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="9cafe-133">IsFrameworkAssembly İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-133">IsFrameworkAssembly Function</span></span>](isframeworkassembly-function.md)  
 <span data-ttu-id="9cafe-134">Belirtilen derlemenin yönetilip yönetilmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="9cafe-134">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="9cafe-135">NukeDownloadedCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-135">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)  
 <span data-ttu-id="9cafe-136">Ortak dil çalışma zamanı indirme önbelleğini siler.</span><span class="sxs-lookup"><span data-stu-id="9cafe-136">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="9cafe-137">PreBindAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="9cafe-137">PreBindAssemblyEx Function</span></span>](prebindassemblyex-function.md)  
 <span data-ttu-id="9cafe-138">Bir derlemenin ilke sonrası görünen adını alır.</span><span class="sxs-lookup"><span data-stu-id="9cafe-138">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9cafe-139">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9cafe-139">Related Sections</span></span>  

 [<span data-ttu-id="9cafe-140">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9cafe-140">Fusion Interfaces</span></span>](fusion-interfaces.md)  
  
 [<span data-ttu-id="9cafe-141">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="9cafe-141">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="9cafe-142">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="9cafe-142">Fusion Structures</span></span>](fusion-structures.md)  
  
 [<span data-ttu-id="9cafe-143">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="9cafe-143">Global Assembly Cache</span></span>](../../app-domains/gac.md)
