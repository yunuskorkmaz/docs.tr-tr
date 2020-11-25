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
ms.openlocfilehash: bd89db3fa0b1814a98b016fcf9d1aeeabfff718b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715855"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="4fe50-102">ICorConfiguration::AddDebuggerSpecialThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4fe50-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>

<span data-ttu-id="4fe50-103">Hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryolarında durdurulan bir uygulamaya sahip olsa da, belirli bir iş parçacığının yürütmeye devam etmesine izin verilmesi gerektiğini hata ayıklama hizmetlerine bildirir.</span><span class="sxs-lookup"><span data-stu-id="4fe50-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe50-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4fe50-104">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fe50-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4fe50-105">Parameters</span></span>  

 `dwSpecialThreadId`  
 <span data-ttu-id="4fe50-106">'ndaki Yürütülmeye devam etmesi için izin verilmesi gereken iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4fe50-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fe50-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fe50-107">Remarks</span></span>  

 <span data-ttu-id="4fe50-108">Belirtilen iş parçacığının yönetilen kodu çalıştırmasına izin verilmez veya çalışma zamanını herhangi bir şekilde giremeyecektir.</span><span class="sxs-lookup"><span data-stu-id="4fe50-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="4fe50-109">Bu tür bir iş parçacığına bir örnek, eski betik hata ayıklayıcılarını desteklemek için işlem içi bir iş parçacığı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4fe50-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fe50-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4fe50-110">Requirements</span></span>  

 <span data-ttu-id="4fe50-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fe50-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fe50-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4fe50-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4fe50-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4fe50-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fe50-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fe50-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe50-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fe50-115">See also</span></span>

- [<span data-ttu-id="4fe50-116">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4fe50-116">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
