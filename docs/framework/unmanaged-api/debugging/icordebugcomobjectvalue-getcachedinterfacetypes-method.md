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
ms.openlocfilehash: 6b02657012870de4d0f888f6c05b115b25073fa2
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892829"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="924c5-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Metodu</span><span class="sxs-lookup"><span data-stu-id="924c5-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="924c5-103">Geçerli nesnenin atanmış veya olarak kullanıldığı arabirim türleri için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="924c5-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="924c5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="924c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="924c5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="924c5-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="924c5-106">'ndaki Yöntemin yalnızca Windows Çalışma Zamanı arabirimleri (`IInspectable` arabirimler) veya çalışma zamanı çağrılabilir sarmalayıcı (RCW) tarafından önbelleğe alınmış tüm com arabirimlerini döndürüp döndürmediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="924c5-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="924c5-107">dışı Öğesine `bIInspectableOnly`göre filtrelenmiş önbelleğe alınmış arabirim türlerini temsil eden ICorDebugType nesnelerine erişim sağlayan ICorDebugTypeEnum Numaralandırıcı adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="924c5-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="924c5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="924c5-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="924c5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="924c5-109">Requirements</span></span>  
 <span data-ttu-id="924c5-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="924c5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="924c5-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="924c5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="924c5-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="924c5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="924c5-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="924c5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="924c5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="924c5-114">See also</span></span>

- [<span data-ttu-id="924c5-115">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="924c5-115">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="924c5-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="924c5-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
