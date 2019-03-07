---
title: ICorDebugModule::IsDynamic Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8012d669cabc1bb589dcfe66bdf2e9b83dc5cb2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502455"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="94044-102">ICorDebugModule::IsDynamic Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94044-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="94044-103">Bu modül dinamik olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="94044-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94044-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94044-104">Syntax</span></span>  
  
```  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94044-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94044-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="94044-106">[out] `true` bu modül dinamik; Aksi takdirde ise `false`.</span><span class="sxs-lookup"><span data-stu-id="94044-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94044-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94044-107">Remarks</span></span>  
 <span data-ttu-id="94044-108">Dinamik modül, yeni sınıflar ekleyebilirsiniz ve modül yüklendikten sonra mevcut sınıfları silin.</span><span class="sxs-lookup"><span data-stu-id="94044-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="94044-109">[Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [Icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları bildirmek hata ayıklayıcı bir sınıf, eklenmiş veya silinmiş.</span><span class="sxs-lookup"><span data-stu-id="94044-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94044-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94044-110">Requirements</span></span>  
 <span data-ttu-id="94044-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94044-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94044-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94044-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94044-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94044-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94044-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94044-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
