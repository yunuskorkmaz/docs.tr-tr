---
title: ICorDebugProcess5::GetArrayLayout Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
ms.openlocfilehash: 5a415c8f3124c08984f8101e1f4dbcae6bf96fbf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129618"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="b2a19-102">ICorDebugProcess5::GetArrayLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2a19-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="b2a19-103">Dizi türlerinin yerleşimi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2a19-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2a19-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2a19-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2a19-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2a19-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="b2a19-106">'ndaki Düzeni istenen diziyi belirten bir [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) belirteci.</span><span class="sxs-lookup"><span data-stu-id="b2a19-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="b2a19-107">dışı [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) yapısına yönelik bir işaretçi, bellekteki dizinin düzeni hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="b2a19-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2a19-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2a19-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2a19-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2a19-109">Requirements</span></span>  
 <span data-ttu-id="b2a19-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2a19-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2a19-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2a19-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2a19-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b2a19-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2a19-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2a19-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a19-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2a19-114">See also</span></span>

- [<span data-ttu-id="b2a19-115">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2a19-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="b2a19-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b2a19-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
