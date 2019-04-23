---
title: IManagedObject::GetObjectIdentity Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d014d2900ea790f84331ed933143513ae9e63f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213499"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="2d37c-102">IManagedObject::GetObjectIdentity Metodu</span><span class="sxs-lookup"><span data-stu-id="2d37c-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="2d37c-103">Bu yönetilen nesne kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="2d37c-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d37c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d37c-104">Syntax</span></span>  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d37c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d37c-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="2d37c-106">[out] Nesnenin bulunduğu işlem GUİD'si işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2d37c-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="2d37c-107">[out] Nesnenin uygulama etki alanı kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2d37c-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="2d37c-108">[out] Nesnenin dizinde COM Klasik v tablo için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2d37c-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d37c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d37c-109">Remarks</span></span>  
 <span data-ttu-id="2d37c-110">Yönetilen bir nesnenin kimliğini COM Klasik v tablosunda işlem GUID'si, uygulama etki alanı kimliği ve nesnenin dizin içerir.</span><span class="sxs-lookup"><span data-stu-id="2d37c-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d37c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d37c-111">Requirements</span></span>  
 <span data-ttu-id="2d37c-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d37c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d37c-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d37c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d37c-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2d37c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d37c-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d37c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d37c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d37c-116">See also</span></span>

- [<span data-ttu-id="2d37c-117">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d37c-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
