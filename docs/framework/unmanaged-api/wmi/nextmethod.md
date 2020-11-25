---
title: NextMethod işlevi (yönetilmeyen API Başvurusu)
description: NextMethod işlevi bir Numaralandırmadaki sonraki yöntemi alır.
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
ms.openlocfilehash: a0466aee47b0a6142870640c78b43f49e221ac2b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726775"
---
# <a name="nextmethod-function"></a><span data-ttu-id="58edb-103">NextMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="58edb-103">NextMethod function</span></span>

<span data-ttu-id="58edb-104">Bir sonraki yöntemi [Beginmethodenumeration](beginmethodenumeration.md)çağrısıyla başlayan bir Numaralandırmadaki alır.</span><span class="sxs-lookup"><span data-stu-id="58edb-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="58edb-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="58edb-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="58edb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58edb-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="58edb-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="58edb-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="58edb-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="58edb-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="58edb-109">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="58edb-109">[in] Reserved.</span></span> <span data-ttu-id="58edb-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58edb-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="58edb-111">dışı Çağrıdan önce işaret eden bir işaretçi `null` .</span><span class="sxs-lookup"><span data-stu-id="58edb-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="58edb-112">İşlev döndüğünde, `BSTR` Yöntem adını içeren yeni bir adresi.</span><span class="sxs-lookup"><span data-stu-id="58edb-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span>

`ppSignatureIn`  
<span data-ttu-id="58edb-113">dışı Yöntemi için parametreleri içeren bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) öğesine işaretçi alan bir işaretçi `in` .</span><span class="sxs-lookup"><span data-stu-id="58edb-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span>

`ppSignatureOut`  
<span data-ttu-id="58edb-114">dışı Yöntemi için parametreleri içeren bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) öğesine işaretçi alan bir işaretçi `out` .</span><span class="sxs-lookup"><span data-stu-id="58edb-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="58edb-115">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="58edb-115">Return value</span></span>

<span data-ttu-id="58edb-116">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58edb-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="58edb-117">Sabit</span><span class="sxs-lookup"><span data-stu-id="58edb-117">Constant</span></span>  |<span data-ttu-id="58edb-118">Değer</span><span class="sxs-lookup"><span data-stu-id="58edb-118">Value</span></span>  |<span data-ttu-id="58edb-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58edb-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="58edb-120">0x8004101D</span><span class="sxs-lookup"><span data-stu-id="58edb-120">0x8004101d</span></span> | <span data-ttu-id="58edb-121">İşleve bir çağrı yoktu [`BeginEnumeration`](beginenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="58edb-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="58edb-122">0</span><span class="sxs-lookup"><span data-stu-id="58edb-122">0</span></span> | <span data-ttu-id="58edb-123">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="58edb-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="58edb-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="58edb-124">0x40005</span></span> | <span data-ttu-id="58edb-125">Numaralandırmada daha fazla özellik yok.</span><span class="sxs-lookup"><span data-stu-id="58edb-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="58edb-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58edb-126">Remarks</span></span>

<span data-ttu-id="58edb-127">Bu işlev, [IWbemClassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="58edb-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="58edb-128">Çağıran, [Beginmethodenumeration](beginmethodenumeration.md) işlevini çağırarak numaralandırma dizisini başlatır ve ardından işlev dönene kadar [NextMethod] işlevini çağırır `WBEM_S_NO_MORE_DATA` .</span><span class="sxs-lookup"><span data-stu-id="58edb-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="58edb-129">İsteğe bağlı olarak, çağıran, [Endmethodenumeration](endmethodenumeration.md)' ı çağırarak sırayı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="58edb-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="58edb-130">Çağıran, her zaman [Endmethodenumeration](endmethodenumeration.md) ' ı çağırarak numaralandırmayı erken sonlandıramayabilir.</span><span class="sxs-lookup"><span data-stu-id="58edb-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="58edb-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="58edb-131">Example</span></span>

<span data-ttu-id="58edb-132">Bir C++ örneği için, bkz. [IWbemClassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="58edb-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="58edb-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58edb-133">Requirements</span></span>  

 <span data-ttu-id="58edb-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58edb-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58edb-135">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="58edb-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="58edb-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="58edb-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58edb-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58edb-137">See also</span></span>

- [<span data-ttu-id="58edb-138">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="58edb-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
