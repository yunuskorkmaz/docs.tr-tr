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
ms.openlocfilehash: fc74b84bccceb1772bf3642e51ec88c562ce5dce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730725"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="dca1d-102">IManagedObject::GetObjectIdentity Metodu</span><span class="sxs-lookup"><span data-stu-id="dca1d-102">IManagedObject::GetObjectIdentity Method</span></span>

<span data-ttu-id="dca1d-103">Bu yönetilen nesnenin kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="dca1d-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dca1d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="dca1d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dca1d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dca1d-105">Parameters</span></span>  

 `pBSTRGUID`  
 <span data-ttu-id="dca1d-106">dışı Nesnenin bulunduğu işlemin GUID 'sine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dca1d-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="dca1d-107">dışı Nesnenin uygulama etki alanının KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dca1d-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="dca1d-108">dışı COM klasik v tablosundaki nesnenin dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dca1d-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dca1d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dca1d-109">Remarks</span></span>  

 <span data-ttu-id="dca1d-110">Yönetilen bir nesnenin kimliği işlem GUID 'SI, uygulama etki alanı KIMLIĞI ve nesnenin dizinini, COM klasik v-tablosunda içerir.</span><span class="sxs-lookup"><span data-stu-id="dca1d-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dca1d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dca1d-111">Requirements</span></span>  

 <span data-ttu-id="dca1d-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dca1d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dca1d-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dca1d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dca1d-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="dca1d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dca1d-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dca1d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca1d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dca1d-116">See also</span></span>

- [<span data-ttu-id="dca1d-117">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dca1d-117">IManagedObject Interface</span></span>](imanagedobject-interface.md)
