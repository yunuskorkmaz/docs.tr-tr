---
title: ICorDebugProcess5::GetObject Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
ms.openlocfilehash: ff2913399e1dbeb33bbfb697058db3caf2a8d1fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713112"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="d1bf4-102">ICorDebugProcess5::GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="d1bf4-102">ICorDebugProcess5::GetObject Method</span></span>

<span data-ttu-id="d1bf4-103">Bir nesne adresini bir "ICorDebugObjectValue" nesnesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d1bf4-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1bf4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d1bf4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1bf4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1bf4-105">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="d1bf4-106">'ndaki Nesne adresi.</span><span class="sxs-lookup"><span data-stu-id="d1bf4-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="d1bf4-107">dışı "ICorDebugObjectValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d1bf4-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1bf4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1bf4-108">Remarks</span></span>  

 <span data-ttu-id="d1bf4-109">`addr`Geçerli bir yönetilen nesneye işaret etmez, `GetObject` yöntemi döndürür `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="d1bf4-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1bf4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1bf4-110">Requirements</span></span>  

 <span data-ttu-id="d1bf4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1bf4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1bf4-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d1bf4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1bf4-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d1bf4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1bf4-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1bf4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1bf4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1bf4-115">See also</span></span>

- [<span data-ttu-id="d1bf4-116">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1bf4-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="d1bf4-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d1bf4-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
