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
ms.openlocfilehash: 615637813b08629aaea74b23fa2737f52d61bafb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616935"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="6cb42-102">AssemblyBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="6cb42-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="6cb42-103">Başvurulan derleme hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6cb42-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cb42-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6cb42-104">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="6cb42-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6cb42-105">Members</span></span>  
  
|<span data-ttu-id="6cb42-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6cb42-106">Member</span></span>|<span data-ttu-id="6cb42-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cb42-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="6cb42-108">`IStream` [IHostAssemblyStore](ihostassemblystore-provideassembly-method.md)çağrısı tarafından döndürülen benzersiz bir tanımlayıcı::P rovideassembly, başvurulan derlemenin yükleneceği.</span><span class="sxs-lookup"><span data-stu-id="6cb42-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="6cb42-109">Başvurulan derleme için benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="6cb42-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="6cb42-110">Bağlama ilkesi değerlerinin uygulamadan sonra başvurulan derlemenin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6cb42-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="6cb42-111">Varsa, başvurulan derlemeye hangi sürüm oluşturma ilkelerinin uygulanacağını belirten [EPolicyAction](epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="6cb42-111">One of the [EPolicyAction](epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cb42-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6cb42-112">Remarks</span></span>  
 <span data-ttu-id="6cb42-113">Ana bilgisayar, `dwAppDomainId` ortak dil çalışma zamanına (CLR) benzersiz tanımlayıcıyı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6cb42-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="6cb42-114">Bir çağrıdan sonra `IHostAssemblyStore::ProvideAssembly` , çalışma zamanı, ' ın içeriklerinin eşlenip eşlenmediğini anlamak için tanımlayıcıyı kullanır `IStream` .</span><span class="sxs-lookup"><span data-stu-id="6cb42-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="6cb42-115">Öyleyse, çalışma zamanı akışı yeniden eşleme yerine mevcut kopyayı yükler.</span><span class="sxs-lookup"><span data-stu-id="6cb42-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="6cb42-116">Çalışma zamanı Ayrıca bu tanımlayıcıyı [IHostAssemblyStore](ihostassemblystore-providemodule-method.md)çağrılarından döndürülen akışlar için bir arama anahtarı olarak kullanır::P rovideModule.</span><span class="sxs-lookup"><span data-stu-id="6cb42-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="6cb42-117">Bu nedenle, tanımlayıcı modül istekleri ve derleme istekleri için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6cb42-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cb42-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6cb42-118">Requirements</span></span>  
 <span data-ttu-id="6cb42-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cb42-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cb42-120">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="6cb42-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="6cb42-121">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6cb42-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cb42-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cb42-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb42-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cb42-123">See also</span></span>

- [<span data-ttu-id="6cb42-124">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="6cb42-124">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="6cb42-125">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6cb42-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="6cb42-126">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6cb42-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="6cb42-127">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6cb42-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="6cb42-128">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6cb42-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="6cb42-129">ModuleBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="6cb42-129">ModuleBindInfo Structure</span></span>](modulebindinfo-structure.md)
