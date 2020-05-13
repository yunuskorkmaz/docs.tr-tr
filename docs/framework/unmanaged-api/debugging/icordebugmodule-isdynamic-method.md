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
ms.openlocfilehash: 4517f266bbb500223214a6a8fe5881e8b29566c3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206893"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="c4fd9-102">ICorDebugModule::IsDynamic Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4fd9-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="c4fd9-103">Bu modülün dinamik olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="c4fd9-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4fd9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4fd9-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4fd9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4fd9-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="c4fd9-106">[out] `true` Bu modül dinamiktir; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="c4fd9-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4fd9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4fd9-107">Remarks</span></span>  
 <span data-ttu-id="c4fd9-108">Dinamik bir modül, modül yüklendikten sonra bile yeni sınıflar ekleyebilir ve var olan sınıfları silebilir.</span><span class="sxs-lookup"><span data-stu-id="c4fd9-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="c4fd9-109">[ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları, bir sınıf eklendiğinde veya silindiğinde hata ayıklayıcıyı bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="c4fd9-109">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4fd9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4fd9-110">Requirements</span></span>  
 <span data-ttu-id="c4fd9-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4fd9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4fd9-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c4fd9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4fd9-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c4fd9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4fd9-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4fd9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
