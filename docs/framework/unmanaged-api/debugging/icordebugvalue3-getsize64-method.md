---
title: ICorDebugValue3::GetSize64 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c0b45e08f7b88d9374023f95c6e3e22139c8949
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768933"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="e13a2-102">ICorDebugValue3::GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e13a2-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="e13a2-103">Bu bayt cinsinden boyutunu alır [Icordebugvalue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="e13a2-103">Gets the size, in bytes, of this [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e13a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e13a2-104">Syntax</span></span>  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e13a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e13a2-105">Parameters</span></span>  
 <span data-ttu-id="e13a2-106">pSize</span><span class="sxs-lookup"><span data-stu-id="e13a2-106">pSize</span></span>  
 <span data-ttu-id="e13a2-107">[out] Bu nesnenin bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e13a2-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e13a2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e13a2-108">Remarks</span></span>  
 <span data-ttu-id="e13a2-109">Bu değer türü bir başvuru türü ise, bu yöntem, nesnenin boyutu yerine işaretçinin boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e13a2-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="e13a2-110">`ICorDebugValue3::GetSize` Yönteminden farklıdır [Icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) yöntemi, çıkış parametresinin türü.</span><span class="sxs-lookup"><span data-stu-id="e13a2-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="e13a2-111">İçinde [Icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), çıkış parametresi olan bir `ULONG32`; `ICorDebugValue3::GetSize`, bunun bir `ULONG64`.</span><span class="sxs-lookup"><span data-stu-id="e13a2-111">In [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="e13a2-112">Böylece [Icordebugvalue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) boyutu 2 GB'ı aşan diziler bildirmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="e13a2-112">This enables the [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e13a2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e13a2-113">Requirements</span></span>  
 <span data-ttu-id="e13a2-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e13a2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e13a2-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e13a2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e13a2-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e13a2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e13a2-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e13a2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e13a2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e13a2-118">See also</span></span>

- [<span data-ttu-id="e13a2-119">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e13a2-119">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="e13a2-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e13a2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
