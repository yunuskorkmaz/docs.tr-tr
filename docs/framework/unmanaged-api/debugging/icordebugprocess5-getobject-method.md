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
ms.openlocfilehash: 35fdcd4bc3c9dbf6408f501256ce0df0174f9374
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135661"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="26888-102">ICorDebugProcess5::GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="26888-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="26888-103">Bir nesne adresi "ICorDebugObjectValue" nesneye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="26888-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26888-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26888-104">Syntax</span></span>  
  
```  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26888-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26888-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="26888-106">[in] Nesnesi adresi.</span><span class="sxs-lookup"><span data-stu-id="26888-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="26888-107">[out] Bir "ICorDebugObjectValue" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="26888-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26888-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26888-108">Remarks</span></span>  
 <span data-ttu-id="26888-109">Varsa `addr` geçerli yönetilen nesneye işaret etmiyor `GetObject` yöntemi döndürür `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="26888-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26888-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26888-110">Requirements</span></span>  
 <span data-ttu-id="26888-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26888-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26888-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26888-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26888-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26888-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="26888-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="26888-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="26888-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26888-115">See also</span></span>

- [<span data-ttu-id="26888-116">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26888-116">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="26888-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="26888-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
