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
ms.openlocfilehash: db5d07d2b9a295a5cd21b4d4af954503b8bd7a8b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763659"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="2d1ff-102">ICorDebugModule::IsDynamic Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d1ff-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="2d1ff-103">Bu modül dinamik olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="2d1ff-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d1ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d1ff-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d1ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d1ff-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="2d1ff-106">[out] `true` bu modül dinamik; Aksi takdirde ise `false`.</span><span class="sxs-lookup"><span data-stu-id="2d1ff-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d1ff-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d1ff-107">Remarks</span></span>  
 <span data-ttu-id="2d1ff-108">Dinamik modül, yeni sınıflar ekleyebilirsiniz ve modül yüklendikten sonra mevcut sınıfları silin.</span><span class="sxs-lookup"><span data-stu-id="2d1ff-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="2d1ff-109">[Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [Icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları bildirmek hata ayıklayıcı bir sınıf, eklenmiş veya silinmiş.</span><span class="sxs-lookup"><span data-stu-id="2d1ff-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d1ff-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d1ff-110">Requirements</span></span>  
 <span data-ttu-id="2d1ff-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d1ff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d1ff-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d1ff-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d1ff-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d1ff-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d1ff-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d1ff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
