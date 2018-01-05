---
title: ICorDebugValue3::GetSize64 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue3::GetSize64
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4eb0c4691b82bdfaecb97c5969a942c113987c04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="04d3b-102">ICorDebugValue3::GetSize64 Metodu</span><span class="sxs-lookup"><span data-stu-id="04d3b-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="04d3b-103">Bu bayt cinsinden boyutu alır [Icordebugvalue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="04d3b-103">Gets the size, in bytes, of this [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04d3b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04d3b-104">Syntax</span></span>  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04d3b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04d3b-105">Parameters</span></span>  
 <span data-ttu-id="04d3b-106">pSize</span><span class="sxs-lookup"><span data-stu-id="04d3b-106">pSize</span></span>  
 <span data-ttu-id="04d3b-107">[out] Bu nesnenin bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="04d3b-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04d3b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04d3b-108">Remarks</span></span>  
 <span data-ttu-id="04d3b-109">Bu değerinin türü bir başvuru türü ise, bu yöntem nesnenin boyutu yerine işaretçi boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="04d3b-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="04d3b-110">`ICorDebugValue3::GetSize` Yönteminden farklıdır [Icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) türü, çıktı parametresi olarak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04d3b-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="04d3b-111">İçinde [Icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), çıktı parametresi bir `ULONG32`; `ICorDebugValue3::GetSize`, bu bir `ULONG64`.</span><span class="sxs-lookup"><span data-stu-id="04d3b-111">In [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="04d3b-112">Böylece [Icordebugvalue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) boyutu 2 GB aşan dizi bildirmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="04d3b-112">This enables the [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04d3b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04d3b-113">Requirements</span></span>  
 <span data-ttu-id="04d3b-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04d3b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04d3b-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04d3b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04d3b-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04d3b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04d3b-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04d3b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d3b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04d3b-118">See Also</span></span>  
 [<span data-ttu-id="04d3b-119">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04d3b-119">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [<span data-ttu-id="04d3b-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="04d3b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
