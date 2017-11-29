---
title: ICorDebugProcess5::GetArrayLayout Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetArrayLayout
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4c5d07e1645bc3736de2f8a298ad5b80e2cb26d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="ba031-102">ICorDebugProcess5::GetArrayLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="ba031-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="ba031-103">Dizi türleri Düzen hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba031-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba031-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba031-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba031-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba031-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="ba031-106">[in] A [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) belirteci düzeni istenen dizisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba031-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="ba031-107">[out] Bir işaretçi bir [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) bellek dizisinde düzeni hakkındaki bilgileri içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="ba031-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba031-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba031-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba031-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba031-109">Requirements</span></span>  
 <span data-ttu-id="ba031-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba031-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba031-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba031-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba031-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba031-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba031-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba031-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba031-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba031-114">See Also</span></span>  
 [<span data-ttu-id="ba031-115">Icordebugprocess5 arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba031-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="ba031-116">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ba031-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
