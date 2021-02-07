---
description: 'Şu konuda daha fazla bilgi edinin: IManagedObject:: GetObjectIdentity yöntemi'
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
ms.openlocfilehash: 8929819bbf490680b5f3f1f47b9f3b8e830d57ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671171"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="f7697-103">IManagedObject::GetObjectIdentity Metodu</span><span class="sxs-lookup"><span data-stu-id="f7697-103">IManagedObject::GetObjectIdentity Method</span></span>

<span data-ttu-id="f7697-104">Bu yönetilen nesnenin kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="f7697-104">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7697-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7697-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7697-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7697-106">Parameters</span></span>  

 `pBSTRGUID`  
 <span data-ttu-id="f7697-107">dışı Nesnenin bulunduğu işlemin GUID 'sine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f7697-107">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="f7697-108">dışı Nesnenin uygulama etki alanının KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f7697-108">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="f7697-109">dışı COM klasik v tablosundaki nesnenin dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f7697-109">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7697-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7697-110">Remarks</span></span>  

 <span data-ttu-id="f7697-111">Yönetilen bir nesnenin kimliği işlem GUID 'SI, uygulama etki alanı KIMLIĞI ve nesnenin dizinini, COM klasik v-tablosunda içerir.</span><span class="sxs-lookup"><span data-stu-id="f7697-111">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7697-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7697-112">Requirements</span></span>  

 <span data-ttu-id="f7697-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7697-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7697-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f7697-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7697-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f7697-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7697-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7697-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7697-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7697-117">See also</span></span>

- [<span data-ttu-id="f7697-118">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7697-118">IManagedObject Interface</span></span>](imanagedobject-interface.md)
