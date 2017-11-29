---
title: "BeginMethodEnumeration işlevi (yönetilmeyen API Başvurusu)"
description: "Nesnenin yöntemleri numaralandırması BeginMethodEnumeration işlevi başlar"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginMethodEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginMethodEnumeration
helpviewer_keywords: BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e44c432f9503f96ad4dab9e25b78e6dd148f94c
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="beginenumeration-function"></a><span data-ttu-id="c276a-103">BeginEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="c276a-103">BeginEnumeration function</span></span>
<span data-ttu-id="c276a-104">Nesne için kullanılabilen yöntemler numaralandırması başlar.</span><span class="sxs-lookup"><span data-stu-id="c276a-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="c276a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c276a-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="c276a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c276a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="c276a-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c276a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="c276a-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="c276a-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="c276a-109">[in] Sıfır (0) tüm yöntemler ve numaralandırma kapsamını belirten bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="c276a-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="c276a-110">Aşağıdaki bayraklar tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="c276a-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="c276a-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="c276a-111">Constant</span></span>  |<span data-ttu-id="c276a-112">Değer</span><span class="sxs-lookup"><span data-stu-id="c276a-112">Value</span></span>  |<span data-ttu-id="c276a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c276a-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="c276a-114">0x10</span><span class="sxs-lookup"><span data-stu-id="c276a-114">0x10</span></span> | <span data-ttu-id="c276a-115">Sınıfında tanımlanan yöntemler numaralandırma sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="c276a-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="c276a-116">0x20</span><span class="sxs-lookup"><span data-stu-id="c276a-116">0x20</span></span> | <span data-ttu-id="c276a-117">Temel sınıflardan devralınır özellikler numaralandırma sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="c276a-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="c276a-118">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="c276a-118">Return value</span></span>

<span data-ttu-id="c276a-119">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="c276a-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c276a-120">Sabit</span><span class="sxs-lookup"><span data-stu-id="c276a-120">Constant</span></span>  |<span data-ttu-id="c276a-121">Değer</span><span class="sxs-lookup"><span data-stu-id="c276a-121">Value</span></span>  |<span data-ttu-id="c276a-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c276a-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c276a-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c276a-123">0x80041008</span></span> | <span data-ttu-id="c276a-124">`lEnnumFlags`sıfır olmayan ve belirtilen bayrakları biri değil.</span><span class="sxs-lookup"><span data-stu-id="c276a-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c276a-125">0</span><span class="sxs-lookup"><span data-stu-id="c276a-125">0</span></span> | <span data-ttu-id="c276a-126">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="c276a-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c276a-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c276a-127">Remarks</span></span>

<span data-ttu-id="c276a-128">Bu işlev çağrısı sarmalar [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c276a-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="c276a-129">Bu yöntem çağrısı, geçerli nesne bir sınıf tanımı ise yalnızca desteklenir.</span><span class="sxs-lookup"><span data-stu-id="c276a-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="c276a-130">Yöntem işleme kullanılabilir değil [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneklerine noktası işaretçileri.</span><span class="sxs-lookup"><span data-stu-id="c276a-130">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to instances.</span></span> <span data-ttu-id="c276a-131">Yöntemleri numaralandırılan sipariş belirli bir örneği için sabit olması garanti [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="c276a-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="c276a-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c276a-132">Requirements</span></span>  
 <span data-ttu-id="c276a-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c276a-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c276a-134">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c276a-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c276a-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c276a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c276a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c276a-136">See also</span></span>  
[<span data-ttu-id="c276a-137">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c276a-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
