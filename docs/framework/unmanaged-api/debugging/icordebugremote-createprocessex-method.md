---
description: ': ICorDebugRemote:: CreateProcessEx yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cd27400f5c9f348621fb66b3b7730cf15d397151
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794734"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="d19b4-103">ICorDebugRemote::CreateProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d19b4-103">ICorDebugRemote::CreateProcessEx Method</span></span>

<span data-ttu-id="d19b4-104">Hata ayıklayıcı altındaki uzak makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="d19b4-104">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d19b4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d19b4-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d19b4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d19b4-106">Parameters</span></span>  

 `pRemoteTarget`  
 <span data-ttu-id="d19b4-107">'ndaki [ICorDebugRemoteTarget arabirimine](icordebugremotetarget-interface.md)yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d19b4-107">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="d19b4-108">İşlemin başlatılacağı uzak makineyi tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d19b4-108">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="d19b4-109">'ndaki Başlatılan işlem tarafından yürütülecek modülü belirten, null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d19b4-109">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="d19b4-110">Modül, çağıran işlemin güvenlik bağlamında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d19b4-110">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="d19b4-111">'ndaki Başlatılan işlem tarafından yürütülecek komut satırını belirten, null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d19b4-111">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="d19b4-112">'ndaki Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d19b4-112">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="d19b4-113">'ndaki Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d19b4-113">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="d19b4-114">'ndaki Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d19b4-114">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="d19b4-115">'ndaki Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d19b4-115">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="d19b4-116">'ndaki Yeni işlem için ortam bloğunun işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d19b4-116">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="d19b4-117">'ndaki İşlem için geçerli dizinin tam yolunu belirten, null ile sonlandırılmış bir dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d19b4-117">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="d19b4-118">Bu parametre null ise, yeni işlem çağıran işlemle aynı geçerli sürücü ve dizine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="d19b4-118">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="d19b4-119">'ndaki Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d19b4-119">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="d19b4-120">'ndaki Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d19b4-120">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="d19b4-121">'ndaki Uzaktan hata ayıklama için kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d19b4-121">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="d19b4-122">dışı İşlemi temsil eden "ICorDebugProcess Interface" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d19b4-122">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d19b4-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d19b4-123">Return Value</span></span>  

 <span data-ttu-id="d19b4-124">S_OK</span><span class="sxs-lookup"><span data-stu-id="d19b4-124">S_OK</span></span>  
 <span data-ttu-id="d19b4-125">İşlem uzak makinede başarıyla başlatıldı ve hata ayıklama için bir "ICorDebugProcess Interface" döndürdü.</span><span class="sxs-lookup"><span data-stu-id="d19b4-125">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="d19b4-126">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="d19b4-126">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="d19b4-127">Uzak makinede işlem başlatılamıyor ve hata ayıklama için bir "ICorDebugProcess Interface" döndürün.</span><span class="sxs-lookup"><span data-stu-id="d19b4-127">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d19b4-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d19b4-128">Remarks</span></span>  

 <span data-ttu-id="d19b4-129">Karışık modda hata ayıklama Silverlight 'ta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d19b4-129">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d19b4-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d19b4-130">Requirements</span></span>  

 <span data-ttu-id="d19b4-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d19b4-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d19b4-132">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="d19b4-132">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="d19b4-133">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d19b4-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d19b4-134">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="d19b4-134">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d19b4-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d19b4-135">See also</span></span>

- [<span data-ttu-id="d19b4-136">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d19b4-136">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="d19b4-137">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d19b4-137">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="d19b4-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d19b4-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
