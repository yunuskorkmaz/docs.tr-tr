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
ms.openlocfilehash: a75235cd0ac0e55412f0ba58881796e3ebc801f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679247"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="e0c6d-102">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0c6d-102">ICLRAssemblyReferenceList Interface</span></span>

<span data-ttu-id="e0c6d-103">Ana bilgisayar tarafından değil, ortak dil çalışma zamanı (CLR) tarafından yüklenen derlemelerin listesini yönetir.</span><span class="sxs-lookup"><span data-stu-id="e0c6d-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0c6d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e0c6d-104">Methods</span></span>  
  
|<span data-ttu-id="e0c6d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e0c6d-105">Method</span></span>|<span data-ttu-id="e0c6d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0c6d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0c6d-107">IsAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0c6d-107">IsAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="e0c6d-108">Sağlanan işaretçinin listedeki bir derlemeye başvuru yapıp olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e0c6d-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="e0c6d-109">IsStringAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0c6d-109">IsStringAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="e0c6d-110">Sağlanan adın listedeki bir derlemenin adıyla eşleşip eşleşmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e0c6d-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0c6d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0c6d-111">Remarks</span></span>  

 <span data-ttu-id="e0c6d-112">Bir örneğine bir işaretçi almak için [ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) metodunu çağırın `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="e0c6d-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0c6d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0c6d-113">Requirements</span></span>  

 <span data-ttu-id="e0c6d-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0c6d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0c6d-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e0c6d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0c6d-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e0c6d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0c6d-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0c6d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c6d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0c6d-118">See also</span></span>

- [<span data-ttu-id="e0c6d-119">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0c6d-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="e0c6d-120">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0c6d-120">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="e0c6d-121">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e0c6d-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
