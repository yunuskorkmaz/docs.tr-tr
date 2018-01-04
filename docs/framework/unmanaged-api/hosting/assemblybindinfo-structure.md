---
title: "AssemblyBindInfo Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyBindInfo
helpviewer_keywords: AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bdf76b95e80d5d4d96d2b5ed8236018147167905
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="fdb42-102">AssemblyBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="fdb42-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="fdb42-103">Başvurulan derlemeyi hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdb42-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdb42-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdb42-104">Syntax</span></span>  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="fdb42-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fdb42-105">Members</span></span>  
  
|<span data-ttu-id="fdb42-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fdb42-106">Member</span></span>|<span data-ttu-id="fdb42-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdb42-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="fdb42-108">İçin benzersiz bir tanımlayıcı `IStream` yapılan bir çağrı tarafından döndürülen [Ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), başvurulan derlemeyi yüklenecek olan gelen.</span><span class="sxs-lookup"><span data-stu-id="fdb42-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="fdb42-109">Başvurulan derlemeyi için benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="fdb42-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="fdb42-110">Başvurulan derlemeyi sonra herhangi bir bağlama ilke değeri uygulama için tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="fdb42-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="fdb42-111">Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hangi sürüm oluşturma ilkeleri varsa, başvurulan derlemeyi uygulanması gereken gösteren değerler.</span><span class="sxs-lookup"><span data-stu-id="fdb42-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdb42-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdb42-112">Remarks</span></span>  
 <span data-ttu-id="fdb42-113">Benzersiz tanımlayıcı ana bilgisayar kaynakları `dwAppDomainId` ortak dil çalışma zamanı (CLR) için.</span><span class="sxs-lookup"><span data-stu-id="fdb42-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="fdb42-114">Çağrı sonra `IHostAssemblyStore::ProvideAssembly` döndürür, çalışma zamanı belirlemek için tanımlayıcısını kullanır olup olmadığını içeriğini `IStream` eşlenmedi.</span><span class="sxs-lookup"><span data-stu-id="fdb42-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="fdb42-115">Bu durumda, çalışma zamanı akış yeniden eşleme yerine var olan kopyasını yükler.</span><span class="sxs-lookup"><span data-stu-id="fdb42-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="fdb42-116">Akışlar döndürülen için çalışma zamanı bu tanımlayıcı ayrıca arama anahtar olarak kullanır. çağrılar [Ihostassemblystore::providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="fdb42-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="fdb42-117">Bu nedenle, tanımlayıcı derleme isteklerini ve modül isteği için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fdb42-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdb42-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fdb42-118">Requirements</span></span>  
 <span data-ttu-id="fdb42-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdb42-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdb42-120">**Başlık:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="fdb42-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="fdb42-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fdb42-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdb42-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdb42-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb42-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fdb42-123">See Also</span></span>  
 [<span data-ttu-id="fdb42-124">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="fdb42-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="fdb42-125">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdb42-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="fdb42-126">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdb42-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="fdb42-127">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdb42-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="fdb42-128">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdb42-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="fdb42-129">ModuleBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="fdb42-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
