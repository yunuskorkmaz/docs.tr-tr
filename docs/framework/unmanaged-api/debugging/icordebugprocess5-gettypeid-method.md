---
title: ICorDebugProcess5::GetTypeID Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cf72d0f41ee916db0e65cc6799217d19893628b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597105"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="c3950-102">ICorDebugProcess5::GetTypeID Metodu</span><span class="sxs-lookup"><span data-stu-id="c3950-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="c3950-103">Bir nesnenin adresine dönüştürür bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c3950-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3950-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3950-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3950-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3950-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="c3950-106">[in] Nesnesi adresi.</span><span class="sxs-lookup"><span data-stu-id="c3950-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="c3950-107">Bir işaretçi [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) nesneyi tanımlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="c3950-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3950-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3950-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3950-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3950-109">Requirements</span></span>  
 <span data-ttu-id="c3950-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3950-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3950-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3950-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3950-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3950-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3950-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3950-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3950-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3950-114">See also</span></span>
- [<span data-ttu-id="c3950-115">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3950-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="c3950-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c3950-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
