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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da0e62250dbef9be93ccee7020e23c3f83e85592
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223283"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="fa018-102">ICorDebugComObjectValue::GetCachedInterfacePointers Metodu</span><span class="sxs-lookup"><span data-stu-id="fa018-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="fa018-103">Geçerli çalışma zamanı çağrılabilir sarmalayıcı üzerinde (RCW) önbelleğe alınan ham arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="fa018-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa018-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa018-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa018-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa018-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="fa018-106">[in] Yöntemi yalnızca döndürür olup olmadığını gösteren bir değer [!INCLUDE[wrt](../../../../includes/wrt-md.md)] arabirimleri (`IInspectable` arabirimleri) veya çalışma zamanı çağrılabilir sarmalayıcı (RCW) önbelleğe alınan tüm COM arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="fa018-106">[in] A value that indicates whether the method will return only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="fa018-107">[in] Alınacak adresleri olan nesneler sayısı.</span><span class="sxs-lookup"><span data-stu-id="fa018-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="fa018-108">[out] Bir işaretçi sayısına `CORDB_ADDRESS` gerçekte döndürülen değerleri `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="fa018-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="fa018-109">Başlangıç adresi içeren bir dizinin işaretçisi `CORDB_ADDRESS` adresleri içeren değerler önbelleğe alınmış arabirim nesnelerini.</span><span class="sxs-lookup"><span data-stu-id="fa018-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa018-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa018-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa018-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa018-111">Requirements</span></span>  
 <span data-ttu-id="fa018-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa018-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa018-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa018-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa018-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa018-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fa018-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="fa018-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fa018-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa018-116">See also</span></span>

- [<span data-ttu-id="fa018-117">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa018-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="fa018-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fa018-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
