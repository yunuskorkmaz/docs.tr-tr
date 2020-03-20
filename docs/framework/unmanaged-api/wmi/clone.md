---
title: Klon işlevi (Yönetilmeyen API Başvurusu)
description: Klon işlevi, geçerli olanın tam bir klonu olan yeni bir nesneyi döndürür.
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: cb4951a1f289417482bfa1287028cc66349a5938
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176857"
---
# <a name="clone-function"></a><span data-ttu-id="1f4c3-103">Clone işlevi</span><span class="sxs-lookup"><span data-stu-id="1f4c3-103">Clone function</span></span>
<span data-ttu-id="1f4c3-104">Geçerli nesnenin tam bir klonu olan yeni bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-104">Returns a new object that is a complete clone of the current object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1f4c3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f4c3-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [out] IWbemClassObject**  ppCopy
);
```  

## <a name="parameters"></a><span data-ttu-id="1f4c3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f4c3-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="1f4c3-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="1f4c3-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="1f4c3-109">[çıkış] Tam bir yalnız olan yeni `ptr`bir nesne .</span><span class="sxs-lookup"><span data-stu-id="1f4c3-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="1f4c3-110">Geçerli nesnenin `null` kopyasını alıyorsa, bu bağımsız değişken olamaz.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="1f4c3-111">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="1f4c3-111">Return value</span></span>

<span data-ttu-id="1f4c3-112">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1f4c3-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1f4c3-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="1f4c3-113">Constant</span></span>  |<span data-ttu-id="1f4c3-114">Değer</span><span class="sxs-lookup"><span data-stu-id="1f4c3-114">Value</span></span>  |<span data-ttu-id="1f4c3-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f4c3-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="1f4c3-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="1f4c3-116">0x80041001</span></span> | <span data-ttu-id="1f4c3-117">Genel bir başarısızlık oldu.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1f4c3-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1f4c3-118">0x80041008</span></span> | <span data-ttu-id="1f4c3-119">`null`bir parametre olarak belirtilmiştir ve bu kullanımda yasal değildir.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="1f4c3-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="1f4c3-120">0x80041006</span></span> | <span data-ttu-id="1f4c3-121">Nesneyi klonlamak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="1f4c3-122">0</span><span class="sxs-lookup"><span data-stu-id="1f4c3-122">0</span></span> | <span data-ttu-id="1f4c3-123">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1f4c3-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f4c3-124">Remarks</span></span>

<span data-ttu-id="1f4c3-125">Bu [işlev, IWbemClassObject::Klon](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="1f4c3-126">Klonlanan nesne, başvuru sayısı 1 olan bir COM nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="1f4c3-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f4c3-127">Requirements</span></span>  
 <span data-ttu-id="1f4c3-128">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f4c3-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f4c3-129">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1f4c3-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1f4c3-130">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1f4c3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f4c3-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f4c3-131">See also</span></span>

- [<span data-ttu-id="1f4c3-132">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1f4c3-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
