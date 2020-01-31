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
ms.openlocfilehash: 7ae06d825565faff70b0c8be2ccbee5228737e41
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791096"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="5d4d3-102">ICorDebugValue3::GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d4d3-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="5d4d3-103">Bu [ICorDebugValue3](icordebugvalue3-interface.md) nesnesinin bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="5d4d3-103">Gets the size, in bytes, of this [ICorDebugValue3](icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d4d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d4d3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d4d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d4d3-105">Parameters</span></span>  
 <span data-ttu-id="5d4d3-106">Psıze</span><span class="sxs-lookup"><span data-stu-id="5d4d3-106">pSize</span></span>  
 <span data-ttu-id="5d4d3-107">dışı Bu nesnenin bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d4d3-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d4d3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d4d3-108">Remarks</span></span>  
 <span data-ttu-id="5d4d3-109">Bu değerin türü bir başvuru türü ise, bu yöntem nesnenin boyutu yerine işaretçinin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d4d3-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="5d4d3-110">`ICorDebugValue3::GetSize` yöntemi, çıkış parametresinin türü içindeki [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md) yönteminden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="5d4d3-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="5d4d3-111">[ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md)içinde, çıkış parametresi bir `ULONG32`; `ICorDebugValue3::GetSize`, bir `ULONG64`.</span><span class="sxs-lookup"><span data-stu-id="5d4d3-111">In [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="5d4d3-112">Bu, [ICorDebugValue3](icordebugvalue3-interface.md) arabiriminin 2GB ' i aşan dizilerin boyutunu rapor etmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d4d3-112">This enables the [ICorDebugValue3](icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d4d3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d4d3-113">Requirements</span></span>  
 <span data-ttu-id="5d4d3-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d4d3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d4d3-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5d4d3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d4d3-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5d4d3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d4d3-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d4d3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d4d3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d4d3-118">See also</span></span>

- [<span data-ttu-id="5d4d3-119">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d4d3-119">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="5d4d3-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5d4d3-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
