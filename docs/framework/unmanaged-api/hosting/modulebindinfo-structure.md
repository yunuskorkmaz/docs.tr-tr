---
title: ModuleBindInfo Yapısı
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
ms.openlocfilehash: 505015877985492edab4b761b379f33f1e5c6660
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729986"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="4c3d6-102">ModuleBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="4c3d6-102">ModuleBindInfo Structure</span></span>

<span data-ttu-id="4c3d6-103">Başvurulan modül ve onu içeren derleme hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c3d6-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c3d6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4c3d6-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="4c3d6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4c3d6-105">Members</span></span>  
  
|<span data-ttu-id="4c3d6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4c3d6-106">Member</span></span>|<span data-ttu-id="4c3d6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c3d6-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="4c3d6-108">`IStream`Başvurulan modülün yükleneceği [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md) yöntemine yapılan bir çağrı tarafından döndürülen benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="4c3d6-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="4c3d6-109">Başvurulan modülü içeren derleme için benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="4c3d6-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="4c3d6-110">Başvurulan modülün adı.</span><span class="sxs-lookup"><span data-stu-id="4c3d6-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c3d6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c3d6-111">Remarks</span></span>  

 <span data-ttu-id="4c3d6-112">`ModuleBindInfo` parametresi olarak geçirilir `IHostAssemblyStore::ProvideModule` .</span><span class="sxs-lookup"><span data-stu-id="4c3d6-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="4c3d6-113">Ana bilgisayar, `dwAppDomainId` ortak dil çalışma zamanına (CLR) benzersiz tanımlayıcıyı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c3d6-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="4c3d6-114">[IHostAssemblyStore ' a bir çağrıdan sonra::P rovideAssembly](ihostassemblystore-provideassembly-method.md) yöntemi döndürülürse, çalışma zamanı, ' ın içeriklerinin `IStream` eşlenip eşlenmediğini anlamak için tanımlayıcıyı kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c3d6-114">After a call to the [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="4c3d6-115">Öyleyse, çalışma zamanı akışı yeniden eşleme yerine mevcut kopyayı yükler.</span><span class="sxs-lookup"><span data-stu-id="4c3d6-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="4c3d6-116">Çalışma zamanı Ayrıca bu tanımlayıcıyı, metoduna yapılan çağrılardan döndürülen akışlar için bir arama anahtarı olarak kullanır `IHostAssemblyStore::ProvideAssembly` .</span><span class="sxs-lookup"><span data-stu-id="4c3d6-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="4c3d6-117">Bu nedenle, tanımlayıcı modül istekleri ve derleme istekleri için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c3d6-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c3d6-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c3d6-118">Requirements</span></span>  

 <span data-ttu-id="4c3d6-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c3d6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c3d6-120">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="4c3d6-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="4c3d6-121">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4c3d6-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c3d6-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c3d6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c3d6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c3d6-123">See also</span></span>

- [<span data-ttu-id="4c3d6-124">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="4c3d6-124">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="4c3d6-125">AssemblyBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="4c3d6-125">AssemblyBindInfo Structure</span></span>](assemblybindinfo-structure.md)
- [<span data-ttu-id="4c3d6-126">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c3d6-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="4c3d6-127">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c3d6-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="4c3d6-128">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c3d6-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
