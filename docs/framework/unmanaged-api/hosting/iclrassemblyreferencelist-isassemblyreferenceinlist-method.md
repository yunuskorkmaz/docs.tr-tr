---
title: ICLRAssemblyReferenceList::IsAssemblyReferenceInList Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 557b15fe2bd04a3362532f190a88ee2ad52ed366
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499842"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="20704-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20704-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="20704-103">Sağlanan işaretçi listesinde bir derlemeye başvuran olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="20704-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20704-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20704-104">Syntax</span></span>  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20704-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20704-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="20704-106">[in] Derleme Aranmak üzere bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="20704-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="20704-107">Geçerli değerler türünü `IAssemblyName` veya `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="20704-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20704-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="20704-108">Return Value</span></span>  
  
|<span data-ttu-id="20704-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20704-109">HRESULT</span></span>|<span data-ttu-id="20704-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20704-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20704-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="20704-111">S_OK</span></span>|<span data-ttu-id="20704-112">Dize listesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="20704-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="20704-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="20704-113">S_FALSE</span></span>|<span data-ttu-id="20704-114">Dize, listede görünmez.</span><span class="sxs-lookup"><span data-stu-id="20704-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="20704-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20704-115">E_FAIL</span></span>|<span data-ttu-id="20704-116">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="20704-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="20704-117">Ortak dil çalışma zamanı, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="20704-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="20704-118">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="20704-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="20704-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20704-119">Requirements</span></span>  
 <span data-ttu-id="20704-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20704-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20704-121">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20704-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20704-122">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="20704-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20704-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20704-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20704-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20704-124">See also</span></span>
- [<span data-ttu-id="20704-125">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20704-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="20704-126">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20704-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="20704-127">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20704-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="20704-128">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20704-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
