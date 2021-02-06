---
description: ': ICorConfiguration:: AddDebuggerSpecialThread yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b6904c2e4d5c265244ac096e0d64c2fc7f5d1be5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636721"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="5f664-103">ICorConfiguration::AddDebuggerSpecialThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f664-103">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>

<span data-ttu-id="5f664-104">Hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryolarında durdurulan bir uygulamaya sahip olsa da, belirli bir iş parçacığının yürütmeye devam etmesine izin verilmesi gerektiğini hata ayıklama hizmetlerine bildirir.</span><span class="sxs-lookup"><span data-stu-id="5f664-104">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f664-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f664-105">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f664-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5f664-106">Parameters</span></span>  

 `dwSpecialThreadId`  
 <span data-ttu-id="5f664-107">'ndaki Yürütülmeye devam etmesi için izin verilmesi gereken iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="5f664-107">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f664-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f664-108">Remarks</span></span>  

 <span data-ttu-id="5f664-109">Belirtilen iş parçacığının yönetilen kodu çalıştırmasına izin verilmez veya çalışma zamanını herhangi bir şekilde giremeyecektir.</span><span class="sxs-lookup"><span data-stu-id="5f664-109">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="5f664-110">Bu tür bir iş parçacığına bir örnek, eski betik hata ayıklayıcılarını desteklemek için işlem içi bir iş parçacığı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5f664-110">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f664-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f664-111">Requirements</span></span>  

 <span data-ttu-id="5f664-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f664-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f664-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5f664-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f664-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5f664-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f664-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f664-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f664-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f664-116">See also</span></span>

- [<span data-ttu-id="5f664-117">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f664-117">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
