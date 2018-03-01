---
title: "ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Yöntemi"
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
- ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 27d81e8b5171ded3301eaafea19d4a09b461078e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="38711-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38711-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="38711-103">Sağlanan ad listesinde bir derlemenin adını eşleşip eşleşmediğini belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="38711-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38711-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38711-104">Syntax</span></span>  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38711-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38711-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="38711-106">[in] Aranacak derleme adı.</span><span class="sxs-lookup"><span data-stu-id="38711-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38711-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="38711-107">Return Value</span></span>  
  
|<span data-ttu-id="38711-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38711-108">HRESULT</span></span>|<span data-ttu-id="38711-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38711-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38711-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="38711-110">S_OK</span></span>|<span data-ttu-id="38711-111">Dize listede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="38711-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="38711-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="38711-112">S_FALSE</span></span>|<span data-ttu-id="38711-113">Dize, listede görünmez.</span><span class="sxs-lookup"><span data-stu-id="38711-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="38711-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38711-114">E_FAIL</span></span>|<span data-ttu-id="38711-115">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="38711-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38711-116">Ortak dil çalışma zamanı, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="38711-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="38711-117">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="38711-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38711-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38711-118">Requirements</span></span>  
 <span data-ttu-id="38711-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38711-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38711-120">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="38711-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38711-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="38711-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38711-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38711-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38711-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38711-123">See Also</span></span>  
 [<span data-ttu-id="38711-124">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38711-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="38711-125">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38711-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="38711-126">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38711-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="38711-127">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38711-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
