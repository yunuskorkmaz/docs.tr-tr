---
title: ICLRAssemblyIdentityManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager
helpviewer_keywords: ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d7fe632941c4cf0c20841ece390d2f41f28337d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="18820-102">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18820-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="18820-103">Derlemeler hakkında ortak dil çalışma zamanı (CLR) ile konak arasındaki iletişimi destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="18820-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18820-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="18820-104">Methods</span></span>  
  
|<span data-ttu-id="18820-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="18820-105">Method</span></span>|<span data-ttu-id="18820-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18820-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18820-107">Getbindingıdentityfromfile yöntemi</span><span class="sxs-lookup"><span data-stu-id="18820-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="18820-108">Belirtilen dosya yolu konumunda derlemesi için veri bağlama derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="18820-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="18820-109">Getbindingıdentityfromstream yöntemi</span><span class="sxs-lookup"><span data-stu-id="18820-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="18820-110">Belirtilen akış derlemede kurallı derleme kimlik verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="18820-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="18820-111">GetCLRAssemblyReferenceList yöntemi</span><span class="sxs-lookup"><span data-stu-id="18820-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="18820-112">Alır bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) kısmi derleme kimlikleri sağlanan listeden örneği.</span><span class="sxs-lookup"><span data-stu-id="18820-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="18820-113">GetProbingAssembliesFromReference yöntemi</span><span class="sxs-lookup"><span data-stu-id="18820-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="18820-114">Alır bir [Iclrprobingassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) belirtilen kimliğe sahip derlemesi tarafından başvurulan derleme kimlikleri için Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="18820-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="18820-115">GetReferencedAssembliesFromFile yöntemi</span><span class="sxs-lookup"><span data-stu-id="18820-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="18820-116">Alır bir [Iclrreferenceassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) belirtilen dosya yolu konumunda derlemesi tarafından başvurulan bir derleme listesi içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="18820-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="18820-117">GetReferencedAssembliesFromStream yöntemi</span><span class="sxs-lookup"><span data-stu-id="18820-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="18820-118">Bir işaretçi alır bir `ICLRReferenceAssemblyEnum` belirtilen stream derlemede tarafından başvurulan derlemeler için derleme kimlik verilerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="18820-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="18820-119">Isstronglynamed yöntemi</span><span class="sxs-lookup"><span data-stu-id="18820-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="18820-120">Belirtilen derleme güçlü olarak adlandırılmamış olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="18820-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18820-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18820-121">Remarks</span></span>  
 <span data-ttu-id="18820-122">Kullanım `ICLRAssemblyIdentityManager` örneklerini almak için `ICLRAssemblyReferenceList` ve derleme kimlikleri numaralandırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="18820-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18820-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18820-123">Requirements</span></span>  
 <span data-ttu-id="18820-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18820-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18820-125">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="18820-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18820-126">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="18820-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18820-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18820-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18820-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="18820-128">See Also</span></span>  
 [<span data-ttu-id="18820-129">Iclrassemblyreferencelist arabirimi</span><span class="sxs-lookup"><span data-stu-id="18820-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="18820-130">Iclrprobingassemblyenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="18820-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [<span data-ttu-id="18820-131">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="18820-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
