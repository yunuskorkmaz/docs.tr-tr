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
ms.openlocfilehash: b95e9f3a0d584511a2bcf156ed2c50a98f96d071
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379058"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="c5a1d-102">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5a1d-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="c5a1d-103">Hata ayıklayıcı altındaki uzak makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5a1d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5a1d-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5a1d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5a1d-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="c5a1d-106">'ndaki [ICorDebugRemoteTarget arabirimine](icordebugremotetarget-interface.md)yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="c5a1d-107">Bu parametre, işlemin üzerinde çalıştığı makineyi tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="c5a1d-108">'ndaki Hata ayıklayıcının eklendiği işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="c5a1d-109">[in] `true` hata ayıklayıcının işlem için Win32 hata ayıklayıcısı olarak davranması ve yönetilmeyen geri çağırmaları dağıtımı gerekiyorsa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="c5a1d-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="c5a1d-110">dışı Hata ayıklayıcının eklendiği işlemi temsil eden bir "ICorDebugProcess" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5a1d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c5a1d-111">Return Value</span></span>  
 <span data-ttu-id="c5a1d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5a1d-112">S_OK</span></span>  
 <span data-ttu-id="c5a1d-113">Uzak makinedeki işleme başarıyla eklendi.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="c5a1d-114">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="c5a1d-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c5a1d-115">Uzak makinedeki işleme iliştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5a1d-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5a1d-116">Remarks</span></span>  
 <span data-ttu-id="c5a1d-117">Karışık modda hata ayıklama Silverlight 'ta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5a1d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5a1d-118">Requirements</span></span>  
 <span data-ttu-id="c5a1d-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5a1d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5a1d-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c5a1d-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5a1d-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c5a1d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5a1d-122">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c5a1d-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a1d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5a1d-123">See also</span></span>

- [<span data-ttu-id="c5a1d-124">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5a1d-124">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="c5a1d-125">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5a1d-125">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="c5a1d-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c5a1d-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
