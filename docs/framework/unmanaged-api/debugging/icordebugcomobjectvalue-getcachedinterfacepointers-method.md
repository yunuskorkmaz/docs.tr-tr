---
description: ': ICorDebugComObjectValue:: Getcachedınterfaceişaretçiler yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 737d71f6aa903a3dfa97f583b47a322ec074147f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710861"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="25538-103">ICorDebugComObjectValue::GetCachedInterfacePointers Metodu</span><span class="sxs-lookup"><span data-stu-id="25538-103">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>

<span data-ttu-id="25538-104">Geçerli çalışma zamanında çağrılabilir sarmalayıcı (RCW) üzerinde önbelleğe alınmış ham arabirim işaretçilerini alır.</span><span class="sxs-lookup"><span data-stu-id="25538-104">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25538-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25538-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25538-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25538-106">Parameters</span></span>  

 `bIInspectableOnly`  
 <span data-ttu-id="25538-107">'ndaki Yöntemin yalnızca `IInspectable` , çalışma zamanı çağrılabilir sarmalayıcı (RCW) tarafından önbelleğe alınan Windows çalışma zamanı arabirimleri (arabirimler) veya tüm com arabirimlerini döndürmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="25538-107">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="25538-108">'ndaki Adresleri alınacak olan nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="25538-108">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="25538-109">dışı `CORDB_ADDRESS` Aslında ' de döndürülen değer sayısına yönelik bir işaretçi `ptrs` .</span><span class="sxs-lookup"><span data-stu-id="25538-109">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="25538-110">Önbelleğe alınmış arabirim nesnelerinin adreslerini içeren bir değer dizisinin başlangıç adresine yönelik bir işaretçi `CORDB_ADDRESS` .</span><span class="sxs-lookup"><span data-stu-id="25538-110">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25538-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25538-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25538-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25538-112">Requirements</span></span>  

 <span data-ttu-id="25538-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25538-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25538-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="25538-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25538-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="25538-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25538-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25538-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25538-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25538-117">See also</span></span>

- [<span data-ttu-id="25538-118">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25538-118">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="25538-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="25538-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
