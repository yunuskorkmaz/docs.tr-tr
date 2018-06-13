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
ms.openlocfilehash: e96dccdd2836eebb08e88fe09dda531cd62baeee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420007"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="084b1-102">ICorDebugProcess5::GetArrayLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="084b1-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="084b1-103">Dizi türleri Düzen hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="084b1-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="084b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="084b1-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="084b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="084b1-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="084b1-106">[in] A [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) belirteci düzeni istenen dizisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="084b1-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="084b1-107">[out] Bir işaretçi bir [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) bellek dizisinde düzeni hakkındaki bilgileri içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="084b1-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="084b1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="084b1-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="084b1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="084b1-109">Requirements</span></span>  
 <span data-ttu-id="084b1-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="084b1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="084b1-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="084b1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="084b1-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="084b1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="084b1-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="084b1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="084b1-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="084b1-114">See Also</span></span>  
 [<span data-ttu-id="084b1-115">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="084b1-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="084b1-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="084b1-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
