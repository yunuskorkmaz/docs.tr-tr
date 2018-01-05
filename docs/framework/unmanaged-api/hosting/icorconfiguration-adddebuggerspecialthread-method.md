---
title: "ICorConfiguration::AddDebuggerSpecialThread Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.AddDebuggerSpecialThread
api_location: mscoree.dll
api_type: COM
f1_keywords: AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2041a45cb80a08b2322f23e820f89b4bb71f845
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="2448a-102">ICorConfiguration::AddDebuggerSpecialThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2448a-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="2448a-103">Hata Ayıklama Hizmetleri belirli bir iş parçacığı hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryoları sırasında durdurulmuş bir uygulama sahipken çalıştırmaya devam etmeyi izin verilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2448a-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2448a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2448a-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2448a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2448a-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="2448a-106">[in] Yürütülmeye devam izin verilmesi gereken iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="2448a-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2448a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2448a-107">Remarks</span></span>  
 <span data-ttu-id="2448a-108">Belirtilen iş parçacığı yönetilen kod çalıştırma veya herhangi bir şekilde çalışma zamanı girmek için izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="2448a-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="2448a-109">Bu tür, bir iş parçacığı örneği eski komut dosyası hata ayıklayıcıları desteklemek için bir işlem iş parçacığı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2448a-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2448a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2448a-110">Requirements</span></span>  
 <span data-ttu-id="2448a-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2448a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2448a-112">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2448a-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2448a-113">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2448a-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2448a-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2448a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2448a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2448a-115">See Also</span></span>  
 [<span data-ttu-id="2448a-116">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2448a-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
