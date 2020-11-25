---
title: ResetSecurity işlevi (yönetilmeyen API Başvurusu)
description: ResetSecurity işlevi, geçerli iş parçacığına bir kimliğe bürünme belirteci atar.
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 259bef74356f16221f1453dd4086e2fbb26faa83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721120"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="7512f-103">ResetSecurity işlevi</span><span class="sxs-lookup"><span data-stu-id="7512f-103">ResetSecurity function</span></span>

<span data-ttu-id="7512f-104">Sağlanan kimliğe bürünme belirtecini geçerli iş parçacığına atar.</span><span class="sxs-lookup"><span data-stu-id="7512f-104">Assigns the supplied impersonation token to the current thread.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7512f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7512f-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
);
```  

## <a name="parameters"></a><span data-ttu-id="7512f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7512f-106">Parameters</span></span>

`token`  
<span data-ttu-id="7512f-107">'ndaki Geçerli iş parçacığıyla ilişkilendirilecek kimliğe bürünme belirteci.</span><span class="sxs-lookup"><span data-stu-id="7512f-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="7512f-108">Değeri olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="7512f-108">Its value can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="7512f-109">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="7512f-109">Return value</span></span>

<span data-ttu-id="7512f-110">İşlev başarılı olursa, dönüş değeri `S_OK` (0) olur.</span><span class="sxs-lookup"><span data-stu-id="7512f-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="7512f-111">İşlev başarısız olursa, dönüş değeri sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="7512f-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="7512f-112">Genişletilmiş hata bilgilerini almak için [GetErrorInfo](geterrorinfo.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="7512f-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="7512f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7512f-113">Requirements</span></span>  

 <span data-ttu-id="7512f-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7512f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7512f-115">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="7512f-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7512f-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7512f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7512f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7512f-117">See also</span></span>

- [<span data-ttu-id="7512f-118">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7512f-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
