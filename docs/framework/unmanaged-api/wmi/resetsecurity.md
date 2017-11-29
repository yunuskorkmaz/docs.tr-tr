---
title: "ResetSecurity işlevi (yönetilmeyen API Başvurusu)"
description: "ResetSecurity işlevi, geçerli iş parçacığına kimliğe bürünme simgesi atar."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ResetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ResetSecurity
helpviewer_keywords: ResetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2790012a429c6a0551d8321a80570f3f8be2142b
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="resetsecurity-function"></a><span data-ttu-id="b29b2-103">ResetSecurity işlevi</span><span class="sxs-lookup"><span data-stu-id="b29b2-103">ResetSecurity function</span></span>
<span data-ttu-id="b29b2-104">Sağlanan kimliğe bürünme belirteci geçerli iş parçacığına atar.</span><span class="sxs-lookup"><span data-stu-id="b29b2-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b29b2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b29b2-105">Syntax</span></span>  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="b29b2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b29b2-106">Parameters</span></span>

`token`  
<span data-ttu-id="b29b2-107">[in] Geçerli iş parçacığı ile ilişkilendirmek için kimliğe bürünme belirteci.</span><span class="sxs-lookup"><span data-stu-id="b29b2-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="b29b2-108">Değerini olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="b29b2-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="b29b2-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b29b2-109">Return value</span></span>

<span data-ttu-id="b29b2-110">İşlev başarılı olursa, dönüş değeri olan `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="b29b2-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="b29b2-111">İşlev başarısız olursa, dönüş değeri sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="b29b2-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="b29b2-112">Genişletilmiş hata bilgilerini için arama [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="b29b2-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="b29b2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b29b2-113">Requirements</span></span>  
 <span data-ttu-id="b29b2-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b29b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b29b2-115">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b29b2-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b29b2-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b29b2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b29b2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b29b2-117">See also</span></span>  
[<span data-ttu-id="b29b2-118">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b29b2-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
