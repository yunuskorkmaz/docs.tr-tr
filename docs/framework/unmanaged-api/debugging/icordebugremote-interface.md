---
description: ': ICorDebugRemote arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugRemote Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugRemote
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemote
helpviewer_keywords:
- ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type:
- apiref
ms.openlocfilehash: 4c9d92800c68155216a077180ea0b613c67423dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790678"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="dc4b3-103">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc4b3-103">ICorDebugRemote Interface</span></span>

<span data-ttu-id="dc4b3-104">Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc4b3-104">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc4b3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dc4b3-105">Syntax</span></span>  
  
```cpp  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dc4b3-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dc4b3-106">Methods</span></span>  
  
|<span data-ttu-id="dc4b3-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dc4b3-107">Method</span></span>|<span data-ttu-id="dc4b3-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc4b3-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc4b3-109">ICorDebugRemote::CreateProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc4b3-109">ICorDebugRemote::CreateProcessEx Method</span></span>](icordebugremote-createprocessex-method.md)|<span data-ttu-id="dc4b3-110">Yönetilen hata ayıklama için uzak makinede bir işlem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dc4b3-110">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="dc4b3-111">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc4b3-111">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="dc4b3-112">Hata ayıklayıcı altındaki uzak makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="dc4b3-112">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc4b3-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc4b3-113">Remarks</span></span>  

 <span data-ttu-id="dc4b3-114">Şu anda bu işlev yalnızca uzak bir Macintosh makinesinde çalışan Silverlight tabanlı bir uygulama hedefinde hata ayıklama için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dc4b3-114">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc4b3-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc4b3-115">Requirements</span></span>  

 <span data-ttu-id="dc4b3-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc4b3-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc4b3-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dc4b3-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc4b3-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dc4b3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc4b3-119">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="dc4b3-119">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc4b3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc4b3-120">See also</span></span>

- [<span data-ttu-id="dc4b3-121">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc4b3-121">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="dc4b3-122">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc4b3-122">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="dc4b3-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dc4b3-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
