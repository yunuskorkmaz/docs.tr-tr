---
title: "ModuleBindInfo Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ModuleBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ModuleBindInfo
helpviewer_keywords: ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6488503e0300530b22c0c6f904e11db7f5d5b41c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="4495a-102">ModuleBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="4495a-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="4495a-103">Başvurulan modül ve içerdiği derleme hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4495a-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4495a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4495a-104">Syntax</span></span>  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="4495a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4495a-105">Members</span></span>  
  
|<span data-ttu-id="4495a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4495a-106">Member</span></span>|<span data-ttu-id="4495a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4495a-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="4495a-108">İçin benzersiz bir tanımlayıcı `IStream` için yapılan bir çağrı tarafından döndürülen [Ihostassemblystore::providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) başvurulan modül olduğu yüklenecek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4495a-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="4495a-109">Başvurulan modül içeren derlemenin için benzersiz bir tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="4495a-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="4495a-110">Başvurulan modül adı.</span><span class="sxs-lookup"><span data-stu-id="4495a-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4495a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4495a-111">Remarks</span></span>  
 <span data-ttu-id="4495a-112">`ModuleBindInfo`bir parametre olarak geçirilen `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="4495a-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="4495a-113">Benzersiz tanımlayıcı ana bilgisayar kaynakları `dwAppDomainId` ortak dil çalışma zamanı (CLR) için.</span><span class="sxs-lookup"><span data-stu-id="4495a-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="4495a-114">Çağrı sonra [Ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) yöntemi döndürür, çalışma zamanı belirlemek için tanımlayıcısını kullanır olup olmadığını içeriğini `IStream` eşlenmedi.</span><span class="sxs-lookup"><span data-stu-id="4495a-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="4495a-115">Bu durumda, çalışma zamanı akış yeniden eşleme yerine var olan kopyasını yükler.</span><span class="sxs-lookup"><span data-stu-id="4495a-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="4495a-116">Çalışma zamanı bu tanımlayıcı ayrıca çağrılardan döndürülen akışlar için arama anahtar olarak kullanır `IHostAssemblyStore::ProvideAssembly` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4495a-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="4495a-117">Bu nedenle, tanımlayıcı derleme istekleri için de modülü istekleri için benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4495a-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4495a-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4495a-118">Requirements</span></span>  
 <span data-ttu-id="4495a-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4495a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4495a-120">**Başlık:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="4495a-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="4495a-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4495a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4495a-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4495a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4495a-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4495a-123">See Also</span></span>  
 [<span data-ttu-id="4495a-124">Barındırma yapıları</span><span class="sxs-lookup"><span data-stu-id="4495a-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="4495a-125">Assemblybindınfo yapısı</span><span class="sxs-lookup"><span data-stu-id="4495a-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 [<span data-ttu-id="4495a-126">Iclrassemblyıdentitymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="4495a-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="4495a-127">Iclrassemblyreferencelist arabirimi</span><span class="sxs-lookup"><span data-stu-id="4495a-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="4495a-128">Ihostassemblymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="4495a-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
