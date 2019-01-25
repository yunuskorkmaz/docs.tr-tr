---
title: SetSecurity işlevi (yönetilmeyen API Başvurusu)
description: SetSecurity işlevi, geçerli iş parçacığının kimliğe bürünme belirtecini alır.
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b3e8ddb34849611daae4dfa1d2762a25ac5cf82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721151"
---
# <a name="setsecurity-function"></a><span data-ttu-id="a7f2a-103">SetSecurity işlevi</span><span class="sxs-lookup"><span data-stu-id="a7f2a-103">SetSecurity function</span></span>
<span data-ttu-id="a7f2a-104">Geçerli iş parçacığıyla ilişkilendirilmiş kimliğe bürünme belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="a7f2a-104">Retrieves the impersonation token associated with the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a7f2a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7f2a-105">Syntax</span></span>  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a><span data-ttu-id="a7f2a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7f2a-106">Parameters</span></span>

<span data-ttu-id="a7f2a-107">`pNeedToReset` [out] İşlevi döndüğünde, bir işaretçi içeren bir `boolean` belirten belirteç çağırarak sıfırlama olmadığını [ResetSecurity](resetsecurity.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="a7f2a-107">`pNeedToReset` [out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>  

`token`  
<span data-ttu-id="a7f2a-108">[out] İşlevi döndüğünde, geçerli iş parçacığıyla ilişkilendirilmiş kimliğe bürünme belirtecini işlemek için bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="a7f2a-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="a7f2a-109">Değeri olabilir `null` geçerli iş parçacığıyla ilişkilendirilmiş hiçbir belirteç olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="a7f2a-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="a7f2a-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="a7f2a-110">Return value</span></span>

<span data-ttu-id="a7f2a-111">İşlev başarılı olursa, dönüş değeri olduğu `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="a7f2a-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="a7f2a-112">İşlev başarısız olursa, dönüş değeri sıfır olmayan hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="a7f2a-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="a7f2a-113">Genişletilmiş hata bilgilerini almak için arama [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="a7f2a-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="a7f2a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7f2a-114">Requirements</span></span>  
 <span data-ttu-id="a7f2a-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7f2a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7f2a-116">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a7f2a-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a7f2a-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a7f2a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f2a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7f2a-118">See also</span></span>
- [<span data-ttu-id="a7f2a-119">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a7f2a-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
