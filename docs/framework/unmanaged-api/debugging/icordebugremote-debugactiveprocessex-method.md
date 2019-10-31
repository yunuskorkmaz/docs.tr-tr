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
ms.openlocfilehash: 83cc4eadca7c337c06c5fbf9f0e74306c2b9cb99
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131280"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="0796b-102">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0796b-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="0796b-103">Hata ayıklayıcı altındaki uzak makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="0796b-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0796b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0796b-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0796b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0796b-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="0796b-106">'ndaki [ICorDebugRemoteTarget arabirimine](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0796b-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="0796b-107">Bu parametre, işlemin üzerinde çalıştığı makineyi tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0796b-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="0796b-108">'ndaki Hata ayıklayıcının eklendiği işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0796b-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="0796b-109">[in] hata ayıklayıcının işlem için Win32 hata ayıklayıcısı olarak davranması ve yönetilmeyen geri çağırmaları gönderimi gerekiyorsa `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="0796b-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="0796b-110">dışı Hata ayıklayıcının eklendiği işlemi temsil eden bir "ICorDebugProcess" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0796b-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0796b-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0796b-111">Return Value</span></span>  
 <span data-ttu-id="0796b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0796b-112">S_OK</span></span>  
 <span data-ttu-id="0796b-113">Uzak makinedeki işleme başarıyla eklendi.</span><span class="sxs-lookup"><span data-stu-id="0796b-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="0796b-114">E_FAıL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="0796b-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="0796b-115">Uzak makinedeki işleme iliştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="0796b-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0796b-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0796b-116">Remarks</span></span>  
 <span data-ttu-id="0796b-117">Karışık modda hata ayıklama Silverlight 'ta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0796b-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0796b-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0796b-118">Requirements</span></span>  
 <span data-ttu-id="0796b-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0796b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0796b-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0796b-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0796b-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0796b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0796b-122">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="0796b-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0796b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0796b-123">See also</span></span>

- [<span data-ttu-id="0796b-124">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0796b-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="0796b-125">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0796b-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="0796b-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0796b-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
