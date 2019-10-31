---
title: ICorDebugComObjectValue::GetCachedInterfacePointers Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
ms.openlocfilehash: c1e2b557a5e5794c50986b1af8ec39faba845cc9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125511"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="d5598-102">ICorDebugComObjectValue::GetCachedInterfacePointers Metodu</span><span class="sxs-lookup"><span data-stu-id="d5598-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="d5598-103">Geçerli çalışma zamanında çağrılabilir sarmalayıcı (RCW) üzerinde önbelleğe alınmış ham arabirim işaretçilerini alır.</span><span class="sxs-lookup"><span data-stu-id="d5598-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5598-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5598-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5598-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5598-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="d5598-106">'ndaki Yöntemin yalnızca, çalışma zamanı çağrılabilir sarmalayıcı (RCW) tarafından önbelleğe alınan Windows Çalışma Zamanı arabirimlerini (`IInspectable` arabirimleri) veya tüm COM arabirimlerini döndürmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d5598-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="d5598-107">'ndaki Adresleri alınacak olan nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="d5598-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d5598-108">dışı Aslında `ptrs`döndürülen `CORDB_ADDRESS` değerlerinin sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5598-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="d5598-109">Önbelleğe alınmış arabirim nesnelerinin adreslerini içeren `CORDB_ADDRESS` değerleri dizisinin başlangıç adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5598-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5598-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5598-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5598-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5598-111">Requirements</span></span>  
 <span data-ttu-id="d5598-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5598-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5598-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d5598-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5598-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d5598-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5598-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5598-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5598-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5598-116">See also</span></span>

- [<span data-ttu-id="d5598-117">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5598-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="d5598-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d5598-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
