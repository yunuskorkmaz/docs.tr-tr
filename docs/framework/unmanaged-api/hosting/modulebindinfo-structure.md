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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f14d3dcaad1cc8cac11599b1647d61df3a793301
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765186"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="46ae6-102">ModuleBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="46ae6-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="46ae6-103">Başvurulan modül ve onu içeren derleme hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="46ae6-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46ae6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46ae6-104">Syntax</span></span>  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="46ae6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="46ae6-105">Members</span></span>  
  
|<span data-ttu-id="46ae6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="46ae6-106">Member</span></span>|<span data-ttu-id="46ae6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46ae6-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="46ae6-108">İçin benzersiz bir tanımlayıcı `IStream` bir çağrı tarafından döndürülen [Ihostassemblystore::providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) içinden başvurulan modül yüklenecek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="46ae6-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="46ae6-109">Başvurulan modül içeren derleme için benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="46ae6-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="46ae6-110">Başvurulan modül adı.</span><span class="sxs-lookup"><span data-stu-id="46ae6-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46ae6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46ae6-111">Remarks</span></span>  
 <span data-ttu-id="46ae6-112">`ModuleBindInfo` bir parametre olarak geçirilen `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="46ae6-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="46ae6-113">Benzersiz tanımlayıcı ana bilgisayar kaynakları `dwAppDomainId` ortak dil çalışma zamanı (CLR).</span><span class="sxs-lookup"><span data-stu-id="46ae6-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="46ae6-114">Çağrısı yapıldıktan sonra [Ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) yöntemi döndürür, çalışma belirlemek için tanımlayıcı kullandığı olmadığını içeriğini `IStream` eşlendi.</span><span class="sxs-lookup"><span data-stu-id="46ae6-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="46ae6-115">Bu durumda, çalışma zamanı akış yeniden eşleme yerine var olan kopyasını yükler.</span><span class="sxs-lookup"><span data-stu-id="46ae6-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="46ae6-116">Çalışma zamanı bu tanımlayıcıyı ayrıca çağrılardan döndürülen akışlar için arama anahtar olarak kullanır `IHostAssemblyStore::ProvideAssembly` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="46ae6-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="46ae6-117">Bu nedenle, tanımlayıcı için derleme isteklerini de modülü istekleri için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46ae6-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46ae6-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46ae6-118">Requirements</span></span>  
 <span data-ttu-id="46ae6-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46ae6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46ae6-120">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="46ae6-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="46ae6-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="46ae6-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46ae6-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46ae6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46ae6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46ae6-123">See also</span></span>

- [<span data-ttu-id="46ae6-124">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="46ae6-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="46ae6-125">AssemblyBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="46ae6-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [<span data-ttu-id="46ae6-126">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46ae6-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="46ae6-127">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46ae6-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="46ae6-128">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46ae6-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
