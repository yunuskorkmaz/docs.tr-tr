---
title: "GetPropertyHandle işlevi (yönetilmeyen API Başvurusu)"
description: "GetPropertyHandle işlevi bu identies bir özelliği bir benzersiz tanıtıcı döndürür."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyHandle
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyHandle
helpviewer_keywords: GetPropertyHandle function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ab3df6d2233059de76036da7ff27f5cc1808aaf
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="0502a-103">GetPropertyHandle işlevi</span><span class="sxs-lookup"><span data-stu-id="0502a-103">GetPropertyHandle function</span></span>
<span data-ttu-id="0502a-104">Bir özelliği tanımlayan benzersiz bir tanıtıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="0502a-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="0502a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0502a-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a><span data-ttu-id="0502a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0502a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0502a-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="0502a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0502a-108">[in] Bir işaretçi bir [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="0502a-108">[in] A pointer to an [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.</span></span>

`wszPropertyName`  
<span data-ttu-id="0502a-109">[in] Özellik adını içeren UTF16 kodlu characaters null ile sonlandırılmış dizisi.</span><span class="sxs-lookup"><span data-stu-id="0502a-109">[in] A null-terminated string of UTF16-encoded characaters that contains the property name.</span></span>   

`pType`  
<span data-ttu-id="0502a-110">[out] Bir işaretçi bir [ `CIMTYPE` ](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) özelliğinin CIM türünü temsil eden numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="0502a-110">[out] A pointer to a [`CIMTYPE`](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`   
<span data-ttu-id="0502a-111">[out] Özellik işleyicisi içeren bir tamsayı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0502a-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="0502a-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="0502a-112">Return value</span></span>

<span data-ttu-id="0502a-113">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="0502a-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0502a-114">Sabit</span><span class="sxs-lookup"><span data-stu-id="0502a-114">Constant</span></span>  |<span data-ttu-id="0502a-115">Değer</span><span class="sxs-lookup"><span data-stu-id="0502a-115">Value</span></span>  |<span data-ttu-id="0502a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0502a-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="0502a-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="0502a-117">0x80041002</span></span> | <span data-ttu-id="0502a-118">Belirtilen özellik adı bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="0502a-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0502a-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0502a-119">0x80041008</span></span> | <span data-ttu-id="0502a-120">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="0502a-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="0502a-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="0502a-121">0x8004100c</span></span> | <span data-ttu-id="0502a-122">İstenen özellik türünde olan `CIM_OBJECT` veya `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="0502a-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0502a-123">0</span><span class="sxs-lookup"><span data-stu-id="0502a-123">0</span></span> | <span data-ttu-id="0502a-124">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="0502a-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0502a-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0502a-125">Remarks</span></span>

<span data-ttu-id="0502a-126">Bu işlev çağrısı sarmalar [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0502a-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="0502a-127">Bu işleyici kullanırken özelliklerini tanımlamak için kullanabileceğiniz [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) özellik değerlerini okumak veya yazmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="0502a-127">You can use this handle to identify properties when using  [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) methods to read or write property values.</span></span>

<span data-ttu-id="0502a-128">Tanıtıcıları alınabilir tüm veri türlerinin özelliklerini dışında `CIM_OBJECT` ve `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="0502a-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="0502a-129">İşler iş bir sınıfın tüm örneklerini döndürdü.</span><span class="sxs-lookup"><span data-stu-id="0502a-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="0502a-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0502a-130">Requirements</span></span>  
<span data-ttu-id="0502a-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0502a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0502a-132">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0502a-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0502a-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0502a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0502a-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0502a-134">See also</span></span>  
[<span data-ttu-id="0502a-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0502a-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
