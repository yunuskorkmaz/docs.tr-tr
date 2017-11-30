---
title: "Initialize işlevi (yönetilmeyen API Başvurusu)"
description: "Initialize işlevi WMI başlatma gerçekleştirir."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Initialize
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Initialize
helpviewer_keywords: Initialize function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ed0e0127608f9f80a2661067dd9a6025fd579a7
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="initialize-function"></a><span data-ttu-id="452bd-103">Initialize işlevi</span><span class="sxs-lookup"><span data-stu-id="452bd-103">Initialize function</span></span>
<span data-ttu-id="452bd-104">WMI başlatma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="452bd-104">Performs WMI initialization.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="452bd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="452bd-105">Syntax</span></span> 
```  
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
); 
```  
## <a name="parameters"></a><span data-ttu-id="452bd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="452bd-106">Parameters</span></span>

`bAllowIManagementObjectQI`   
<span data-ttu-id="452bd-107">[in] `true` QueryInterface çağrıları WMI nesnelerde izin verildiğini; göstermek için `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="452bd-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="452bd-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="452bd-108">Return value</span></span>

<span data-ttu-id="452bd-109">İşlev her zaman döndürür `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="452bd-109">The function always returns `S_OK` (0).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="452bd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="452bd-110">Requirements</span></span>  
 <span data-ttu-id="452bd-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="452bd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="452bd-112">**Başlık:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="452bd-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="452bd-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="452bd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="452bd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="452bd-114">See also</span></span>  
[<span data-ttu-id="452bd-115">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="452bd-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
