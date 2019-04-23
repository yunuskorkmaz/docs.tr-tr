---
title: ICorDebug::DebugActiveProcess Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b880358ed0d7bce4896217bc07c6ef6268d62962
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076282"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="3d276-102">ICorDebug::DebugActiveProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d276-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="3d276-103">Hata ayıklayıcı, varolan bir sürece ekler.</span><span class="sxs-lookup"><span data-stu-id="3d276-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d276-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d276-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d276-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d276-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="3d276-106">[in] Hata ayıklayıcı eklenmiş olduğu işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="3d276-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="3d276-107">[in] Ayarlanmış bir Boole değeri `true` hata ayıklayıcı Win32 hata ayıklayıcı işlemi gibi davranır ve yönetilmeyen geri çağırmaları; gönderme, aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="3d276-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="3d276-108">[out] Hata ayıklayıcı eklendikten işlemini temsil eden bir "ICorDebugProcess" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3d276-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d276-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d276-109">Remarks</span></span>  
 <span data-ttu-id="3d276-110">Birlikte çalışma hata ayıklama gibi IA-64 tabanlı ve AMD64 tabanlı platformlarda, Win9x ve x86 olmayan platformda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3d276-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d276-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d276-111">Requirements</span></span>  
 <span data-ttu-id="3d276-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d276-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d276-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d276-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d276-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d276-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d276-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d276-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d276-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d276-116">See also</span></span>

- [<span data-ttu-id="3d276-117">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d276-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
