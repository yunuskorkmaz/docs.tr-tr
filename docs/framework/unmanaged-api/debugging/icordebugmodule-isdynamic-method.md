---
title: "ICorDebugModule::IsDynamic Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.IsDynamic
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3583749ddb48015b43d45061d3e4cb10e08016b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="c67fc-102">ICorDebugModule::IsDynamic Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c67fc-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="c67fc-103">Bu modül dinamik olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="c67fc-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c67fc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c67fc-104">Syntax</span></span>  
  
```  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c67fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c67fc-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="c67fc-106">[out] `true` bu modül, dinamik Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="c67fc-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c67fc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c67fc-107">Remarks</span></span>  
 <span data-ttu-id="c67fc-108">Dinamik bir modül, yeni sınıflar ekleyebilirsiniz ve modül bile yüklendikten sonra varolan sınıfları silin.</span><span class="sxs-lookup"><span data-stu-id="c67fc-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="c67fc-109">[Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [Icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri aramalar bildirmek hata ayıklayıcı bir sınıf zaman eklenmiş veya silinmiş.</span><span class="sxs-lookup"><span data-stu-id="c67fc-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c67fc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c67fc-110">Requirements</span></span>  
 <span data-ttu-id="c67fc-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c67fc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c67fc-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c67fc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c67fc-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c67fc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c67fc-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c67fc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
