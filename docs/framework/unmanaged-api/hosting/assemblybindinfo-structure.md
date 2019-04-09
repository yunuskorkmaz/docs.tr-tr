---
title: AssemblyBindInfo Yapısı
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce79987c7fcf45b8d10dcc4613e053ee735941de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112820"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="dd41e-102">AssemblyBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="dd41e-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="dd41e-103">Başvurulan derleme hakkında ayrıntılı bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd41e-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd41e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd41e-104">Syntax</span></span>  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="dd41e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="dd41e-105">Members</span></span>  
  
|<span data-ttu-id="dd41e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="dd41e-106">Member</span></span>|<span data-ttu-id="dd41e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd41e-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="dd41e-108">İçin benzersiz bir tanımlayıcı `IStream` bir çağrı tarafından döndürülen [Ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), başvurulan derleme yüklenecek olan öğesinden.</span><span class="sxs-lookup"><span data-stu-id="dd41e-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="dd41e-109">Başvurulan derleme için benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="dd41e-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="dd41e-110">Başvurulan derleme bağlama ilkesi değerleri uygulandıktan sonra tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="dd41e-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="dd41e-111">Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hangi sürüm ilkeleri varsa, başvurulan derlemeye uygulanması gerektiğini gösteren değerleri.</span><span class="sxs-lookup"><span data-stu-id="dd41e-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd41e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd41e-112">Remarks</span></span>  
 <span data-ttu-id="dd41e-113">Benzersiz tanımlayıcı ana bilgisayar kaynakları `dwAppDomainId` ortak dil çalışma zamanı (CLR).</span><span class="sxs-lookup"><span data-stu-id="dd41e-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="dd41e-114">Çağrısı yapıldıktan sonra `IHostAssemblyStore::ProvideAssembly` döndürür, çalışma belirlemek için tanımlayıcı kullandığı olmadığını içeriğini `IStream` eşlendi.</span><span class="sxs-lookup"><span data-stu-id="dd41e-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="dd41e-115">Bu durumda, çalışma zamanı akış yeniden eşleme yerine var olan kopyasını yükler.</span><span class="sxs-lookup"><span data-stu-id="dd41e-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="dd41e-116">Döndürülen akışlar için çalışma zamanı bu tanımlayıcıyı ayrıca arama anahtar olarak kullanır. çağrılar [Ihostassemblystore::providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="dd41e-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="dd41e-117">Bu nedenle, tanımlayıcı derleme isteklerini ve modülün istekleri için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dd41e-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd41e-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd41e-118">Requirements</span></span>  
 <span data-ttu-id="dd41e-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd41e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd41e-120">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="dd41e-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="dd41e-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dd41e-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="dd41e-122">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="dd41e-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dd41e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd41e-123">See also</span></span>

- [<span data-ttu-id="dd41e-124">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="dd41e-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="dd41e-125">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd41e-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="dd41e-126">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd41e-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="dd41e-127">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd41e-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="dd41e-128">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd41e-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="dd41e-129">ModuleBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="dd41e-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
