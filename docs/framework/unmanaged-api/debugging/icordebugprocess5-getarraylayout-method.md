---
title: ICorDebugProcess5::GetArrayLayout Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6f739902738f05e103cce9365a3afc0379f9b0e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646990"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="4056b-102">ICorDebugProcess5::GetArrayLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="4056b-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="4056b-103">Dizi türleri Düzen hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4056b-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4056b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4056b-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4056b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4056b-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="4056b-106">[in] A [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) belirteci düzenini istenen dizisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4056b-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="4056b-107">[out] Bir işaretçi bir [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) dizinin bellek düzeni hakkındaki bilgileri içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="4056b-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4056b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4056b-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4056b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4056b-109">Requirements</span></span>  
 <span data-ttu-id="4056b-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4056b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4056b-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4056b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4056b-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4056b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4056b-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4056b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4056b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4056b-114">See also</span></span>
- [<span data-ttu-id="4056b-115">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4056b-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="4056b-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4056b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
