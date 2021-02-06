---
description: 'Daha fazla bilgi edinin: ICorDebugProcess5:: GetTypeId yöntemi'
title: ICorDebugProcess5::GetTypeID Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess5.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeID
helpviewer_keywords:
- ICorDebugProcess5::GetTypeID method [.NET Framework debugging]
- GetTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 47dbaea4-8857-462e-93ba-fff880fc9e50
topic_type:
- apiref
ms.openlocfilehash: 564fc2819c9c370844111cf497d62e6d89cb28b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649721"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="a62dd-103">ICorDebugProcess5::GetTypeID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a62dd-103">ICorDebugProcess5::GetTypeID Method</span></span>

<span data-ttu-id="a62dd-104">Bir nesne adresini [COR_TYPEID](cor-typeid-structure.md) tanımlayıcısına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a62dd-104">Converts an object address to a [COR_TYPEID](cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a62dd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a62dd-105">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a62dd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a62dd-106">Parameters</span></span>  

 `obj`  
 <span data-ttu-id="a62dd-107">'ndaki Nesne adresi.</span><span class="sxs-lookup"><span data-stu-id="a62dd-107">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="a62dd-108">Nesneyi tanımlayan [COR_TYPEID](cor-typeid-structure.md) değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a62dd-108">A pointer to the [COR_TYPEID](cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a62dd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a62dd-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a62dd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a62dd-110">Requirements</span></span>  

 <span data-ttu-id="a62dd-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a62dd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a62dd-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a62dd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a62dd-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a62dd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a62dd-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a62dd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62dd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a62dd-115">See also</span></span>

- [<span data-ttu-id="a62dd-116">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a62dd-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="a62dd-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a62dd-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
