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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e937690c184d810549e8ab11ef1fc2273a45c5f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049251"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="28bb1-103">ResetSecurity işlevi</span><span class="sxs-lookup"><span data-stu-id="28bb1-103">ResetSecurity function</span></span>
<span data-ttu-id="28bb1-104">Sağlanan kimliğe bürünme belirteci için geçerli iş parçacığı atar.</span><span class="sxs-lookup"><span data-stu-id="28bb1-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="28bb1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28bb1-105">Syntax</span></span>  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="28bb1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28bb1-106">Parameters</span></span>

`token`  
<span data-ttu-id="28bb1-107">[in] Geçerli iş parçacığı ile ilişkilendirmek için kimliğe bürünme belirteci.</span><span class="sxs-lookup"><span data-stu-id="28bb1-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="28bb1-108">Değeri olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="28bb1-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="28bb1-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="28bb1-109">Return value</span></span>

<span data-ttu-id="28bb1-110">İşlev başarılı olursa, dönüş değeri olduğu `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="28bb1-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="28bb1-111">İşlev başarısız olursa, dönüş değeri sıfır olmayan hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="28bb1-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="28bb1-112">Genişletilmiş hata bilgilerini almak için arama [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="28bb1-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="28bb1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28bb1-113">Requirements</span></span>  
 <span data-ttu-id="28bb1-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28bb1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28bb1-115">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="28bb1-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="28bb1-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="28bb1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28bb1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28bb1-117">See also</span></span>

- [<span data-ttu-id="28bb1-118">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="28bb1-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
