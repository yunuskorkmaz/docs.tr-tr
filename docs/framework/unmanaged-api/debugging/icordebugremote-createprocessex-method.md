---
title: "ICorDebugRemote::CreateProcessEx Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemote.CreateProcessEx
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 00709ffe4695ea0b56982cb60df15c2991b49d4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="c79e3-102">ICorDebugRemote::CreateProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c79e3-102">ICorDebugRemote::CreateProcessEx Method</span></span>
<span data-ttu-id="c79e3-103">Hata ayıklayıcı altında uzaktaki bir makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="c79e3-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c79e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c79e3-104">Syntax</span></span>  
  
```  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c79e3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c79e3-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="c79e3-106">[in] İşaretçi bir [Icordebugremotetarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c79e3-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="c79e3-107">İşlem başlatılacak uzak makine belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c79e3-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="c79e3-108">[in] İşaretçi null ile sonlandırılmış dizeye başlatılan işlem tarafından yürütülecek Modülü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c79e3-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="c79e3-109">Modül çağırma işlemi güvenlik bağlamında çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="c79e3-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="c79e3-110">[in] İşaretçi null ile sonlandırılmış dizeye başlatılan işlem tarafından yürütülecek komut satırını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c79e3-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="c79e3-111">[in] Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c79e3-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="c79e3-112">[in] Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c79e3-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="c79e3-113">[in] Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c79e3-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="c79e3-114">[in] Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c79e3-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="c79e3-115">[in] Yeni işlem için bir ortam bloğu işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c79e3-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="c79e3-116">[in] İşaretçi null ile sonlandırılmış dizeye işlemi için geçerli dizin tam yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c79e3-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="c79e3-117">Bu parametre null ise, yeni işlem çağırma işlemi aynı geçerli sürücü ve dizine sahip.</span><span class="sxs-lookup"><span data-stu-id="c79e3-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="c79e3-118">[in] Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c79e3-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="c79e3-119">[in] Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c79e3-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="c79e3-120">[in] Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c79e3-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="c79e3-121">[out] İşlemi temsil eden bir "Icordebugprocess arabirimi" nesnesi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c79e3-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c79e3-122">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c79e3-122">Return Value</span></span>  
 <span data-ttu-id="c79e3-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="c79e3-123">S_OK</span></span>  
 <span data-ttu-id="c79e3-124">Hata ayıklama için uzak makineye ve döndürülen bir "Icordebugprocess arabirimi" işlem başarıyla başlattı.</span><span class="sxs-lookup"><span data-stu-id="c79e3-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="c79e3-125">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="c79e3-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c79e3-126">Uzak makinedeki işlemi başlatmak ve hata ayıklama için "Icordebugprocess arabirimi" dönmek oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="c79e3-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c79e3-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c79e3-127">Remarks</span></span>  
 <span data-ttu-id="c79e3-128">Karışık mod hata ayıklaması Silverlight'ta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c79e3-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c79e3-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c79e3-129">Requirements</span></span>  
 <span data-ttu-id="c79e3-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c79e3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c79e3-131">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="c79e3-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c79e3-132">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c79e3-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c79e3-133">**.NET framework sürümleri:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="c79e3-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c79e3-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c79e3-134">See Also</span></span>  
 [<span data-ttu-id="c79e3-135">Icordebugremote arabirimi</span><span class="sxs-lookup"><span data-stu-id="c79e3-135">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="c79e3-136">Icordebug arabirimi</span><span class="sxs-lookup"><span data-stu-id="c79e3-136">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="c79e3-137">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c79e3-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
