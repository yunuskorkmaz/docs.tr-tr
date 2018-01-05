---
title: "ICorDebugRemote::DebugActiveProcessEx Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemote.DebugActiveProcessEx
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09bc98b477231eb1466300451585f4569aff222c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="b58bc-102">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b58bc-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="b58bc-103">Hata ayıklayıcı altında uzaktaki bir makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="b58bc-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b58bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b58bc-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b58bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b58bc-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="b58bc-106">[in] İşaretçi bir [Icordebugremotetarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b58bc-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="b58bc-107">Bu parametre, işlemin çalıştığı makine belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b58bc-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="b58bc-108">[in] Hata ayıklayıcısı ekli olduğu işlemin kimliği.</span><span class="sxs-lookup"><span data-stu-id="b58bc-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="b58bc-109">[in] `true` hata ayıklayıcı işlem için Win32 hata ayıklayıcı olarak davranır ve yönetilmeyen geri çağırmaları; gönderme gerekir, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="b58bc-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="b58bc-110">[out] Hata ayıklayıcı eklenmiş olması işlemi temsil eden bir "ICorDebugProcess" nesnesinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b58bc-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b58bc-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b58bc-111">Return Value</span></span>  
 <span data-ttu-id="b58bc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b58bc-112">S_OK</span></span>  
 <span data-ttu-id="b58bc-113">Uzak makinedeki işlemi başarıyla eklendi.</span><span class="sxs-lookup"><span data-stu-id="b58bc-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="b58bc-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="b58bc-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b58bc-115">Uzak makinedeki işlem eklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="b58bc-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b58bc-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b58bc-116">Remarks</span></span>  
 <span data-ttu-id="b58bc-117">Karışık mod hata ayıklaması Silverlight'ta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b58bc-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b58bc-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b58bc-118">Requirements</span></span>  
 <span data-ttu-id="b58bc-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b58bc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b58bc-120">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b58bc-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b58bc-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b58bc-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b58bc-122">**.NET framework sürümleri:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="b58bc-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b58bc-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b58bc-123">See Also</span></span>  
 [<span data-ttu-id="b58bc-124">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b58bc-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="b58bc-125">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b58bc-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="b58bc-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b58bc-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
