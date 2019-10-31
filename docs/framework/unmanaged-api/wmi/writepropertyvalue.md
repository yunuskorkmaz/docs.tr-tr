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
ms.openlocfilehash: f02fb3877d55e9f47384b281573202712c29c606
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107298"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="d7666-103">WritePropertyValue işlevi</span><span class="sxs-lookup"><span data-stu-id="d7666-103">WritePropertyValue function</span></span>
<span data-ttu-id="d7666-104">Bir özellik tanıtıcısı tarafından tanımlanan bir özelliğe belirtilen sayıda bayt yazar.</span><span class="sxs-lookup"><span data-stu-id="d7666-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="d7666-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7666-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="d7666-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7666-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d7666-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d7666-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d7666-108">'ndaki Bir [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d7666-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="d7666-109">'ndaki Bu özelliği tanımlayan tanıtıcıyı içeren bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d7666-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="d7666-110">Tanıtıcı, [Getpropertyhandle](getpropertyhandle.md) işlevi çağırarak alınabilir.</span><span class="sxs-lookup"><span data-stu-id="d7666-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="d7666-111">'ndaki Özelliğe yazılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="d7666-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="d7666-112">Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d7666-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="d7666-113">dışı Verileri içeren bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d7666-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="d7666-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d7666-114">Return value</span></span>

<span data-ttu-id="d7666-115">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d7666-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d7666-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="d7666-116">Constant</span></span>  |<span data-ttu-id="d7666-117">Değer</span><span class="sxs-lookup"><span data-stu-id="d7666-117">Value</span></span>  |<span data-ttu-id="d7666-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7666-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d7666-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d7666-119">0x80041008</span></span> | <span data-ttu-id="d7666-120">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="d7666-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="d7666-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="d7666-121">0x80041005</span></span> | <span data-ttu-id="d7666-122">Tür uyumsuzluğu oluştu.</span><span class="sxs-lookup"><span data-stu-id="d7666-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d7666-123">0</span><span class="sxs-lookup"><span data-stu-id="d7666-123">0</span></span> | <span data-ttu-id="d7666-124">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="d7666-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d7666-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7666-125">Remarks</span></span>

<span data-ttu-id="d7666-126">Bu işlev, [IWbemClassObject:: WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="d7666-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="d7666-127">Dizeyi ve diğer tüm`DWORD` olmayan veya`QWORD` olmayan verileri ayarlamak için bu işlevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d7666-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="d7666-128">Dize olmayan özellik değerleri için `lNumBytes`, belirtilen özellik türünün doğru veri boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7666-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="d7666-129">Dize özellik değerleri için `lNumBytes`, belirtilen dizenin bayt cinsinden uzunluğu olmalıdır ve dizenin kendisi, bayt cinsinden bir çift uzunluğunda olmalı ve ardından null sonlandırma karakteriyle birlikte gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="d7666-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="d7666-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7666-130">Requirements</span></span>  
<span data-ttu-id="d7666-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7666-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7666-132">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="d7666-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d7666-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d7666-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7666-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7666-134">See also</span></span>

- [<span data-ttu-id="d7666-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d7666-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
