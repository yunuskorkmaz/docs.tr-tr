---
title: ICorDebugProcess5::GetTypeID Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess5.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeID
helpviewer_keywords:
- ICorDebugProcess5::GetTypeID method [.NET Framework debugging]
- GetTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 47dbaea4-8857-462e-93ba-fff880fc9e50
topic_type:
- apiref
ms.openlocfilehash: 6c159780b9019127d166e8437ea4ed214284011f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121257"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="9b7f6-102">ICorDebugProcess5::GetTypeID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b7f6-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="9b7f6-103">Bir nesne adresini bir [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) tanımlayıcısına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="9b7f6-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b7f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b7f6-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b7f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b7f6-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="9b7f6-106">'ndaki Nesne adresi.</span><span class="sxs-lookup"><span data-stu-id="9b7f6-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="9b7f6-107">Nesneyi tanımlayan [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9b7f6-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b7f6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b7f6-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b7f6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b7f6-109">Requirements</span></span>  
 <span data-ttu-id="9b7f6-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b7f6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b7f6-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9b7f6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b7f6-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9b7f6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b7f6-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b7f6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7f6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b7f6-114">See also</span></span>

- [<span data-ttu-id="9b7f6-115">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b7f6-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="9b7f6-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9b7f6-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
