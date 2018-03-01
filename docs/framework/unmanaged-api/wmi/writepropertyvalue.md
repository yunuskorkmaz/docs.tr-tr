---
title: "WritePropertyValue işlevi (yönetilmeyen API Başvurusu)"
description: "WritePropertyValue işlevi bir özelliğe bayt yazar."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7221c9e0f1cb49ab0e27130ce69c0527ba903148
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="a2108-103">WritePropertyValue işlevi</span><span class="sxs-lookup"><span data-stu-id="a2108-103">WritePropertyValue function</span></span>
<span data-ttu-id="a2108-104">Bir özellik tanımlayıcısı tarafından tanımlanan bir özellik için belirtilen sayıda baytı yazar.</span><span class="sxs-lookup"><span data-stu-id="a2108-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="a2108-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2108-105">Syntax</span></span>  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="a2108-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2108-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a2108-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a2108-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a2108-108">[in] Bir işaretçi bir [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="a2108-108">[in] A pointer to an [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.</span></span>

`lHandle`  
<span data-ttu-id="a2108-109">[in] Bu özelliği tanımlar tanıtıcı içeren bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a2108-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="a2108-110">Tanıtıcı çağırarak alınabilir [GetPropertyHandle](getpropertyhandle.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="a2108-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="a2108-111">[in] Özelliğin yazılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="a2108-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="a2108-112">Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.</span><span class="sxs-lookup"><span data-stu-id="a2108-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="a2108-113">[out] Verileri içeren bayt dizisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a2108-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="a2108-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="a2108-114">Return value</span></span>

<span data-ttu-id="a2108-115">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="a2108-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a2108-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="a2108-116">Constant</span></span>  |<span data-ttu-id="a2108-117">Değer</span><span class="sxs-lookup"><span data-stu-id="a2108-117">Value</span></span>  |<span data-ttu-id="a2108-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2108-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a2108-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a2108-119">0x80041008</span></span> | <span data-ttu-id="a2108-120">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="a2108-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="a2108-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="a2108-121">0x80041005</span></span> | <span data-ttu-id="a2108-122">Tür uyumsuzluğu oluştu.</span><span class="sxs-lookup"><span data-stu-id="a2108-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a2108-123">0</span><span class="sxs-lookup"><span data-stu-id="a2108-123">0</span></span> | <span data-ttu-id="a2108-124">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="a2108-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a2108-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2108-125">Remarks</span></span>

<span data-ttu-id="a2108-126">Bu işlev çağrısı sarmalar [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a2108-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="a2108-127">Dize ve tüm diğer olmayan ayarlamak için bu işlevi kullanın`DWORD` olmayan veya -`QWORD` veri.</span><span class="sxs-lookup"><span data-stu-id="a2108-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="a2108-128">Dize olmayan özellik değerleri için `lNumBytes` belirtilen özellik türü doğru veri boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2108-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="a2108-129">Dize özellik değerleri için `lNumBytes` uzunluğu olmalıdır ve bayt cinsinden belirtilen dize, dize kendisi bayt bile bir uzunlukta olmalıdır ve null sonlandırma karakteri ile izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="a2108-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="a2108-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2108-130">Requirements</span></span>  
<span data-ttu-id="a2108-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2108-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2108-132">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a2108-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a2108-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a2108-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2108-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2108-134">See also</span></span>  
[<span data-ttu-id="a2108-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a2108-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
