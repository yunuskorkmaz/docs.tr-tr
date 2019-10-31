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
ms.openlocfilehash: 6ecd2b49d6850a8fae25ddca54f855fdda2ccabb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120348"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="3ceea-103">GetCurrentApartmentType işlevi</span><span class="sxs-lookup"><span data-stu-id="3ceea-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="3ceea-104">Çağıranın yürütüldüğü grup türünü alır.</span><span class="sxs-lookup"><span data-stu-id="3ceea-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="3ceea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ceea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="3ceea-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ceea-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3ceea-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3ceea-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3ceea-108">'ndaki [Iomthreadingınfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3ceea-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="3ceea-109">dışı Arayanın Apartmanı belirten bir [Apttype](/windows/win32/api/objidlbase/ne-objidlbase-apttype) numaralandırma değeri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3ceea-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="3ceea-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="3ceea-110">Return value</span></span>

|<span data-ttu-id="3ceea-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="3ceea-111">Constant</span></span>  |<span data-ttu-id="3ceea-112">Değer</span><span class="sxs-lookup"><span data-stu-id="3ceea-112">Value</span></span>  |<span data-ttu-id="3ceea-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ceea-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="3ceea-114">0</span><span class="sxs-lookup"><span data-stu-id="3ceea-114">0</span></span> | <span data-ttu-id="3ceea-115">İşlev başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3ceea-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="3ceea-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="3ceea-116">0x80000008</span></span> | <span data-ttu-id="3ceea-117">Arayan bir grupta yürütülmüyor.</span><span class="sxs-lookup"><span data-stu-id="3ceea-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="3ceea-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ceea-118">Remarks</span></span>

<span data-ttu-id="3ceea-119">Bu işlev, [ICommandText Threadingınfo:: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) metoduna bir çağrıyı sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="3ceea-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ceea-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ceea-120">Requirements</span></span>  
 <span data-ttu-id="3ceea-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ceea-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ceea-122">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="3ceea-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3ceea-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3ceea-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ceea-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ceea-124">See also</span></span>

- [<span data-ttu-id="3ceea-125">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3ceea-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
