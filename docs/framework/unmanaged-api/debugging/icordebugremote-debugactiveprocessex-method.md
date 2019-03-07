---
title: ICorDebugRemote::DebugActiveProcessEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eba0ff6e545a5da5d7733a157b73ddd66e717de9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477120"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="1cd33-102">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1cd33-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="1cd33-103">Hata ayıklayıcısı altında uzak bir makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="1cd33-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cd33-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1cd33-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cd33-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1cd33-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="1cd33-106">[in] İşaretçi bir [Icordebugremotetarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="1cd33-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="1cd33-107">Bu parametre, işlem üzerinde çalıştığı makinenin belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1cd33-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="1cd33-108">[in] Hata ayıklayıcı eklenmiş olduğu işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="1cd33-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="1cd33-109">[in] `true` hata ayıklayıcı Win32 hata ayıklayıcı işlemi gibi davranır ve gönderme yönetilmeyen geri çağırmaları; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="1cd33-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="1cd33-110">[out] Hata ayıklayıcı eklendikten işlemini temsil eden bir "ICorDebugProcess" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1cd33-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cd33-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1cd33-111">Return Value</span></span>  
 <span data-ttu-id="1cd33-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1cd33-112">S_OK</span></span>  
 <span data-ttu-id="1cd33-113">İşlem uzak makinede başarıyla kullanıma açıldı.</span><span class="sxs-lookup"><span data-stu-id="1cd33-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="1cd33-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="1cd33-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="1cd33-115">Uzak makinede işlemine iliştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="1cd33-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cd33-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1cd33-116">Remarks</span></span>  
 <span data-ttu-id="1cd33-117">Silverlight'ta, karma mod hata ayıklaması desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="1cd33-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cd33-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1cd33-118">Requirements</span></span>  
 <span data-ttu-id="1cd33-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cd33-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cd33-120">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1cd33-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1cd33-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cd33-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cd33-122">**.NET framework sürümleri:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="1cd33-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cd33-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cd33-123">See also</span></span>
- [<span data-ttu-id="1cd33-124">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1cd33-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="1cd33-125">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1cd33-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="1cd33-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1cd33-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
