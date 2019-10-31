---
title: EndMethodEnumeration işlevi (yönetilmeyen API Başvurusu)
description: EndMethodEnumeration işlevi bir yöntem numaralandırma sırasını sonlandırır.
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 174cf76d4b0ddf07e67e02bff20a983dca08819a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132016"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="bff3e-103">EndMethodEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="bff3e-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="bff3e-104">[Beginmethodenumeration işlevi](beginmethodenumeration.md)çağrısıyla başlatılan bir numaralandırma dizisini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="bff3e-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="bff3e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bff3e-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="bff3e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bff3e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="bff3e-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="bff3e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="bff3e-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bff3e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="bff3e-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="bff3e-109">Return value</span></span>

<span data-ttu-id="bff3e-110">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bff3e-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bff3e-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="bff3e-111">Constant</span></span>  |<span data-ttu-id="bff3e-112">Değer</span><span class="sxs-lookup"><span data-stu-id="bff3e-112">Value</span></span>  |<span data-ttu-id="bff3e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bff3e-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="bff3e-114">0x8004101D</span><span class="sxs-lookup"><span data-stu-id="bff3e-114">0x8004101d</span></span> | <span data-ttu-id="bff3e-115">Bir iç hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bff3e-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="bff3e-116">0</span><span class="sxs-lookup"><span data-stu-id="bff3e-116">0</span></span> | <span data-ttu-id="bff3e-117">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="bff3e-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="bff3e-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bff3e-118">Remarks</span></span>

<span data-ttu-id="bff3e-119">Bu işlev, [IWbemClassObject:: EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="bff3e-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="bff3e-120">Çağıran, [Beginmethodenumeration işlevini](beginmethodenumeration.md)kullanarak numaralandırma sırasını başlatır ve ardından Yöntem `WBEM_S_NO_MORE_DATA`dönene kadar [NextMethod işlevini](nextmethod.md )çağırır.</span><span class="sxs-lookup"><span data-stu-id="bff3e-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="bff3e-121">Çağıran, isteğe bağlı olarak `EndMethodEnumeration`çağırarak sırayı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="bff3e-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="bff3e-122">Çağıran, herhangi bir zamanda `EndMethodEnumeration` çağırarak numaralandırmayı erken sonlandıramayabilir.</span><span class="sxs-lookup"><span data-stu-id="bff3e-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="bff3e-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bff3e-123">Requirements</span></span>  
 <span data-ttu-id="bff3e-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bff3e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bff3e-125">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="bff3e-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="bff3e-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bff3e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bff3e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bff3e-127">See also</span></span>

- [<span data-ttu-id="bff3e-128">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bff3e-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
