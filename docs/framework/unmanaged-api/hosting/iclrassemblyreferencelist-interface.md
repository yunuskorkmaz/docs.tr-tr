---
title: ICLRAssemblyReferenceList Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c2b383abdc67546749867de154a00fda244b3ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660027"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="fe2f2-102">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe2f2-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="fe2f2-103">Ortak dil çalışma zamanı (CLR) ve ana bilgisayar tarafından yüklenen derlemelerin bir listesini yönetir.</span><span class="sxs-lookup"><span data-stu-id="fe2f2-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe2f2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fe2f2-104">Methods</span></span>  
  
|<span data-ttu-id="fe2f2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fe2f2-105">Method</span></span>|<span data-ttu-id="fe2f2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe2f2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe2f2-107">IsAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe2f2-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="fe2f2-108">Sağlanan işaretçi listedeki bir derleme başvuruda bulunup bulunmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="fe2f2-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="fe2f2-109">IsStringAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe2f2-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="fe2f2-110">Sağlanan ad listesinde bir derlemenin adı ile eşleşip eşleşmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="fe2f2-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe2f2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe2f2-111">Remarks</span></span>  
 <span data-ttu-id="fe2f2-112">Çağrı [Iclrassemblyıdentitymanager::getclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) örneğine bir işaretçi almak için yöntemi `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="fe2f2-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe2f2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe2f2-113">Requirements</span></span>  
 <span data-ttu-id="fe2f2-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe2f2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe2f2-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fe2f2-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe2f2-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fe2f2-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe2f2-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe2f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe2f2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe2f2-118">See also</span></span>
- [<span data-ttu-id="fe2f2-119">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe2f2-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="fe2f2-120">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe2f2-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="fe2f2-121">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fe2f2-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
