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
ms.openlocfilehash: 6eb26de83a6cdce47477e6cb3dffd6a94d889975
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397021"
---
# <a name="icordebugvalue3getsize64-method"></a><span data-ttu-id="d85d7-102">ICorDebugValue3::GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d85d7-102">ICorDebugValue3::GetSize64 Method</span></span>
<span data-ttu-id="d85d7-103">Bu [ICorDebugValue3](icordebugvalue3-interface.md) nesnesinin bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="d85d7-103">Gets the size, in bytes, of this [ICorDebugValue3](icordebugvalue3-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d85d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d85d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d85d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d85d7-105">Parameters</span></span>  
 <span data-ttu-id="d85d7-106">Psıze</span><span class="sxs-lookup"><span data-stu-id="d85d7-106">pSize</span></span>  
 <span data-ttu-id="d85d7-107">dışı Bu nesnenin bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d85d7-107">[out] A pointer to the size, in bytes, of this object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d85d7-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d85d7-108">Remarks</span></span>  
 <span data-ttu-id="d85d7-109">Bu değerin türü bir başvuru türü ise, bu yöntem nesnenin boyutu yerine işaretçinin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d85d7-109">If this value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="d85d7-110">`ICorDebugValue3::GetSize`Yöntemi, çıkış parametresinin türündeki [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md) yönteminden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d85d7-110">The `ICorDebugValue3::GetSize` method differs from the [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md) method in the type of its output parameter.</span></span> <span data-ttu-id="d85d7-111">[ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md), çıkış parametresi bir `ULONG32` ; içinde, `ICorDebugValue3::GetSize` bir `ULONG64` .</span><span class="sxs-lookup"><span data-stu-id="d85d7-111">In [ICorDebugValue::GetSize](icordebugvalue-getsize-method.md), the output parameter is a `ULONG32`; in `ICorDebugValue3::GetSize`, it is a `ULONG64`.</span></span> <span data-ttu-id="d85d7-112">Bu, [ICorDebugValue3](icordebugvalue3-interface.md) arabiriminin 2GB ' i aşan dizilerin boyutunu rapor etmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d85d7-112">This enables the [ICorDebugValue3](icordebugvalue3-interface.md) interface to report the size of arrays that exceed 2GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d85d7-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d85d7-113">Requirements</span></span>  
 <span data-ttu-id="d85d7-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d85d7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d85d7-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d85d7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d85d7-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d85d7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d85d7-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d85d7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d85d7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d85d7-118">See also</span></span>

- [<span data-ttu-id="d85d7-119">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d85d7-119">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="d85d7-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d85d7-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
