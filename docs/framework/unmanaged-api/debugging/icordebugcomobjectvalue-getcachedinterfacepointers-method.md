---
title: ICorDebugComObjectValue::GetCachedInterfacePointers Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2b47395235ce21c7d40e4413702e6c655493a739
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="4c166-102">ICorDebugComObjectValue::GetCachedInterfacePointers Metodu</span><span class="sxs-lookup"><span data-stu-id="4c166-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="4c166-103">Geçerli çalışma zamanı aranabilir sarmalayıcısı üzerinde (RCW) önbelleğe ham arabirim işaretçileri alır.</span><span class="sxs-lookup"><span data-stu-id="4c166-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c166-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c166-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c166-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c166-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="4c166-106">[in] Yöntem yalnızca döndürür olup olmadığını belirten bir değer [!INCLUDE[wrt](../../../../includes/wrt-md.md)] arabirimleri (`IInspectable` arabirimleri) veya çalışma zamanı aranabilir sarmalayıcısı (RCW) önbelleğe alınan tüm COM arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="4c166-106">[in] A value that indicates whether the method will return only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="4c166-107">[in] Alınacak olan adresler nesnelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="4c166-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4c166-108">[out] Sayısını gösteren bir işaretçi `CORDB_ADDRESS` gerçekte döndürülen değerleri `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="4c166-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="4c166-109">Bir dizi başlangıç adresini gösteren bir işaretçi `CORDB_ADDRESS` adreslerini içeren bir değerler arabirimi nesneleri önbelleğe alınmış.</span><span class="sxs-lookup"><span data-stu-id="4c166-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c166-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c166-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c166-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c166-111">Requirements</span></span>  
 <span data-ttu-id="4c166-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c166-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c166-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c166-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c166-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c166-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c166-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c166-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c166-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c166-116">See Also</span></span>  
 [<span data-ttu-id="4c166-117">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c166-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [<span data-ttu-id="4c166-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4c166-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
