---
title: "SetSecurity işlevi (yönetilmeyen API Başvurusu)"
description: "SetSecurity işlevi geçerli iş parçacığının kimliğe bürünme belirtecini alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SetSecurity
helpviewer_keywords: SetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abb716d64bde9b298203e54d862ff4f1b2bcd170
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="setsecurity-function"></a><span data-ttu-id="1dacf-103">SetSecurity işlevi</span><span class="sxs-lookup"><span data-stu-id="1dacf-103">SetSecurity function</span></span>
<span data-ttu-id="1dacf-104">Geçerli iş parçacığı ile ilişkili kimliğe bürünme belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="1dacf-104">Retrieves the impersonation token associated with the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1dacf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dacf-105">Syntax</span></span>  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a><span data-ttu-id="1dacf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dacf-106">Parameters</span></span>

<span data-ttu-id="1dacf-107">`pNeedToReset`[out] İşlevi döndüğünde gösteren bir işaretçi içeren bir `boolean` belirten belirteç çağırarak sıfırlayıp sıfırlayamayacağını [ResetSecurity](resetsecurity.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="1dacf-107">`pNeedToReset` [out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>  

`token`  
<span data-ttu-id="1dacf-108">[out] İşlevi döndüğünde, geçerli iş parçacığı ile ilişkili kimliğe bürünme belirtecini işlemek için bir işaretçi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="1dacf-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="1dacf-109">Değerini olabilir `null` geçerli iş parçacığı ile ilişkili herhangi bir belirteci olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="1dacf-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="1dacf-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="1dacf-110">Return value</span></span>

<span data-ttu-id="1dacf-111">İşlev başarılı olursa, dönüş değeri olan `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="1dacf-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="1dacf-112">İşlev başarısız olursa, dönüş değeri sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="1dacf-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="1dacf-113">Genişletilmiş hata bilgilerini için arama [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="1dacf-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="1dacf-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dacf-114">Requirements</span></span>  
 <span data-ttu-id="1dacf-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dacf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dacf-116">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1dacf-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1dacf-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1dacf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dacf-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dacf-118">See also</span></span>  
[<span data-ttu-id="1dacf-119">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1dacf-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
