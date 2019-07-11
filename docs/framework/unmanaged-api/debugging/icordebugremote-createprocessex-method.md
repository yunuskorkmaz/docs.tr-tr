---
title: ICorDebugRemote::CreateProcessEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d05384af8201fae8cf81650d38c99a5c44e6bd16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744782"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="c38db-102">ICorDebugRemote::CreateProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c38db-102">ICorDebugRemote::CreateProcessEx Method</span></span>
<span data-ttu-id="c38db-103">Hata ayıklayıcısı altında uzak bir makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="c38db-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c38db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c38db-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="c38db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c38db-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="c38db-106">[in] İşaretçi bir [Icordebugremotetarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c38db-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="c38db-107">İşlem başlatılacak uzak makineye belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c38db-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="c38db-108">[in] Başlatılan işlem tarafından yürütülecek modülü belirtiyorsa null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c38db-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="c38db-109">Modül çağırma işleminin bağlamında çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="c38db-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="c38db-110">[in] Başlatılan işlem tarafından yürütülecek komut satırı belirten bir null ile sonlandırılmış dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c38db-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="c38db-111">[in] Uzaktan hata ayıklama için kullanılmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c38db-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="c38db-112">[in] Uzaktan hata ayıklama için kullanılmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c38db-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="c38db-113">[in] Uzaktan hata ayıklama için kullanılmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c38db-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="c38db-114">[in] Uzaktan hata ayıklama için kullanılmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c38db-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="c38db-115">[in] Yeni işlem için bir ortam bloğuna işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c38db-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="c38db-116">[in] İşlem için geçerli dizin tam yolunu belirtir null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c38db-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="c38db-117">Bu parametre null ise, yeni işlem çağırma işlemi aynı geçerli sürücü ve dizine sahip.</span><span class="sxs-lookup"><span data-stu-id="c38db-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="c38db-118">[in] Uzaktan hata ayıklama için kullanılmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c38db-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="c38db-119">[in] Uzaktan hata ayıklama için kullanılmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c38db-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="c38db-120">[in] Uzaktan hata ayıklama için kullanılmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c38db-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="c38db-121">[out] İşlemi temsil eden bir "Icordebugprocess arabirimi" nesnesinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c38db-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c38db-122">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c38db-122">Return Value</span></span>  
 <span data-ttu-id="c38db-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="c38db-123">S_OK</span></span>  
 <span data-ttu-id="c38db-124">Hata ayıklama için uzak makineye ve döndürülen bir "Icordebugprocess arabirimi" işlem başarıyla başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="c38db-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="c38db-125">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="c38db-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c38db-126">Uzak makinede işlemi başlatmak ve hata ayıklama için bir "Icordebugprocess arabirimi" dönüş oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="c38db-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c38db-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c38db-127">Remarks</span></span>  
 <span data-ttu-id="c38db-128">Silverlight'ta, karma mod hata ayıklaması desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="c38db-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c38db-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c38db-129">Requirements</span></span>  
 <span data-ttu-id="c38db-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c38db-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c38db-131">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="c38db-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c38db-132">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c38db-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c38db-133">**.NET framework sürümleri:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="c38db-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c38db-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c38db-134">See also</span></span>

- [<span data-ttu-id="c38db-135">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c38db-135">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="c38db-136">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c38db-136">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="c38db-137">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c38db-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
