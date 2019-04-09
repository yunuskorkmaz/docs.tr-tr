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
ms.openlocfilehash: ca8e87157a7adf45f35608aeba1067f2d66c8972
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081612"
---
# <a name="initialize-function"></a><span data-ttu-id="924e5-103">Initialize işlevi</span><span class="sxs-lookup"><span data-stu-id="924e5-103">Initialize function</span></span>
<span data-ttu-id="924e5-104">WMI başlatma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="924e5-104">Performs WMI initialization.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="924e5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="924e5-105">Syntax</span></span> 
```  
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
); 
```  
## <a name="parameters"></a><span data-ttu-id="924e5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="924e5-106">Parameters</span></span>

`bAllowIManagementObjectQI`   
<span data-ttu-id="924e5-107">[in] `true` QueryInterface çağrıları WMI nesnelerde izin verildiğini; göstermek için `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="924e5-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="924e5-108">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="924e5-108">Return value</span></span>

<span data-ttu-id="924e5-109">İşlev her zaman döndürür `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="924e5-109">The function always returns `S_OK` (0).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="924e5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="924e5-110">Requirements</span></span>  
 <span data-ttu-id="924e5-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="924e5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="924e5-112">**Üst bilgi:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="924e5-112">**Header:** WMINet_Utils.def</span></span>  
  
 **<span data-ttu-id="924e5-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="924e5-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="924e5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="924e5-114">See also</span></span>

- [<span data-ttu-id="924e5-115">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="924e5-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
