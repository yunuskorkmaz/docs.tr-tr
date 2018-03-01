---
title: "GetCurrentApartmentType işlevi (yönetilmeyen API Başvurusu)"
description: "GetCurrentApartmentType işlevi çağıran yürütülmekte olduğu Grup türünü alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a42c6c3c778dbdefd4b83621e65b81741b940ebe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="e71bb-103">GetCurrentApartmentType işlevi</span><span class="sxs-lookup"><span data-stu-id="e71bb-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="e71bb-104">Arayan yürütülmekte olduğu Grup türünü alır.</span><span class="sxs-lookup"><span data-stu-id="e71bb-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e71bb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e71bb-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="e71bb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e71bb-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e71bb-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e71bb-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e71bb-108">[in] Bir işaretçi bir [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="e71bb-108">[in] A pointer to an [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span></span>

`aptType`  
<span data-ttu-id="e71bb-109">[out] Bir işaretçi bir [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) arayanın Grup belirten numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="e71bb-109">[out] A pointer to an [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="e71bb-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e71bb-110">Return value</span></span>


|<span data-ttu-id="e71bb-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="e71bb-111">Constant</span></span>  |<span data-ttu-id="e71bb-112">Değer</span><span class="sxs-lookup"><span data-stu-id="e71bb-112">Value</span></span>  |<span data-ttu-id="e71bb-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e71bb-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="e71bb-114">0</span><span class="sxs-lookup"><span data-stu-id="e71bb-114">0</span></span> | <span data-ttu-id="e71bb-115">İşlev başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e71bb-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="e71bb-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="e71bb-116">0x80000008</span></span> | <span data-ttu-id="e71bb-117">Çağıran bir grupta yürütülmüyor.</span><span class="sxs-lookup"><span data-stu-id="e71bb-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="e71bb-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e71bb-118">Remarks</span></span>

<span data-ttu-id="e71bb-119">Bu işlev çağrısı sarmalar [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e71bb-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e71bb-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e71bb-120">Requirements</span></span>  
 <span data-ttu-id="e71bb-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e71bb-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e71bb-122">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e71bb-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e71bb-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e71bb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e71bb-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e71bb-124">See also</span></span>  
[<span data-ttu-id="e71bb-125">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e71bb-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
