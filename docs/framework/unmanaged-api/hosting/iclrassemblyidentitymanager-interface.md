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
ms.workload: dotnet
ms.openlocfilehash: 168c67eb701d7dfc461553cfe32ed43dcea5e844
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="ab1d8-102">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab1d8-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="ab1d8-103">Derlemeler hakkında ortak dil çalışma zamanı (CLR) ile konak arasındaki iletişimi destekleyen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab1d8-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab1d8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ab1d8-104">Methods</span></span>  
  
|<span data-ttu-id="ab1d8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ab1d8-105">Method</span></span>|<span data-ttu-id="ab1d8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab1d8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab1d8-107">GetBindingIdentityFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab1d8-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="ab1d8-108">Belirtilen dosya yolu konumunda derlemesi için veri bağlama derleme kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="ab1d8-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="ab1d8-109">GetBindingIdentityFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab1d8-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="ab1d8-110">Belirtilen akış derlemede kurallı derleme kimlik verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="ab1d8-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="ab1d8-111">GetCLRAssemblyReferenceList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab1d8-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="ab1d8-112">Alır bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) kısmi derleme kimlikleri sağlanan listeden örneği.</span><span class="sxs-lookup"><span data-stu-id="ab1d8-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="ab1d8-113">GetProbingAssembliesFromReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab1d8-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="ab1d8-114">Alır bir [Iclrprobingassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) belirtilen kimliğe sahip derlemesi tarafından başvurulan derleme kimlikleri için Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="ab1d8-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="ab1d8-115">GetReferencedAssembliesFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab1d8-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="ab1d8-116">Alır bir [Iclrreferenceassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) belirtilen dosya yolu konumunda derlemesi tarafından başvurulan bir derleme listesi içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="ab1d8-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="ab1d8-117">GetReferencedAssembliesFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab1d8-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="ab1d8-118">Bir işaretçi alır bir `ICLRReferenceAssemblyEnum` belirtilen stream derlemede tarafından başvurulan derlemeler için derleme kimlik verilerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="ab1d8-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="ab1d8-119">IsStronglyNamed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab1d8-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="ab1d8-120">Belirtilen derleme güçlü olarak adlandırılmamış olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ab1d8-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab1d8-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab1d8-121">Remarks</span></span>  
 <span data-ttu-id="ab1d8-122">Kullanım `ICLRAssemblyIdentityManager` örneklerini almak için `ICLRAssemblyReferenceList` ve derleme kimlikleri numaralandırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="ab1d8-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab1d8-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab1d8-123">Requirements</span></span>  
 <span data-ttu-id="ab1d8-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab1d8-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab1d8-125">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ab1d8-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab1d8-126">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ab1d8-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab1d8-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab1d8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab1d8-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab1d8-128">See Also</span></span>  
 [<span data-ttu-id="ab1d8-129">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab1d8-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="ab1d8-130">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab1d8-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [<span data-ttu-id="ab1d8-131">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ab1d8-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
