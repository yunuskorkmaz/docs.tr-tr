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
ms.openlocfilehash: b78bff2994cefc6c35a4bd59133338392c3a1b24
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791968"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="b4e8a-102">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b4e8a-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="b4e8a-103">Hata ayıklayıcı altındaki uzak makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="b4e8a-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4e8a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4e8a-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4e8a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4e8a-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="b4e8a-106">'ndaki [ICorDebugRemoteTarget arabirimine](icordebugremotetarget-interface.md)yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b4e8a-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="b4e8a-107">Bu parametre, işlemin üzerinde çalıştığı makineyi tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b4e8a-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="b4e8a-108">'ndaki Hata ayıklayıcının eklendiği işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b4e8a-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="b4e8a-109">[in] hata ayıklayıcının işlem için Win32 hata ayıklayıcısı olarak davranması ve yönetilmeyen geri çağırmaları gönderimi gerekiyorsa `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="b4e8a-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="b4e8a-110">dışı Hata ayıklayıcının eklendiği işlemi temsil eden bir "ICorDebugProcess" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b4e8a-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4e8a-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b4e8a-111">Return Value</span></span>  
 <span data-ttu-id="b4e8a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4e8a-112">S_OK</span></span>  
 <span data-ttu-id="b4e8a-113">Uzak makinedeki işleme başarıyla eklendi.</span><span class="sxs-lookup"><span data-stu-id="b4e8a-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="b4e8a-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="b4e8a-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b4e8a-115">Uzak makinedeki işleme iliştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="b4e8a-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4e8a-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4e8a-116">Remarks</span></span>  
 <span data-ttu-id="b4e8a-117">Karışık modda hata ayıklama Silverlight 'ta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b4e8a-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4e8a-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4e8a-118">Requirements</span></span>  
 <span data-ttu-id="b4e8a-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4e8a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4e8a-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b4e8a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4e8a-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b4e8a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4e8a-122">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="b4e8a-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4e8a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4e8a-123">See also</span></span>

- [<span data-ttu-id="b4e8a-124">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4e8a-124">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="b4e8a-125">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4e8a-125">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="b4e8a-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b4e8a-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
