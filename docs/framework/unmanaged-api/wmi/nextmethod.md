---
title: NextMethod işlevi (Yönetilmeyen API Başvurusu)
description: NextMethod işlevi bir sonraki yöntemi numaralandırmada alır.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 36acd6135110a8865bd8efdda628c352c01b4f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174933"
---
# <a name="nextmethod-function"></a><span data-ttu-id="222b1-103">NextMethod fonksiyonu</span><span class="sxs-lookup"><span data-stu-id="222b1-103">NextMethod function</span></span>
<span data-ttu-id="222b1-104">[BeginMethodEnumeration](beginmethodenumeration.md)için bir çağrı ile başlayan bir numaralandırma sonraki yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="222b1-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="222b1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="222b1-105">Syntax</span></span>  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```  

## <a name="parameters"></a><span data-ttu-id="222b1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="222b1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="222b1-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="222b1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="222b1-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="222b1-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="222b1-109">[içinde] Saklı -dır.</span><span class="sxs-lookup"><span data-stu-id="222b1-109">[in] Reserved.</span></span> <span data-ttu-id="222b1-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="222b1-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="222b1-111">[çıkış] Aramadan önce `null` işaret eden bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="222b1-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="222b1-112">İşlev döndüğünde, yöntem adını `BSTR` içeren yeni bir adres.</span><span class="sxs-lookup"><span data-stu-id="222b1-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span>

`ppSignatureIn`  
<span data-ttu-id="222b1-113">[çıkış] Yöntem için parametreleri `in` içeren bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) için bir işaretçi alan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="222b1-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span>

`ppSignatureOut`  
<span data-ttu-id="222b1-114">[çıkış] Yöntem için parametreleri `out` içeren bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) için bir işaretçi alan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="222b1-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="222b1-115">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="222b1-115">Return value</span></span>

<span data-ttu-id="222b1-116">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="222b1-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="222b1-117">Sabit</span><span class="sxs-lookup"><span data-stu-id="222b1-117">Constant</span></span>  |<span data-ttu-id="222b1-118">Değer</span><span class="sxs-lookup"><span data-stu-id="222b1-118">Value</span></span>  |<span data-ttu-id="222b1-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="222b1-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="222b1-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="222b1-120">0x8004101d</span></span> | <span data-ttu-id="222b1-121">Fonksiyon arayın. [`BeginEnumeration`](beginenumeration.md)</span><span class="sxs-lookup"><span data-stu-id="222b1-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="222b1-122">0</span><span class="sxs-lookup"><span data-stu-id="222b1-122">0</span></span> | <span data-ttu-id="222b1-123">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="222b1-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="222b1-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="222b1-124">0x40005</span></span> | <span data-ttu-id="222b1-125">Numaralandırmada başka özellik yok.</span><span class="sxs-lookup"><span data-stu-id="222b1-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="222b1-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="222b1-126">Remarks</span></span>

<span data-ttu-id="222b1-127">Bu [işlev, IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="222b1-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="222b1-128">Arayan numaralandırma sırasını [BeginMethodEnumeration](beginmethodenumeration.md) işlevini çağırarak başlatır ve işlev dönene `WBEM_S_NO_MORE_DATA`kadar [NextMethod] işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="222b1-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="222b1-129">İsteğe bağlı olarak, arayan [EndMethodEnumeration](endmethodenumeration.md)çağırarak sırayı bitirir.</span><span class="sxs-lookup"><span data-stu-id="222b1-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="222b1-130">Arayan, [endmethodenumeration'ı](endmethodenumeration.md) herhangi bir zamanda arayarak numaralandırmayı erken sonlandırabilir.</span><span class="sxs-lookup"><span data-stu-id="222b1-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="222b1-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="222b1-131">Example</span></span>

<span data-ttu-id="222b1-132">C++ örneği için [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemine bakın.</span><span class="sxs-lookup"><span data-stu-id="222b1-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="222b1-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="222b1-133">Requirements</span></span>  
 <span data-ttu-id="222b1-134">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="222b1-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="222b1-135">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="222b1-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="222b1-136">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="222b1-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="222b1-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="222b1-137">See also</span></span>

- [<span data-ttu-id="222b1-138">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="222b1-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
