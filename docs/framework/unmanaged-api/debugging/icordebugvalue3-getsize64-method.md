---
description: 'Daha fazla bilgi edinin: ICorDebugValue3:: GetSize64 Yöntemi'
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
ms.openlocfilehash: ce7db5211c6a8fc16b58e0197fa3142b5b744d96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690203"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="6c3bd-103">ICorDebugValue3::GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c3bd-103">ICorDebugValue3::GetSize64 Method</span></span>

<span data-ttu-id="6c3bd-104">Bu [ICorDebugValue3](icordebugvalue3-interface.md) nesnesinin bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-104">Gets the size, in bytes, of this [ICorDebugValue3](icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c3bd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c3bd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c3bd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c3bd-106">Parameters</span></span>  

 <span data-ttu-id="6c3bd-107">Psıze</span><span class="sxs-lookup"><span data-stu-id="6c3bd-107">pSize</span></span>  
 <span data-ttu-id="6c3bd-108">dışı Bu nesnenin bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-108">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c3bd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c3bd-109">Remarks</span></span>  

 <span data-ttu-id="6c3bd-110">Bu değerin türü bir başvuru türü ise, bu yöntem nesnenin boyutu yerine işaretçinin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-110">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="6c3bd-111">`ICorDebugValue3::GetSize`Yöntemi, çıkış parametresinin türündeki [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md) yönteminden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-111">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="6c3bd-112">[ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md), çıkış parametresi bir `ULONG32` ; içinde, `ICorDebugValue3::GetSize` bir `ULONG64` .</span><span class="sxs-lookup"><span data-stu-id="6c3bd-112">In [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="6c3bd-113">Bu, [ICorDebugValue3](icordebugvalue3-interface.md) arabiriminin 2GB ' i aşan dizilerin boyutunu rapor etmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-113">This enables the [ICorDebugValue3](icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c3bd-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c3bd-114">Requirements</span></span>  

 <span data-ttu-id="6c3bd-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c3bd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c3bd-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6c3bd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c3bd-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6c3bd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c3bd-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c3bd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c3bd-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c3bd-119">See also</span></span>

- [<span data-ttu-id="6c3bd-120">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c3bd-120">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="6c3bd-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6c3bd-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
