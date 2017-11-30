---
title: "GetMethodQualifierSet işlevi (yönetilmeyen API Başvurusu)"
description: "GetMethodQualifierSet işlevi bir yöntemin niteleyicisi kümesini alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetMethodQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetMethodQualifierSet
helpviewer_keywords: GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79a19d3bb40dd4d435bd7cf97eb0b4071020648e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="28b24-103">GetMethodQualifierSet işlevi</span><span class="sxs-lookup"><span data-stu-id="28b24-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="28b24-104">Belirli bir yöntem için ayarlanmış niteleyicisi alır.</span><span class="sxs-lookup"><span data-stu-id="28b24-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="28b24-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28b24-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="28b24-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28b24-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="28b24-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="28b24-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="28b24-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="28b24-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="28b24-109">[in] Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="28b24-109">[in] The method  name.</span></span> <span data-ttu-id="28b24-110">`wszMethod`Geçerli bir işaret etmelidir `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="28b24-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="28b24-111">[out] Yönteminin niteleyicileri erişmesini sağlayan arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="28b24-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="28b24-112">`ppQualSet`olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="28b24-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="28b24-113">Bir hata oluştuğunda yeni bir nesne değil döndürülür ve işaretçi işaret edecek şekilde ayarlanır `null`.</span><span class="sxs-lookup"><span data-stu-id="28b24-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="28b24-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="28b24-114">Return value</span></span>

<span data-ttu-id="28b24-115">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="28b24-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="28b24-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="28b24-116">Constant</span></span>  |<span data-ttu-id="28b24-117">Değer</span><span class="sxs-lookup"><span data-stu-id="28b24-117">Value</span></span>  |<span data-ttu-id="28b24-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28b24-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="28b24-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="28b24-119">0x80041002</span></span> | <span data-ttu-id="28b24-120">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="28b24-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="28b24-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="28b24-121">0x80041008</span></span> | <span data-ttu-id="28b24-122">Parametre `null`.</span><span class="sxs-lookup"><span data-stu-id="28b24-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="28b24-123">0</span><span class="sxs-lookup"><span data-stu-id="28b24-123">0</span></span> | <span data-ttu-id="28b24-124">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="28b24-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="28b24-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28b24-125">Remarks</span></span>

<span data-ttu-id="28b24-126">Bu işlev çağrısı sarmalar [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="28b24-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="28b24-127">Yalnızca geçerli nesne bir CIM sınıfı tanımı ise bu işlev için bir çağrı desteklenir.</span><span class="sxs-lookup"><span data-stu-id="28b24-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="28b24-128">Yöntem işleme için kullanılabilir olmadığından [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) CIM örneklerine noktası ponters.</span><span class="sxs-lookup"><span data-stu-id="28b24-128">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="28b24-129">Her yöntemin kendi niteleyicileri olabileceğinden [IWbemQualifierSet işaretçi](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) eklemek, düzenlemek veya silmek bu niteleyicileri çağıran olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="28b24-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="28b24-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28b24-130">Requirements</span></span>  
<span data-ttu-id="28b24-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28b24-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28b24-132">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="28b24-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="28b24-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="28b24-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b24-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28b24-134">See also</span></span>  
[<span data-ttu-id="28b24-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="28b24-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
