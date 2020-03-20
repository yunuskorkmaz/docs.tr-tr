---
title: WritePropertyValue işlevi (Yönetilmeyen API Başvurusu)
description: WritePropertyValue işlevi bir özelliğe bayt yazar.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4a950beef2e9bf8c0230d6a38008d75f89373410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174842"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="e0a14-103">WritePropertyValue fonksiyonu</span><span class="sxs-lookup"><span data-stu-id="e0a14-103">WritePropertyValue function</span></span>
<span data-ttu-id="e0a14-104">Özellik tutamacı tarafından tanımlanan bir özelliğe belirli sayıda bayt yazar.</span><span class="sxs-lookup"><span data-stu-id="e0a14-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e0a14-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0a14-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a><span data-ttu-id="e0a14-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0a14-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e0a14-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e0a14-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e0a14-108">[içinde] [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e0a14-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="e0a14-109">[içinde] Bu özelliği tanımlayan tutamacı içeren bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e0a14-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="e0a14-110">Tanıtıcı [GetPropertyHandle](getpropertyhandle.md) işlevini arayarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="e0a14-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>

`lNumBytes`  
<span data-ttu-id="e0a14-111">[içinde] Tesise yazılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="e0a14-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="e0a14-112">Daha fazla bilgi için [Açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e0a14-112">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="e0a14-113">`pHandle`[çıkış] Verileri içeren bayt dizisiiçin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e0a14-113">`pHandle` [out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="e0a14-114">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="e0a14-114">Return value</span></span>

<span data-ttu-id="e0a14-115">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0a14-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e0a14-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="e0a14-116">Constant</span></span>  |<span data-ttu-id="e0a14-117">Değer</span><span class="sxs-lookup"><span data-stu-id="e0a14-117">Value</span></span>  |<span data-ttu-id="e0a14-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0a14-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e0a14-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e0a14-119">0x80041008</span></span> | <span data-ttu-id="e0a14-120">Parametre geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="e0a14-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="e0a14-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="e0a14-121">0x80041005</span></span> | <span data-ttu-id="e0a14-122">Bir tür uyuşmazlığı oluştu.</span><span class="sxs-lookup"><span data-stu-id="e0a14-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e0a14-123">0</span><span class="sxs-lookup"><span data-stu-id="e0a14-123">0</span></span> | <span data-ttu-id="e0a14-124">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="e0a14-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e0a14-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0a14-125">Remarks</span></span>

<span data-ttu-id="e0a14-126">Bu [işlev, IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="e0a14-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="e0a14-127">Dize ve diğer tüm`DWORD` `QWORD` veri olmayan veya olmayan ayarlamak için bu işlevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0a14-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="e0a14-128">Non string özellik `lNumBytes` değerleri için, belirtilen özellik türünün doğru veri boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0a14-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="e0a14-129">Dize özellik `lNumBytes` değerleri için, baytlarda belirtilen dize uzunluğu olmalıdır ve dize kendisi bayt eşit uzunlukta olmalı ve bir null-sonlandırma karakteri ile takip edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e0a14-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0a14-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0a14-130">Requirements</span></span>  
<span data-ttu-id="e0a14-131">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0a14-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0a14-132">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e0a14-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e0a14-133">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e0a14-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a14-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0a14-134">See also</span></span>

- [<span data-ttu-id="e0a14-135">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e0a14-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
