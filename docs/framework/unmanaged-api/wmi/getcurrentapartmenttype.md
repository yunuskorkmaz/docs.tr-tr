---
title: GetCurrentApartmentType fonksiyonu (Yönetilmeyen API Başvurusu)
description: GetCurrentApartmentType işlevi, arayanın yürütüldettiği daire türünü alır.
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
ms.openlocfilehash: 3fc88f7997ee5a6c25359243e1ee97a041050eb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176831"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="d545d-103">GetCurrentApartmentType fonksiyonu</span><span class="sxs-lookup"><span data-stu-id="d545d-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="d545d-104">Arayanın yürütüldettiği daire türünü alır.</span><span class="sxs-lookup"><span data-stu-id="d545d-104">Retrieves the type of apartment in which the caller is executing.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d545d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d545d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a><span data-ttu-id="d545d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d545d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d545d-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="d545d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d545d-108">[içinde] [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d545d-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="d545d-109">[çıkış] Arayan kişinin dairesini gösteren [bir APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) numaralandırma değerine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d545d-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="d545d-110">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="d545d-110">Return value</span></span>

|<span data-ttu-id="d545d-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="d545d-111">Constant</span></span>  |<span data-ttu-id="d545d-112">Değer</span><span class="sxs-lookup"><span data-stu-id="d545d-112">Value</span></span>  |<span data-ttu-id="d545d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d545d-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="d545d-114">0</span><span class="sxs-lookup"><span data-stu-id="d545d-114">0</span></span> | <span data-ttu-id="d545d-115">İşlev başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d545d-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="d545d-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="d545d-116">0x80000008</span></span> | <span data-ttu-id="d545d-117">Arayan bir dairede yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d545d-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d545d-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d545d-118">Remarks</span></span>

<span data-ttu-id="d545d-119">Bu [işlev, IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="d545d-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d545d-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d545d-120">Requirements</span></span>  
 <span data-ttu-id="d545d-121">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d545d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d545d-122">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d545d-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d545d-123">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d545d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d545d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d545d-124">See also</span></span>

- [<span data-ttu-id="d545d-125">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d545d-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
