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
ms.openlocfilehash: 8764a3d665c997460419561eb168f92ca769c30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192108"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="02034-102">AssemblyBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="02034-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="02034-103">Başvurulan derleme hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="02034-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02034-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02034-104">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="02034-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="02034-105">Members</span></span>  
  
|<span data-ttu-id="02034-106">Üye</span><span class="sxs-lookup"><span data-stu-id="02034-106">Member</span></span>|<span data-ttu-id="02034-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="02034-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="02034-108">Başvurulan derlemenin yükleneceği [ıhostassembly:P Store](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)çağrısı tarafından döndürülen `IStream` için benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="02034-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="02034-109">Başvurulan derleme için benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="02034-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="02034-110">Bağlama ilkesi değerlerinin uygulamadan sonra başvurulan derlemenin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="02034-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="02034-111">Varsa, başvurulan derlemeye hangi sürüm oluşturma ilkelerinin uygulanacağını belirten [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="02034-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02034-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02034-112">Remarks</span></span>  
 <span data-ttu-id="02034-113">Ana bilgisayar, ortak dil çalışma zamanına (CLR) `dwAppDomainId` benzersiz tanımlayıcıyı sağlar.</span><span class="sxs-lookup"><span data-stu-id="02034-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="02034-114">`IHostAssemblyStore::ProvideAssembly` çağrısı yapıldıktan sonra, çalışma zamanı `IStream` içeriğinin eşlenip eşleştirilmediğini anlamak için tanımlayıcıyı kullanır.</span><span class="sxs-lookup"><span data-stu-id="02034-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="02034-115">Öyleyse, çalışma zamanı akışı yeniden eşleme yerine mevcut kopyayı yükler.</span><span class="sxs-lookup"><span data-stu-id="02034-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="02034-116">Çalışma zamanı Ayrıca bu tanımlayıcıyı [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)çağrılarından döndürülen akışlar için bir arama anahtarı olarak kullanır::P rovideModule.</span><span class="sxs-lookup"><span data-stu-id="02034-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="02034-117">Bu nedenle, tanımlayıcı modül istekleri ve derleme istekleri için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02034-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02034-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02034-118">Requirements</span></span>  
 <span data-ttu-id="02034-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02034-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02034-120">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="02034-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="02034-121">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="02034-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02034-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02034-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02034-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02034-123">See also</span></span>

- [<span data-ttu-id="02034-124">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="02034-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="02034-125">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02034-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="02034-126">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02034-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="02034-127">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02034-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="02034-128">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02034-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="02034-129">ModuleBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="02034-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
