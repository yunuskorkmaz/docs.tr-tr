---
title: GetCurrentApartmentType işlevi (yönetilmeyen API Başvurusu)
description: GetCurrentApartmentType işlevi, çağıranın yürütüldüğü grup türünü alır.
ms.date: 11/06/2017
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
ms.openlocfilehash: 0832867d86b7dda80e037846d9aa66c1d37f87be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726203"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="4eb50-103">GetCurrentApartmentType işlevi</span><span class="sxs-lookup"><span data-stu-id="4eb50-103">GetCurrentApartmentType function</span></span>

<span data-ttu-id="4eb50-104">Çağıranın yürütüldüğü grup türünü alır.</span><span class="sxs-lookup"><span data-stu-id="4eb50-104">Retrieves the type of apartment in which the caller is executing.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4eb50-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4eb50-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a><span data-ttu-id="4eb50-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4eb50-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4eb50-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="4eb50-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4eb50-108">'ndaki [Iomthreadingınfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4eb50-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="4eb50-109">dışı Arayanın Apartmanı belirten bir [Apttype](/windows/win32/api/objidlbase/ne-objidlbase-apttype) numaralandırma değeri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4eb50-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="4eb50-110">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="4eb50-110">Return value</span></span>

|<span data-ttu-id="4eb50-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="4eb50-111">Constant</span></span>  |<span data-ttu-id="4eb50-112">Değer</span><span class="sxs-lookup"><span data-stu-id="4eb50-112">Value</span></span>  |<span data-ttu-id="4eb50-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4eb50-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="4eb50-114">0</span><span class="sxs-lookup"><span data-stu-id="4eb50-114">0</span></span> | <span data-ttu-id="4eb50-115">İşlev başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="4eb50-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="4eb50-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="4eb50-116">0x80000008</span></span> | <span data-ttu-id="4eb50-117">Arayan bir grupta yürütülmüyor.</span><span class="sxs-lookup"><span data-stu-id="4eb50-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="4eb50-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4eb50-118">Remarks</span></span>

<span data-ttu-id="4eb50-119">Bu işlev, [ICommandText Threadingınfo:: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) metoduna bir çağrıyı sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="4eb50-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4eb50-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4eb50-120">Requirements</span></span>  

 <span data-ttu-id="4eb50-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4eb50-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eb50-122">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="4eb50-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4eb50-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4eb50-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb50-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4eb50-124">See also</span></span>

- [<span data-ttu-id="4eb50-125">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4eb50-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
