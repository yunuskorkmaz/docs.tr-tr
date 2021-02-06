---
description: ': ICorDebugModule:: IsDynamic yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 06ecb7aaffbe73da29bbdbba9446839db54c58c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660108"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="3d422-103">ICorDebugModule::IsDynamic Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d422-103">ICorDebugModule::IsDynamic Method</span></span>

<span data-ttu-id="3d422-104">Bu modülün dinamik olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="3d422-104">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d422-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d422-105">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d422-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d422-106">Parameters</span></span>  

 `pDynamic`  
 <span data-ttu-id="3d422-107">[out] `true` Bu modül dinamiktir; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="3d422-107">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d422-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d422-108">Remarks</span></span>  

 <span data-ttu-id="3d422-109">Dinamik bir modül, modül yüklendikten sonra bile yeni sınıflar ekleyebilir ve var olan sınıfları silebilir.</span><span class="sxs-lookup"><span data-stu-id="3d422-109">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="3d422-110">[ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları, bir sınıf eklendiğinde veya silindiğinde hata ayıklayıcıyı bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="3d422-110">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d422-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d422-111">Requirements</span></span>  

 <span data-ttu-id="3d422-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d422-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d422-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3d422-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d422-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3d422-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d422-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d422-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
