---
title: ResetSecurity işlevi (Yönetilmeyen API Başvurusu)
description: ResetSecurity işlevi geçerli iş parçacığına bir kimliğe bürünme belirteci atar.
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
ms.openlocfilehash: ce74494455c6cc7fe382a4ea4ef2ff0c4e98c61b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174868"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="92311-103">ResetSecurity işlevi</span><span class="sxs-lookup"><span data-stu-id="92311-103">ResetSecurity function</span></span>
<span data-ttu-id="92311-104">Verilen kimliğe bürünme belirteci belirteci geçerli iş parçacığına atar.</span><span class="sxs-lookup"><span data-stu-id="92311-104">Assigns the supplied impersonation token to the current thread.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="92311-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92311-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
);
```  

## <a name="parameters"></a><span data-ttu-id="92311-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92311-106">Parameters</span></span>

`token`  
<span data-ttu-id="92311-107">[içinde] Geçerli iş parçacığı ile ilişkilendirmek için kimliğe bürünme belirteci.</span><span class="sxs-lookup"><span data-stu-id="92311-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="92311-108">Değeri olabilir. `null`</span><span class="sxs-lookup"><span data-stu-id="92311-108">Its value can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="92311-109">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="92311-109">Return value</span></span>

<span data-ttu-id="92311-110">İşlev başarılı olursa, iade `S_OK` değeri (0) olur.</span><span class="sxs-lookup"><span data-stu-id="92311-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="92311-111">İşlev başarısız olursa, iade değeri sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="92311-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="92311-112">Genişletilmiş hata bilgilerini almak için [GetErrorInfo](geterrorinfo.md) işlevini arayın.</span><span class="sxs-lookup"><span data-stu-id="92311-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="92311-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92311-113">Requirements</span></span>  
 <span data-ttu-id="92311-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92311-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92311-115">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="92311-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="92311-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="92311-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92311-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92311-117">See also</span></span>

- [<span data-ttu-id="92311-118">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="92311-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
