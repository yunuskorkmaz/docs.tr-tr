---
title: WritePropertyValue işlevi (yönetilmeyen API Başvurusu)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2a4eb444967390492be33b25866de8a93a1698c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393913"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="09fbc-103">WritePropertyValue işlevi</span><span class="sxs-lookup"><span data-stu-id="09fbc-103">WritePropertyValue function</span></span>
<span data-ttu-id="09fbc-104">Belirtilen sayıda baytı bir özellik tanımlayıcısı tarafından tanımlanan bir özellik yazar.</span><span class="sxs-lookup"><span data-stu-id="09fbc-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="09fbc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09fbc-105">Syntax</span></span>  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a><span data-ttu-id="09fbc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09fbc-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="09fbc-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="09fbc-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="09fbc-108">[in] Bir işaretçi bir [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) örneği.</span><span class="sxs-lookup"><span data-stu-id="09fbc-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="09fbc-109">[in] Bu özelliği tanımlar tanıtıcı içeren bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="09fbc-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="09fbc-110">Tanıtıcı çağrılarak alınabilir [GetPropertyHandle](getpropertyhandle.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="09fbc-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>   

`lNumBytes`  
<span data-ttu-id="09fbc-111">[in] Özelliğini yazılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="09fbc-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="09fbc-112">Bkz: [açıklamalar](#remarks) bölümünde daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="09fbc-112">See the [Remarks](#remarks) section for more information.</span></span>

`pHandle`   
<span data-ttu-id="09fbc-113">[out] Verileri içeren bir bayt dizisine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="09fbc-113">[out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="09fbc-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="09fbc-114">Return value</span></span>

<span data-ttu-id="09fbc-115">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="09fbc-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="09fbc-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="09fbc-116">Constant</span></span>  |<span data-ttu-id="09fbc-117">Değer</span><span class="sxs-lookup"><span data-stu-id="09fbc-117">Value</span></span>  |<span data-ttu-id="09fbc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09fbc-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="09fbc-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="09fbc-119">0x80041008</span></span> | <span data-ttu-id="09fbc-120">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="09fbc-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="09fbc-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="09fbc-121">0x80041005</span></span> | <span data-ttu-id="09fbc-122">Tür uyuşmazlığı oluştu.</span><span class="sxs-lookup"><span data-stu-id="09fbc-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="09fbc-123">0</span><span class="sxs-lookup"><span data-stu-id="09fbc-123">0</span></span> | <span data-ttu-id="09fbc-124">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="09fbc-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="09fbc-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09fbc-125">Remarks</span></span>

<span data-ttu-id="09fbc-126">Bu işlev bir çağrı sarılır [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="09fbc-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="09fbc-127">Dize ve tüm diğer olmayan ayarlamak için bu işlevi kullanın`DWORD` olmayan veya -`QWORD` veri.</span><span class="sxs-lookup"><span data-stu-id="09fbc-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="09fbc-128">Dize olmayan özellik değerleri için `lNumBytes` belirtilen özellik türü doğru veri boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="09fbc-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="09fbc-129">Dize özelliği değerleri için `lNumBytes` uzunluğu olmalıdır bayt cinsinden belirtilen dize ve dize kendi bir bayt uzunlukta olmalıdır ve bir sonlandırma boş karakteri ile izlenmesi.</span><span class="sxs-lookup"><span data-stu-id="09fbc-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="09fbc-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09fbc-130">Requirements</span></span>  
<span data-ttu-id="09fbc-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09fbc-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09fbc-132">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="09fbc-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="09fbc-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="09fbc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09fbc-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09fbc-134">See also</span></span>  
[<span data-ttu-id="09fbc-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="09fbc-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
