---
title: "ICorDebug::DebugActiveProcess Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 10cb2a5323db67c6f5664e13cb1f97d1a807d20c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="8d865-102">ICorDebug::DebugActiveProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d865-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="8d865-103">Hata ayıklayıcı varolan bir işlemi ekler.</span><span class="sxs-lookup"><span data-stu-id="8d865-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d865-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d865-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d865-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d865-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="8d865-106">[in] Hata ayıklayıcısı ekli olduğu işlemin kimliği.</span><span class="sxs-lookup"><span data-stu-id="8d865-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="8d865-107">[in] Ayarlamak için Boolean değeri `true` hata ayıklayıcı işlem için Win32 hata ayıklayıcı olarak davranır ve yönetilmeyen geri çağırmaları; gönderme gerekir, aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="8d865-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="8d865-108">[out] Hata ayıklayıcı eklenmiş olması işlemi temsil eden bir "ICorDebugProcess" nesnesinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8d865-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d865-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d865-109">Remarks</span></span>  
 <span data-ttu-id="8d865-110">Birlikte çalışma hata ayıklama IA-64 tabanlı ve AMD64 tabanlı platformları gibi Win9x ve x86 olmayan platformlarda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="8d865-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d865-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d865-111">Requirements</span></span>  
 <span data-ttu-id="8d865-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d865-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d865-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d865-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d865-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d865-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d865-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d865-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d865-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d865-116">See Also</span></span>  
 [<span data-ttu-id="8d865-117">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d865-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
