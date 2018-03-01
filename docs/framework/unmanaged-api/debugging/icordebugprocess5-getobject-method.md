---
title: ICorDebugProcess5::GetObject Metodu
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
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 285554502271f0e93ff5de08ba593a08ab95eb6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="d1eca-102">ICorDebugProcess5::GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="d1eca-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="d1eca-103">Bir nesne adresi "ICorDebugObjectValue" nesneye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d1eca-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1eca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1eca-104">Syntax</span></span>  
  
```  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1eca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1eca-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="d1eca-106">[in] Nesne adresi.</span><span class="sxs-lookup"><span data-stu-id="d1eca-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="d1eca-107">[out] "ICorDebugObjectValue" nesnenin adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d1eca-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1eca-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1eca-108">Remarks</span></span>  
 <span data-ttu-id="d1eca-109">Varsa `addr` geçerli yönetilen nesneye işaret etmiyor `GetObject` yöntemi döndürür `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="d1eca-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1eca-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1eca-110">Requirements</span></span>  
 <span data-ttu-id="d1eca-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1eca-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1eca-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1eca-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1eca-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1eca-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1eca-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1eca-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1eca-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1eca-115">See Also</span></span>  
 [<span data-ttu-id="d1eca-116">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1eca-116">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="d1eca-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d1eca-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
