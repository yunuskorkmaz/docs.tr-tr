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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bc3688b30180bdcde0a87027955a789de749f90
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798434"
---
# <a name="initialize-function"></a><span data-ttu-id="abdc3-103">Initialize işlevi</span><span class="sxs-lookup"><span data-stu-id="abdc3-103">Initialize function</span></span>

<span data-ttu-id="abdc3-104">WMI başlatması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="abdc3-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="abdc3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abdc3-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="abdc3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="abdc3-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="abdc3-107">'ndaki `true` WMI nesnelerinde QueryInterface çağrılarına izin verildiğini belirtmek için; `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="abdc3-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="abdc3-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="abdc3-108">Return value</span></span>

<span data-ttu-id="abdc3-109">İşlev her zaman ( `S_OK` 0) döndürür.</span><span class="sxs-lookup"><span data-stu-id="abdc3-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="abdc3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abdc3-110">Requirements</span></span>

<span data-ttu-id="abdc3-111">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abdc3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="abdc3-112">**Üst bilgi** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="abdc3-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="abdc3-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="abdc3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="abdc3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abdc3-114">See also</span></span>

- [<span data-ttu-id="abdc3-115">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="abdc3-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
