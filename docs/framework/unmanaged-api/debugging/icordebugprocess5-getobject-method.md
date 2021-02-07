---
description: 'Daha fazla bilgi edinin: ICorDebugProcess5:: GetObject yöntemi'
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
ms.openlocfilehash: 4e295e1afc19cc5b9ca763b04b05097d48f0302c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746367"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="5a052-103">ICorDebugProcess5::GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="5a052-103">ICorDebugProcess5::GetObject Method</span></span>

<span data-ttu-id="5a052-104">Bir nesne adresini bir "ICorDebugObjectValue" nesnesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5a052-104">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a052-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a052-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a052-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a052-106">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="5a052-107">'ndaki Nesne adresi.</span><span class="sxs-lookup"><span data-stu-id="5a052-107">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="5a052-108">dışı "ICorDebugObjectValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5a052-108">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a052-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a052-109">Remarks</span></span>  

 <span data-ttu-id="5a052-110">`addr`Geçerli bir yönetilen nesneye işaret etmez, `GetObject` yöntemi döndürür `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="5a052-110">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a052-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a052-111">Requirements</span></span>  

 <span data-ttu-id="5a052-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a052-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a052-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5a052-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a052-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5a052-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a052-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a052-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a052-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a052-116">See also</span></span>

- [<span data-ttu-id="5a052-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a052-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="5a052-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5a052-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
