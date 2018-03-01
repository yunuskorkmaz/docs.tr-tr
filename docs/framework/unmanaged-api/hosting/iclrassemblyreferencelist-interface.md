---
title: ICLRAssemblyReferenceList Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eeef0e7f825f4a6ad907d6b17b92afe1807bad12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="4c547-102">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c547-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="4c547-103">Ortak dil çalışma zamanı (CLR) ve ana bilgisayar tarafından yüklenen bir derleme listesi yönetir.</span><span class="sxs-lookup"><span data-stu-id="4c547-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c547-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4c547-104">Methods</span></span>  
  
|<span data-ttu-id="4c547-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4c547-105">Method</span></span>|<span data-ttu-id="4c547-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c547-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c547-107">IsAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c547-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="4c547-108">Sağlanan işaretçi listesinde bir derlemeye başvurur olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="4c547-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="4c547-109">IsStringAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c547-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="4c547-110">Sağlanan ad listesinde bir derlemenin adını eşleşip eşleşmediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="4c547-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c547-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c547-111">Remarks</span></span>  
 <span data-ttu-id="4c547-112">Çağrı [Iclrassemblyıdentitymanager::getclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) örneği için bir işaretçi almak için yöntemi `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="4c547-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c547-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c547-113">Requirements</span></span>  
 <span data-ttu-id="4c547-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c547-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c547-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c547-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c547-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4c547-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c547-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c547-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c547-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c547-118">See Also</span></span>  
 [<span data-ttu-id="4c547-119">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c547-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="4c547-120">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c547-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="4c547-121">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4c547-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
