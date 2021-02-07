---
description: ': ICLRAssemblyReferenceList arabirimi hakkında daha fazla bilgi'
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
ms.openlocfilehash: f5ef4efd343ebc18c443482f4697a3d299c5aac1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716830"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="d6288-103">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6288-103">ICLRAssemblyReferenceList Interface</span></span>

<span data-ttu-id="d6288-104">Ana bilgisayar tarafından değil, ortak dil çalışma zamanı (CLR) tarafından yüklenen derlemelerin listesini yönetir.</span><span class="sxs-lookup"><span data-stu-id="d6288-104">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d6288-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d6288-105">Methods</span></span>  
  
|<span data-ttu-id="d6288-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d6288-106">Method</span></span>|<span data-ttu-id="d6288-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6288-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d6288-108">IsAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6288-108">IsAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="d6288-109">Sağlanan işaretçinin listedeki bir derlemeye başvuru yapıp olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d6288-109">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="d6288-110">IsStringAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6288-110">IsStringAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="d6288-111">Sağlanan adın listedeki bir derlemenin adıyla eşleşip eşleşmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d6288-111">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6288-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6288-112">Remarks</span></span>  

 <span data-ttu-id="d6288-113">Bir örneğine bir işaretçi almak için [ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) metodunu çağırın `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="d6288-113">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6288-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6288-114">Requirements</span></span>  

 <span data-ttu-id="d6288-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6288-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6288-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d6288-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6288-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d6288-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6288-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6288-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6288-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6288-119">See also</span></span>

- [<span data-ttu-id="d6288-120">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6288-120">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="d6288-121">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6288-121">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="d6288-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d6288-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
