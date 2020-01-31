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
ms.openlocfilehash: 540ca78c5548d4fbdd3338671ea02314736f15cd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792357"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="82047-102">ICorDebugProcess5::GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="82047-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="82047-103">Bir nesne adresini bir "ICorDebugObjectValue" nesnesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="82047-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82047-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82047-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82047-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82047-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="82047-106">'ndaki Nesne adresi.</span><span class="sxs-lookup"><span data-stu-id="82047-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="82047-107">dışı "ICorDebugObjectValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="82047-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82047-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82047-108">Remarks</span></span>  
 <span data-ttu-id="82047-109">`addr` geçerli bir yönetilen nesneyi işaret etmez, `GetObject` yöntemi `E_FAIL`döndürür.</span><span class="sxs-lookup"><span data-stu-id="82047-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82047-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82047-110">Requirements</span></span>  
 <span data-ttu-id="82047-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82047-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82047-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="82047-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82047-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="82047-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82047-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82047-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82047-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82047-115">See also</span></span>

- [<span data-ttu-id="82047-116">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82047-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="82047-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="82047-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
