---
title: Initialize işlevi (yönetilmeyen API Başvurusu)
description: Initialize işlevi WMI başlatması gerçekleştirir.
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b1f96b6285911b12d72ac136127d736b75d44023
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127385"
---
# <a name="initialize-function"></a><span data-ttu-id="21eba-103">Initialize işlevi</span><span class="sxs-lookup"><span data-stu-id="21eba-103">Initialize function</span></span>

<span data-ttu-id="21eba-104">WMI başlatması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="21eba-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="21eba-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21eba-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="21eba-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21eba-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="21eba-107">[in] WMI nesnelerinde QueryInterface çağrılarına izin verildiğini belirtmek için `true`; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="21eba-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="21eba-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="21eba-108">Return value</span></span>

<span data-ttu-id="21eba-109">İşlev her zaman `S_OK` (0) döndürür.</span><span class="sxs-lookup"><span data-stu-id="21eba-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="21eba-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21eba-110">Requirements</span></span>

<span data-ttu-id="21eba-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21eba-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="21eba-112">**Üst bilgi:** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="21eba-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="21eba-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="21eba-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="21eba-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21eba-114">See also</span></span>

- [<span data-ttu-id="21eba-115">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="21eba-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
