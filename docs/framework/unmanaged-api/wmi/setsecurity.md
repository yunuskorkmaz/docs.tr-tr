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
ms.openlocfilehash: 94c76213acb66116105d181e9961a33976047ee7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798243"
---
# <a name="setsecurity-function"></a><span data-ttu-id="e642e-103">SetSecurity işlevi</span><span class="sxs-lookup"><span data-stu-id="e642e-103">SetSecurity function</span></span>

<span data-ttu-id="e642e-104">Geçerli iş parçacığıyla ilişkili kimliğe bürünme belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="e642e-104">Retrieves the impersonation token associated with the current thread.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e642e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e642e-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a><span data-ttu-id="e642e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e642e-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="e642e-107">dışı İşlev döndürüldüğünde, belirtecin [resetsecurity](resetsecurity.md) işlevini çağırarak sıfırlanmasının `boolean` gerekip gerekmediğini belirten bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="e642e-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="e642e-108">dışı İşlev döndürüldüğünde, geçerli iş parçacığıyla ilişkili kimliğe bürünme belirtecinin tanıtıcısına yönelik bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="e642e-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="e642e-109">Geçerli iş parçacığıyla ilişkili `null` bir belirteç yoksa değeri bu olabilir.</span><span class="sxs-lookup"><span data-stu-id="e642e-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="e642e-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e642e-110">Return value</span></span>

<span data-ttu-id="e642e-111">İşlev başarılı olursa, dönüş değeri (0) `S_OK` olur.</span><span class="sxs-lookup"><span data-stu-id="e642e-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="e642e-112">İşlev başarısız olursa, dönüş değeri sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="e642e-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="e642e-113">Genişletilmiş hata bilgilerini almak için [GetErrorInfo](geterrorinfo.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="e642e-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="e642e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e642e-114">Requirements</span></span>

 <span data-ttu-id="e642e-115">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e642e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="e642e-116">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="e642e-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="e642e-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e642e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e642e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e642e-118">See also</span></span>

- [<span data-ttu-id="e642e-119">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e642e-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
