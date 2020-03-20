---
title: SetSecurity işlevi (Yönetilmeyen API Başvurusu)
description: SetSecurity işlevi geçerli iş parçacığının kimliğe bürünme belirteci alır.
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
ms.openlocfilehash: 809f6a95fdd6854b3a591b496877838c48d52199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176740"
---
# <a name="setsecurity-function"></a><span data-ttu-id="b914e-103">SetSecurity işlevi</span><span class="sxs-lookup"><span data-stu-id="b914e-103">SetSecurity function</span></span>

<span data-ttu-id="b914e-104">Geçerli iş parçacığı ile ilişkili kimliğe bürünme belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="b914e-104">Retrieves the impersonation token associated with the current thread.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="b914e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b914e-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset,
   [out] HANDLE* pCurrentThreadToken
);
```

## <a name="parameters"></a><span data-ttu-id="b914e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b914e-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="b914e-107">[çıkış] İşlev döndüğünde, [ResetSecurity](resetsecurity.md) `boolean` işlevini çağırarak belirteç sıfırlanıp sıfırlanmayacağını belirten bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="b914e-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="b914e-108">[çıkış] İşlev döndüğünde, geçerli iş parçacığı ile ilişkili kimliğe bürünme belirteci işparçacığı için bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="b914e-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="b914e-109">Geçerli iş `null` parçacığı ile ilişkili bir belirteç varsa değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="b914e-109">Its value can be `null` if there is no token associated with the current thread.</span></span>

## <a name="return-value"></a><span data-ttu-id="b914e-110">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="b914e-110">Return value</span></span>

<span data-ttu-id="b914e-111">İşlev başarılı olursa, iade `S_OK` değeri (0) olur.</span><span class="sxs-lookup"><span data-stu-id="b914e-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="b914e-112">İşlev başarısız olursa, iade değeri sıfır olmayan bir hata kodudur.</span><span class="sxs-lookup"><span data-stu-id="b914e-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="b914e-113">Genişletilmiş hata bilgilerini almak için [GetErrorInfo](geterrorinfo.md) işlevini arayın.</span><span class="sxs-lookup"><span data-stu-id="b914e-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="b914e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b914e-114">Requirements</span></span>

 <span data-ttu-id="b914e-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b914e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="b914e-116">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b914e-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="b914e-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b914e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b914e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b914e-118">See also</span></span>

- [<span data-ttu-id="b914e-119">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b914e-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
