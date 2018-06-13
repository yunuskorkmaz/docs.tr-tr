---
title: ResetSecurity işlevi (yönetilmeyen API Başvurusu)
description: ResetSecurity işlevi, geçerli iş parçacığına kimliğe bürünme simgesi atar.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31e42b9e39ddb43025e18888572c394d742e38cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457912"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="32919-103">ResetSecurity işlevi</span><span class="sxs-lookup"><span data-stu-id="32919-103">ResetSecurity function</span></span>
<span data-ttu-id="32919-104">Sağlanan kimliğe bürünme belirteci geçerli iş parçacığına atar.</span><span class="sxs-lookup"><span data-stu-id="32919-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="32919-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32919-105">Syntax</span></span>  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="32919-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32919-106">Parameters</span></span>

`token`  
<span data-ttu-id="32919-107">[in] Geçerli iş parçacığı ile ilişkilendirmek için kimliğe bürünme belirteci.</span><span class="sxs-lookup"><span data-stu-id="32919-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="32919-108">Değerini olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="32919-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="32919-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="32919-109">Return value</span></span>

<span data-ttu-id="32919-110">İşlev başarılı olursa, dönüş değeri olan `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="32919-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="32919-111">İşlev başarısız olursa, dönüş değeri sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="32919-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="32919-112">Genişletilmiş hata bilgilerini için arama [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="32919-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="32919-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32919-113">Requirements</span></span>  
 <span data-ttu-id="32919-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32919-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32919-115">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="32919-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="32919-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="32919-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32919-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32919-117">See also</span></span>  
[<span data-ttu-id="32919-118">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="32919-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
