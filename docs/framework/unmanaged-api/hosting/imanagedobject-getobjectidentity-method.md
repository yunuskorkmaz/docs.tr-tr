---
title: IManagedObject::GetObjectIdentity Metodu
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
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c5654865c557e6e004685f66753366d7cb575919
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="ff4f0-102">IManagedObject::GetObjectIdentity Metodu</span><span class="sxs-lookup"><span data-stu-id="ff4f0-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="ff4f0-103">Bu yönetilen nesne kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="ff4f0-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff4f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff4f0-104">Syntax</span></span>  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff4f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff4f0-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="ff4f0-106">[out] Bir işaretçi nesne bulunduğu işlem GUID.</span><span class="sxs-lookup"><span data-stu-id="ff4f0-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="ff4f0-107">[out] Nesnenin uygulama etki alanı kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff4f0-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="ff4f0-108">[out] COM Klasik v tablosunda nesnenin dizin için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff4f0-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff4f0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff4f0-109">Remarks</span></span>  
 <span data-ttu-id="ff4f0-110">Yönetilen bir nesnenin kimliğini işlemi GUID, uygulama etki alanı kimliği ve nesnenin dizin COM Klasik v tabloda içerir.</span><span class="sxs-lookup"><span data-stu-id="ff4f0-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff4f0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff4f0-111">Requirements</span></span>  
 <span data-ttu-id="ff4f0-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff4f0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff4f0-113">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ff4f0-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff4f0-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ff4f0-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff4f0-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff4f0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff4f0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff4f0-116">See Also</span></span>  
 [<span data-ttu-id="ff4f0-117">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff4f0-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
