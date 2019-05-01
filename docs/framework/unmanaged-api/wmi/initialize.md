---
title: Initialize işlevi (yönetilmeyen API Başvurusu)
description: Başlatma işlevinin WMI başlatma gerçekleştirir.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c71b2b6d6f102d19d30d480ee9bafcac3c204be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049303"
---
# <a name="initialize-function"></a><span data-ttu-id="435b8-103">Initialize işlevi</span><span class="sxs-lookup"><span data-stu-id="435b8-103">Initialize function</span></span>

<span data-ttu-id="435b8-104">WMI başlatma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="435b8-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="435b8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="435b8-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="435b8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="435b8-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="435b8-107">[in] `true` QueryInterface çağrıları WMI nesnelerde izin verildiğini; göstermek için `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="435b8-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="435b8-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="435b8-108">Return value</span></span>

<span data-ttu-id="435b8-109">İşlev her zaman döndürür `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="435b8-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="435b8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="435b8-110">Requirements</span></span>

<span data-ttu-id="435b8-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="435b8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="435b8-112">**Üst bilgi:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="435b8-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="435b8-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="435b8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="435b8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="435b8-114">See also</span></span>

- [<span data-ttu-id="435b8-115">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="435b8-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
