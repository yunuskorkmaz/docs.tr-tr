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
ms.openlocfilehash: 8c884569a452fb2985713956f942205cda6ea1ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141251"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="30712-102">IManagedObject::GetObjectIdentity Metodu</span><span class="sxs-lookup"><span data-stu-id="30712-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="30712-103">Bu yönetilen nesnenin kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="30712-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30712-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30712-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30712-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30712-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="30712-106">dışı Nesnenin bulunduğu işlemin GUID 'sine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="30712-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="30712-107">dışı Nesnenin uygulama etki alanının KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="30712-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="30712-108">dışı COM klasik v tablosundaki nesnenin dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="30712-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30712-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30712-109">Remarks</span></span>  
 <span data-ttu-id="30712-110">Yönetilen bir nesnenin kimliği işlem GUID 'SI, uygulama etki alanı KIMLIĞI ve nesnenin dizinini, COM klasik v-tablosunda içerir.</span><span class="sxs-lookup"><span data-stu-id="30712-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30712-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30712-111">Requirements</span></span>  
 <span data-ttu-id="30712-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30712-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30712-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="30712-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30712-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="30712-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30712-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30712-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30712-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30712-116">See also</span></span>

- [<span data-ttu-id="30712-117">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30712-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
