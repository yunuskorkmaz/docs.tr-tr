---
title: ICorDebugProcess5::GetObject Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56b5796a6edb3d9fb7e0dc1072951a93a6e508a3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502520"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="8c36d-102">ICorDebugProcess5::GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="8c36d-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="8c36d-103">Bir nesne adresi "ICorDebugObjectValue" nesneye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="8c36d-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c36d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c36d-104">Syntax</span></span>  
  
```  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c36d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c36d-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="8c36d-106">[in] Nesnesi adresi.</span><span class="sxs-lookup"><span data-stu-id="8c36d-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="8c36d-107">[out] Bir "ICorDebugObjectValue" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8c36d-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c36d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c36d-108">Remarks</span></span>  
 <span data-ttu-id="8c36d-109">Varsa `addr` geçerli yönetilen nesneye işaret etmiyor `GetObject` yöntemi döndürür `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="8c36d-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c36d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c36d-110">Requirements</span></span>  
 <span data-ttu-id="8c36d-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c36d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c36d-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c36d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c36d-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c36d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c36d-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c36d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c36d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c36d-115">See also</span></span>
- [<span data-ttu-id="8c36d-116">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c36d-116">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="8c36d-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8c36d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
