---
title: ICorDebugType::GetClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: 3a895f432ed640cc35a492df0c91cece34893062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122360"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="16ceb-102">ICorDebugType::GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16ceb-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="16ceb-103">Örneklenmiş genel türü temsil eden bir ICorDebugClass için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="16ceb-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16ceb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16ceb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16ceb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16ceb-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="16ceb-106">dışı Örneklenmemiş genel türü temsil eden `ICorDebugClass` arabiriminin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="16ceb-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16ceb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16ceb-107">Remarks</span></span>  
 <span data-ttu-id="16ceb-108">`GetClass`, yalnızca belirli koşullar altında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="16ceb-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="16ceb-109">`GetClass`çağrılmadan önce [ICorDebugType:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) çağırın.</span><span class="sxs-lookup"><span data-stu-id="16ceb-109">Call [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="16ceb-110">`ICorDebugType::GetType` ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE olan bir CorElementType değeri döndürürse, genel bir türün örneklenmemiş türünü almak için `GetClass` çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="16ceb-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16ceb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16ceb-111">Requirements</span></span>  
 <span data-ttu-id="16ceb-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16ceb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16ceb-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16ceb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16ceb-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="16ceb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16ceb-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16ceb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
