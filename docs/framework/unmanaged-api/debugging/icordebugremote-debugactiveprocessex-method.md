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
ms.openlocfilehash: eb085cc486c307a308258709f4c58619597bc202
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608394"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="bbbdc-102">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbbdc-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="bbbdc-103">Hata ayıklayıcısı altında uzak bir makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="bbbdc-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbbdc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbbdc-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbbdc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbbdc-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="bbbdc-106">[in] İşaretçi bir [Icordebugremotetarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bbbdc-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="bbbdc-107">Bu parametre, işlem üzerinde çalıştığı makinenin belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbbdc-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="bbbdc-108">[in] Hata ayıklayıcı eklenmiş olduğu işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="bbbdc-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="bbbdc-109">[in] `true` hata ayıklayıcı Win32 hata ayıklayıcı işlemi gibi davranır ve gönderme yönetilmeyen geri çağırmaları; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="bbbdc-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="bbbdc-110">[out] Hata ayıklayıcı eklendikten işlemini temsil eden bir "ICorDebugProcess" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bbbdc-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbbdc-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bbbdc-111">Return Value</span></span>  
 <span data-ttu-id="bbbdc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="bbbdc-112">S_OK</span></span>  
 <span data-ttu-id="bbbdc-113">İşlem uzak makinede başarıyla kullanıma açıldı.</span><span class="sxs-lookup"><span data-stu-id="bbbdc-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="bbbdc-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="bbbdc-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="bbbdc-115">Uzak makinede işlemine iliştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="bbbdc-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbbdc-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbbdc-116">Remarks</span></span>  
 <span data-ttu-id="bbbdc-117">Silverlight'ta, karma mod hata ayıklaması desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="bbbdc-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbbdc-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbbdc-118">Requirements</span></span>  
 <span data-ttu-id="bbbdc-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbbdc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbbdc-120">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbbdc-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbbdc-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbbdc-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbbdc-122">**.NET framework sürümleri:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="bbbdc-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbbdc-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbbdc-123">See also</span></span>
- [<span data-ttu-id="bbbdc-124">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbbdc-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="bbbdc-125">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbbdc-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="bbbdc-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bbbdc-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
