---
description: 'Şu konuda daha fazla bilgi edinin: ICoreClrDebugTarget arabirimi'
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
ms.openlocfilehash: f0ed4dd75cd1daca6e83617433b29bbaecb1dd36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728762"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="c596b-103">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c596b-103">ICoreClrDebugTarget Interface</span></span>

<span data-ttu-id="c596b-104">Başvuru sayılarını denetleyen, işlem numaralandırmakta olan ve uzak bir Macintosh Silverlight hedefine bağlı bir hata ayıklayıcı ile ilişkili belleği serbest alan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c596b-104">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c596b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c596b-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="c596b-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c596b-106">Methods</span></span>  
  
|<span data-ttu-id="c596b-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c596b-107">Method</span></span>|<span data-ttu-id="c596b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c596b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c596b-109">ICoreClrDebugTarget::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c596b-109">ICoreClrDebugTarget::EnumProcesses Method</span></span>](icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="c596b-110">Uzak bir bilgisayarda çalışan işlemi numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="c596b-110">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="c596b-111">ICoreClrDebugTarget::EnumRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c596b-111">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="c596b-112">Uzak bilgisayardaki belirtilen işlemdeki ortak dil çalışma zamanlarını (CLRs) numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="c596b-112">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="c596b-113">ICoreClrDebugTarget::FreeMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c596b-113">ICoreClrDebugTarget::FreeMemory Method</span></span>](icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="c596b-114">Bu sınıftaki sabit listesi yöntemleriyle ayrılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="c596b-114">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c596b-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c596b-115">Remarks</span></span>  

 <span data-ttu-id="c596b-116">Şu anda bu işlev yalnızca uzak bir Macintosh bilgisayarda çalışan Silverlight tabanlı bir uygulama hedefinde hata ayıklama için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c596b-116">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c596b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c596b-117">Requirements</span></span>  

 <span data-ttu-id="c596b-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c596b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c596b-119">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="c596b-119">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="c596b-120">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="c596b-120">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="c596b-121">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c596b-121">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c596b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c596b-122">See also</span></span>

- [<span data-ttu-id="c596b-123">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c596b-123">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="c596b-124">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c596b-124">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="c596b-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c596b-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
