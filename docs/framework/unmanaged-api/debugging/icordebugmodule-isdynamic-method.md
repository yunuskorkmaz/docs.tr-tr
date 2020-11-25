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
ms.openlocfilehash: 98c01993a85ed07d961902d8a098a96df4702c76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709836"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="ba452-102">ICorDebugModule::IsDynamic Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba452-102">ICorDebugModule::IsDynamic Method</span></span>

<span data-ttu-id="ba452-103">Bu modülün dinamik olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ba452-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba452-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ba452-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba452-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba452-105">Parameters</span></span>  

 `pDynamic`  
 <span data-ttu-id="ba452-106">[out] `true` Bu modül dinamiktir; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="ba452-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba452-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba452-107">Remarks</span></span>  

 <span data-ttu-id="ba452-108">Dinamik bir modül, modül yüklendikten sonra bile yeni sınıflar ekleyebilir ve var olan sınıfları silebilir.</span><span class="sxs-lookup"><span data-stu-id="ba452-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="ba452-109">[ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları, bir sınıf eklendiğinde veya silindiğinde hata ayıklayıcıyı bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="ba452-109">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba452-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba452-110">Requirements</span></span>  

 <span data-ttu-id="ba452-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba452-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba452-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ba452-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba452-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ba452-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba452-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba452-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
