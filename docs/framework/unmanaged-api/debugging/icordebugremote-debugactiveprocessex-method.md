---
description: ': ICorDebugRemote::D ebugActiveProcessEx yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ccbde152e59146bd852a5a0a2f991d10333fa9d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717907"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="9820c-103">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9820c-103">ICorDebugRemote::DebugActiveProcessEx Method</span></span>

<span data-ttu-id="9820c-104">Hata ayıklayıcı altındaki uzak makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="9820c-104">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9820c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9820c-105">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9820c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9820c-106">Parameters</span></span>  

 `pRemoteTarget`  
 <span data-ttu-id="9820c-107">'ndaki [ICorDebugRemoteTarget arabirimine](icordebugremotetarget-interface.md)yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9820c-107">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="9820c-108">Bu parametre, işlemin üzerinde çalıştığı makineyi tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9820c-108">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="9820c-109">'ndaki Hata ayıklayıcının eklendiği işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9820c-109">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="9820c-110">[in] `true` hata ayıklayıcının işlem için Win32 hata ayıklayıcısı olarak davranması ve yönetilmeyen geri çağırmaları dağıtımı gerekiyorsa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="9820c-110">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="9820c-111">dışı Hata ayıklayıcının eklendiği işlemi temsil eden bir "ICorDebugProcess" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9820c-111">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9820c-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9820c-112">Return Value</span></span>  

 <span data-ttu-id="9820c-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9820c-113">S_OK</span></span>  
 <span data-ttu-id="9820c-114">Uzak makinedeki işleme başarıyla eklendi.</span><span class="sxs-lookup"><span data-stu-id="9820c-114">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="9820c-115">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="9820c-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="9820c-116">Uzak makinedeki işleme iliştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="9820c-116">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9820c-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9820c-117">Remarks</span></span>  

 <span data-ttu-id="9820c-118">Karışık modda hata ayıklama Silverlight 'ta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9820c-118">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9820c-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9820c-119">Requirements</span></span>  

 <span data-ttu-id="9820c-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9820c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9820c-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9820c-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9820c-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9820c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9820c-123">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="9820c-123">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9820c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9820c-124">See also</span></span>

- [<span data-ttu-id="9820c-125">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9820c-125">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="9820c-126">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9820c-126">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="9820c-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9820c-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
