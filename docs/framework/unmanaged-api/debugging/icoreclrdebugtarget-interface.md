---
title: ICoreClrDebugTarget Arabirimi
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: 791bd2754a96b97a38e2509c0c61a644324857cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716960"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="0b47c-102">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b47c-102">ICoreClrDebugTarget Interface</span></span>

<span data-ttu-id="0b47c-103">Başvuru sayılarını denetleyen, işlem numaralandırmakta olan ve uzak bir Macintosh Silverlight hedefine bağlı bir hata ayıklayıcı ile ilişkili belleği serbest alan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b47c-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b47c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0b47c-104">Syntax</span></span>  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0b47c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0b47c-105">Methods</span></span>  
  
|<span data-ttu-id="0b47c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0b47c-106">Method</span></span>|<span data-ttu-id="0b47c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b47c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b47c-108">ICoreClrDebugTarget::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b47c-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="0b47c-109">Uzak bir bilgisayarda çalışan işlemi numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="0b47c-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="0b47c-110">ICoreClrDebugTarget::EnumRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b47c-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="0b47c-111">Uzak bilgisayardaki belirtilen işlemdeki ortak dil çalışma zamanlarını (CLRs) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="0b47c-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="0b47c-112">ICoreClrDebugTarget::FreeMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b47c-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="0b47c-113">Bu sınıftaki sabit listesi yöntemleriyle ayrılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="0b47c-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b47c-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b47c-114">Remarks</span></span>  

 <span data-ttu-id="0b47c-115">Şu anda bu işlev yalnızca uzak bir Macintosh bilgisayarda çalışan Silverlight tabanlı bir uygulama hedefinde hata ayıklama için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0b47c-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b47c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b47c-116">Requirements</span></span>  

 <span data-ttu-id="0b47c-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b47c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b47c-118">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="0b47c-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="0b47c-119">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="0b47c-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="0b47c-120">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="0b47c-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b47c-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b47c-121">See also</span></span>

- [<span data-ttu-id="0b47c-122">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b47c-122">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="0b47c-123">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b47c-123">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="0b47c-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0b47c-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
