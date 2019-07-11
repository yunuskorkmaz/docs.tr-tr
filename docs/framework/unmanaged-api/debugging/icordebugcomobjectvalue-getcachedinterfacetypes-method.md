---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7325e84d8fe4df9a31543426c6376d0941306fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748456"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="65fd4-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Metodu</span><span class="sxs-lookup"><span data-stu-id="65fd4-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="65fd4-103">Bir numaralandırıcı, geçerli nesne için tür dönüştürme veya bırakıldığı olarak kullanılan, arabirim türlerinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="65fd4-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65fd4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65fd4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65fd4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65fd4-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="65fd4-106">[in] Yöntem yalnızca Windows çalışma zamanı arabirimleri döndürüp döndürmeyeceğini belirten bir değer (`IInspectable` arabirimleri) veya çalışma zamanı çağrılabilir sarmalayıcı (RCW) önbelleğe alınmış tüm COM arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="65fd4-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="65fd4-107">[out] Önbelleğe alınmış arabirim türleri temsil eden Icordebugtype nesneleri erişim sağlayan bir Icordebugtypeenum Numaralandırıcı adresini bir işaretçiye şunlara göre filtrelenmiş `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="65fd4-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65fd4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65fd4-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65fd4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65fd4-109">Requirements</span></span>  
 <span data-ttu-id="65fd4-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65fd4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65fd4-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65fd4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65fd4-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65fd4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65fd4-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65fd4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65fd4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65fd4-114">See also</span></span>

- [<span data-ttu-id="65fd4-115">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65fd4-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="65fd4-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="65fd4-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
