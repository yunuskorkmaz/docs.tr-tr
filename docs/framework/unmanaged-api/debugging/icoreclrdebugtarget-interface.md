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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 371768a8306c3751e7fc54b91a8583df41ad219b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422288"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="81d63-102">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81d63-102">ICoreClrDebugTarget Interface</span></span>
<span data-ttu-id="81d63-103">Başvuru sayıları denetlemek, işlemleri numaralandıran ve bir uzak Macintosh Silverlight hedefe bağlı bir hata ayıklayıcısı ile ilişkili belleği serbest yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="81d63-103">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81d63-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81d63-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="81d63-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="81d63-105">Methods</span></span>  
  
|<span data-ttu-id="81d63-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="81d63-106">Method</span></span>|<span data-ttu-id="81d63-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81d63-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81d63-108">ICoreClrDebugTarget::EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="81d63-108">ICoreClrDebugTarget::EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="81d63-109">Bir uzak bilgisayarda çalışan işlemler numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="81d63-109">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="81d63-110">ICoreClrDebugTarget::EnumRuntimes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="81d63-110">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="81d63-111">Ortak dil çalışma zamanları (CLRs), uzak bir bilgisayarda belirtilen işlemde numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="81d63-111">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="81d63-112">ICoreClrDebugTarget::FreeMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="81d63-112">ICoreClrDebugTarget::FreeMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="81d63-113">Bu sınıf numaralandırma yöntemleri tarafından ayrılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="81d63-113">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81d63-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81d63-114">Remarks</span></span>  
 <span data-ttu-id="81d63-115">Şu anda bu işlevsellik yalnızca bir uzak Macintosh bilgisayarda çalışan Silverlight tabanlı uygulamaya hedef hata ayıklama için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="81d63-115">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81d63-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81d63-116">Requirements</span></span>  
 <span data-ttu-id="81d63-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81d63-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81d63-118">**Başlık:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="81d63-118">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="81d63-119">**Kitaplığı:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="81d63-119">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="81d63-120">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="81d63-120">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d63-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81d63-121">See Also</span></span>  
 [<span data-ttu-id="81d63-122">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81d63-122">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="81d63-123">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="81d63-123">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="81d63-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="81d63-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
