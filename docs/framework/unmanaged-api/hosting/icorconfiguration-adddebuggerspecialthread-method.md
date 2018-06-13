---
title: ICorConfiguration::AddDebuggerSpecialThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59b940c0dbe9462dda513e933b7360ff55a9b447
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437355"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="f1f0b-102">ICorConfiguration::AddDebuggerSpecialThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1f0b-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="f1f0b-103">Hata Ayıklama Hizmetleri belirli bir iş parçacığı hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryoları sırasında durdurulmuş bir uygulama sahipken çalıştırmaya devam etmeyi izin verilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1f0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1f0b-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1f0b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1f0b-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="f1f0b-106">[in] Yürütülmeye devam izin verilmesi gereken iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1f0b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1f0b-107">Remarks</span></span>  
 <span data-ttu-id="f1f0b-108">Belirtilen iş parçacığı yönetilen kod çalıştırma veya herhangi bir şekilde çalışma zamanı girmek için izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="f1f0b-109">Bu tür, bir iş parçacığı örneği eski komut dosyası hata ayıklayıcıları desteklemek için bir işlem iş parçacığı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1f0b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1f0b-110">Requirements</span></span>  
 <span data-ttu-id="f1f0b-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1f0b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1f0b-112">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f1f0b-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1f0b-113">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f1f0b-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1f0b-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1f0b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f0b-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1f0b-115">See Also</span></span>  
 [<span data-ttu-id="f1f0b-116">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1f0b-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
