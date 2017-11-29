---
title: "ICLRAssemblyReferenceList::IsAssemblyReferenceInList Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 923f7f4178d3c310b51ebb7e7df06040ba69f9c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="2fc2c-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2fc2c-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="2fc2c-103">Sağlanan işaretçi bütünleştirilmiş listesinde başvurduğu olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="2fc2c-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fc2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2fc2c-104">Syntax</span></span>  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2fc2c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2fc2c-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="2fc2c-106">[in] Arabirim işaretçisi aranacak derleme.</span><span class="sxs-lookup"><span data-stu-id="2fc2c-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="2fc2c-107">Geçerli değerler türünü `IAssemblyName` veya `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="2fc2c-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2fc2c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2fc2c-108">Return Value</span></span>  
  
|<span data-ttu-id="2fc2c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2fc2c-109">HRESULT</span></span>|<span data-ttu-id="2fc2c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fc2c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2fc2c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2fc2c-111">S_OK</span></span>|<span data-ttu-id="2fc2c-112">Dize listede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2fc2c-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="2fc2c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2fc2c-113">S_FALSE</span></span>|<span data-ttu-id="2fc2c-114">Dize, listede görünmez.</span><span class="sxs-lookup"><span data-stu-id="2fc2c-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="2fc2c-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2fc2c-115">E_FAIL</span></span>|<span data-ttu-id="2fc2c-116">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2fc2c-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2fc2c-117">Ortak dil çalışma zamanı, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2fc2c-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="2fc2c-118">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2fc2c-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2fc2c-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2fc2c-119">Requirements</span></span>  
 <span data-ttu-id="2fc2c-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fc2c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fc2c-121">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2fc2c-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2fc2c-122">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2fc2c-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2fc2c-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fc2c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fc2c-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2fc2c-124">See Also</span></span>  
 [<span data-ttu-id="2fc2c-125">Iclrassemblyıdentitymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="2fc2c-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="2fc2c-126">Iclrassemblyreferencelist arabirimi</span><span class="sxs-lookup"><span data-stu-id="2fc2c-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="2fc2c-127">Ihostassemblymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="2fc2c-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="2fc2c-128">Ihostassemblystore arabirimi</span><span class="sxs-lookup"><span data-stu-id="2fc2c-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
