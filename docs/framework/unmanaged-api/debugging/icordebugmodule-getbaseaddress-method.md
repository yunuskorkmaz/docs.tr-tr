---
title: ICorDebugModule::GetBaseAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11685e8ceba1638ce99a8c4c47b66d0ae2e67714
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476172"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="d8394-102">ICorDebugModule::GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8394-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="d8394-103">Modül temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="d8394-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8394-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8394-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8394-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8394-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="d8394-106">[out] A `CORDB_ADDRESS` modülü temel adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8394-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8394-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8394-107">Remarks</span></span>  
 <span data-ttu-id="d8394-108">Modül bir yerel ise (diğer bir deyişle, modül NGen.exe yerel Görüntü Oluşturucu tarafından üretilmişse) görüntü, temel adresini sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="d8394-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8394-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8394-109">Requirements</span></span>  
 <span data-ttu-id="d8394-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8394-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8394-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8394-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8394-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8394-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8394-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8394-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8394-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8394-114">See also</span></span>


