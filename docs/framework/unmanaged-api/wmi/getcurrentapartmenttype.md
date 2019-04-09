---
title: GetCurrentApartmentType işlevi (yönetilmeyen API Başvurusu)
description: GetCurrentApartmentType işlevi çağıran dosyanızın çalıştığı Grup türünü alır.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ead1c1a91b910e7cfbb09f17ba823fc7a77ce0f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181447"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="33fc2-103">GetCurrentApartmentType işlevi</span><span class="sxs-lookup"><span data-stu-id="33fc2-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="33fc2-104">Arayan içinde yürütüyor Grup türünü alır.</span><span class="sxs-lookup"><span data-stu-id="33fc2-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="33fc2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33fc2-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="33fc2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33fc2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="33fc2-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="33fc2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="33fc2-108">[in] Bir işaretçi bir [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) örneği.</span><span class="sxs-lookup"><span data-stu-id="33fc2-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="33fc2-109">[out] Bir işaretçi bir [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) arayanın apartman belirten numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="33fc2-109">[out] A pointer to an [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="33fc2-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="33fc2-110">Return value</span></span>

|<span data-ttu-id="33fc2-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="33fc2-111">Constant</span></span>  |<span data-ttu-id="33fc2-112">Değer</span><span class="sxs-lookup"><span data-stu-id="33fc2-112">Value</span></span>  |<span data-ttu-id="33fc2-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33fc2-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="33fc2-114">0</span><span class="sxs-lookup"><span data-stu-id="33fc2-114">0</span></span> | <span data-ttu-id="33fc2-115">İşlev başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="33fc2-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="33fc2-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="33fc2-116">0x80000008</span></span> | <span data-ttu-id="33fc2-117">Arayan bir grupta yürütülmüyor.</span><span class="sxs-lookup"><span data-stu-id="33fc2-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="33fc2-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33fc2-118">Remarks</span></span>

<span data-ttu-id="33fc2-119">Bu işlev bir çağrı sarılır [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="33fc2-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="33fc2-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33fc2-120">Requirements</span></span>  
 <span data-ttu-id="33fc2-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33fc2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33fc2-122">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="33fc2-122">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="33fc2-123">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="33fc2-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33fc2-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33fc2-124">See also</span></span>

- [<span data-ttu-id="33fc2-125">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="33fc2-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
