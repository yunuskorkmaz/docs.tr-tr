---
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
ms.openlocfilehash: ef11aa48f679592126f736c2877c697f02cb5e62
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379243"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="b1711-102">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1711-102">ICorDebugRemote Interface</span></span>
<span data-ttu-id="b1711-103">Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1711-103">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1711-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1711-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b1711-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b1711-105">Methods</span></span>  
  
|<span data-ttu-id="b1711-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b1711-106">Method</span></span>|<span data-ttu-id="b1711-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1711-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1711-108">ICorDebugRemote::CreateProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1711-108">ICorDebugRemote::CreateProcessEx Method</span></span>](icordebugremote-createprocessex-method.md)|<span data-ttu-id="b1711-109">Yönetilen hata ayıklama için uzak makinede bir işlem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1711-109">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="b1711-110">ICorDebugRemote::DebugActiveProcessEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1711-110">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="b1711-111">Hata ayıklayıcı altındaki uzak makinede bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="b1711-111">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1711-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1711-112">Remarks</span></span>  
 <span data-ttu-id="b1711-113">Şu anda bu işlev yalnızca uzak bir Macintosh makinesinde çalışan Silverlight tabanlı bir uygulama hedefinde hata ayıklama için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b1711-113">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1711-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1711-114">Requirements</span></span>  
 <span data-ttu-id="b1711-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1711-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1711-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b1711-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1711-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b1711-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1711-118">**.NET Framework sürümleri:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="b1711-118">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1711-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1711-119">See also</span></span>

- [<span data-ttu-id="b1711-120">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1711-120">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="b1711-121">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1711-121">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="b1711-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b1711-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
