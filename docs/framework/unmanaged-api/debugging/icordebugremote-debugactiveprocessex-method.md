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
ms.openlocfilehash: e0e3cdbff5054ec990c40c333ed4bd4029a91f12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420810"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="e2fb4-102">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2fb4-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="e2fb4-103">Hata ayıklayıcı altında uzaktaki bir makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="e2fb4-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2fb4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2fb4-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2fb4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2fb4-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="e2fb4-106">[in] İşaretçi bir [Icordebugremotetarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e2fb4-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="e2fb4-107">Bu parametre, işlemin çalıştığı makine belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e2fb4-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="e2fb4-108">[in] Hata ayıklayıcısı ekli olduğu işlemin kimliği.</span><span class="sxs-lookup"><span data-stu-id="e2fb4-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="e2fb4-109">[in] `true` hata ayıklayıcı işlem için Win32 hata ayıklayıcı olarak davranır ve yönetilmeyen geri çağırmaları; gönderme gerekir, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="e2fb4-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="e2fb4-110">[out] Hata ayıklayıcı eklenmiş olması işlemi temsil eden bir "ICorDebugProcess" nesnesinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2fb4-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2fb4-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e2fb4-111">Return Value</span></span>  
 <span data-ttu-id="e2fb4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2fb4-112">S_OK</span></span>  
 <span data-ttu-id="e2fb4-113">Uzak makinedeki işlemi başarıyla eklendi.</span><span class="sxs-lookup"><span data-stu-id="e2fb4-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="e2fb4-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="e2fb4-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e2fb4-115">Uzak makinedeki işlem eklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="e2fb4-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2fb4-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2fb4-116">Remarks</span></span>  
 <span data-ttu-id="e2fb4-117">Karışık mod hata ayıklaması Silverlight'ta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e2fb4-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2fb4-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2fb4-118">Requirements</span></span>  
 <span data-ttu-id="e2fb4-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2fb4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2fb4-120">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2fb4-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2fb4-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2fb4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2fb4-122">**.NET framework sürümleri:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e2fb4-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2fb4-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2fb4-123">See Also</span></span>  
 [<span data-ttu-id="e2fb4-124">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2fb4-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="e2fb4-125">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2fb4-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="e2fb4-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e2fb4-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
