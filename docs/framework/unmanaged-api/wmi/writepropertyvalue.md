---
title: WritePropertyValue işlevi (yönetilmeyen API Başvurusu)
description: WritePropertyValue işlevi, bir özelliğe bayt yazar.
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
ms.openlocfilehash: e225516b06c477dc1a24cf721bc3e1ade9076b75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729414"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="b7ff0-103">WritePropertyValue işlevi</span><span class="sxs-lookup"><span data-stu-id="b7ff0-103">WritePropertyValue function</span></span>

<span data-ttu-id="b7ff0-104">Bir özellik tanıtıcısı tarafından tanımlanan bir özelliğe belirtilen sayıda bayt yazar.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="b7ff0-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b7ff0-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a><span data-ttu-id="b7ff0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7ff0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b7ff0-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b7ff0-108">'ndaki Bir [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="b7ff0-109">'ndaki Bu özelliği tanımlayan tanıtıcıyı içeren bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="b7ff0-110">Tanıtıcı, [Getpropertyhandle](getpropertyhandle.md) işlevi çağırarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>

`lNumBytes`  
<span data-ttu-id="b7ff0-111">'ndaki Özelliğe yazılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="b7ff0-112">Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-112">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="b7ff0-113">`pHandle` dışı Verileri içeren bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-113">`pHandle` [out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="b7ff0-114">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="b7ff0-114">Return value</span></span>

<span data-ttu-id="b7ff0-115">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b7ff0-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b7ff0-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="b7ff0-116">Constant</span></span>  |<span data-ttu-id="b7ff0-117">Değer</span><span class="sxs-lookup"><span data-stu-id="b7ff0-117">Value</span></span>  |<span data-ttu-id="b7ff0-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7ff0-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b7ff0-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b7ff0-119">0x80041008</span></span> | <span data-ttu-id="b7ff0-120">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="b7ff0-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="b7ff0-121">0x80041005</span></span> | <span data-ttu-id="b7ff0-122">Tür uyumsuzluğu oluştu.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b7ff0-123">0</span><span class="sxs-lookup"><span data-stu-id="b7ff0-123">0</span></span> | <span data-ttu-id="b7ff0-124">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b7ff0-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7ff0-125">Remarks</span></span>

<span data-ttu-id="b7ff0-126">Bu işlev, [IWbemClassObject:: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="b7ff0-127">Bu işlevi, dizeyi ve diğer tüm veri olmayan verileri ayarlamak için kullanın `DWORD` `QWORD` .</span><span class="sxs-lookup"><span data-stu-id="b7ff0-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="b7ff0-128">Dize olmayan özellik değerleri için `lNumBytes` belirtilen özellik türünün doğru veri boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="b7ff0-129">Dize özellik değerleri için, `lNumBytes` belirtilen dizenin bayt cinsinden uzunluğu olmalıdır ve dizenin kendisi, bayt cinsinden bir çift uzunluğunda olmalı ve ardından null sonlandırma karakteriyle birlikte gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="b7ff0-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7ff0-130">Requirements</span></span>  

<span data-ttu-id="b7ff0-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7ff0-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7ff0-132">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="b7ff0-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b7ff0-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b7ff0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ff0-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7ff0-134">See also</span></span>

- [<span data-ttu-id="b7ff0-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b7ff0-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
