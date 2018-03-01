---
title: ICorDebugProcess5::GetTypeID Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f76285fceaa32f7c8b62b5cdf2ae7b4e9ec00de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5gettypeid-method"></a><span data-ttu-id="1de22-102">ICorDebugProcess5::GetTypeID Metodu</span><span class="sxs-lookup"><span data-stu-id="1de22-102">ICorDebugProcess5::GetTypeID Method</span></span>
<span data-ttu-id="1de22-103">Bir nesne adresine dönüştüren bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1de22-103">Converts an object address to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1de22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1de22-104">Syntax</span></span>  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1de22-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1de22-105">Parameters</span></span>  
 `obj`  
 <span data-ttu-id="1de22-106">[in] Nesne adresi.</span><span class="sxs-lookup"><span data-stu-id="1de22-106">[in] The object address.</span></span>  
  
 `pId`  
 <span data-ttu-id="1de22-107">Bir işaretçi [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) nesneyi tanımlayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="1de22-107">A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1de22-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1de22-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1de22-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1de22-109">Requirements</span></span>  
 <span data-ttu-id="1de22-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1de22-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1de22-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1de22-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1de22-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1de22-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1de22-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1de22-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1de22-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1de22-114">See Also</span></span>  
 [<span data-ttu-id="1de22-115">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1de22-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="1de22-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1de22-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
