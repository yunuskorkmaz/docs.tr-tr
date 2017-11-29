---
title: "GetCurrentApartmentType işlevi (yönetilmeyen API Başvurusu)"
description: "GetCurrentApartmentType işlevi çağıran yürütülmekte olduğu Grup türünü alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetCurrentApartmentType
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetCurrentApartmentType
helpviewer_keywords: GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b250913b55ba59261a666760cc15466b6f9d096e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="e6074-103">GetCurrentApartmentType işlevi</span><span class="sxs-lookup"><span data-stu-id="e6074-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="e6074-104">Arayan yürütülmekte olduğu Grup türünü alır.</span><span class="sxs-lookup"><span data-stu-id="e6074-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e6074-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6074-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="e6074-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6074-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e6074-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e6074-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e6074-108">[in] Bir işaretçi bir [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="e6074-108">[in] A pointer to an [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span></span>

`aptType`  
<span data-ttu-id="e6074-109">[out] Bir işaretçi bir [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) arayanın Grup belirten numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="e6074-109">[out] A pointer to an [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="e6074-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e6074-110">Return value</span></span>


|<span data-ttu-id="e6074-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="e6074-111">Constant</span></span>  |<span data-ttu-id="e6074-112">Değer</span><span class="sxs-lookup"><span data-stu-id="e6074-112">Value</span></span>  |<span data-ttu-id="e6074-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6074-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="e6074-114">0</span><span class="sxs-lookup"><span data-stu-id="e6074-114">0</span></span> | <span data-ttu-id="e6074-115">İşlev başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e6074-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="e6074-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="e6074-116">0x80000008</span></span> | <span data-ttu-id="e6074-117">Çağıran bir grupta yürütülmüyor.</span><span class="sxs-lookup"><span data-stu-id="e6074-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="e6074-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6074-118">Remarks</span></span>

<span data-ttu-id="e6074-119">Bu işlev çağrısı sarmalar [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e6074-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6074-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6074-120">Requirements</span></span>  
 <span data-ttu-id="e6074-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6074-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6074-122">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e6074-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e6074-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e6074-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6074-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6074-124">See also</span></span>  
[<span data-ttu-id="e6074-125">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e6074-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
