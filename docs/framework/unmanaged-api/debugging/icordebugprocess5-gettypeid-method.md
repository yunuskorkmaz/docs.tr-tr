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
ms.openlocfilehash: b63c6ca8ead2a401f907ea6569e966c6470aca13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421957"
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="2cefc-102">ICorDebugProcess5::GetTypeID Metodu</span><span class="sxs-lookup"><span data-stu-id="2cefc-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="2cefc-103">Bir nesne adresine dönüştüren bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2cefc-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cefc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cefc-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2cefc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2cefc-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="2cefc-106">[in] Nesne adresi.</span><span class="sxs-lookup"><span data-stu-id="2cefc-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="2cefc-107">Bir işaretçi [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) nesneyi tanımlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="2cefc-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cefc-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cefc-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cefc-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2cefc-109">Requirements</span></span>  
 <span data-ttu-id="2cefc-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cefc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cefc-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cefc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cefc-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cefc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cefc-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cefc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cefc-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2cefc-114">See Also</span></span>  
 [<span data-ttu-id="2cefc-115">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cefc-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="2cefc-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2cefc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
