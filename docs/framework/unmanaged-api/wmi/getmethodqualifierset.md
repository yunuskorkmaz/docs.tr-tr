---
title: "GetMethodQualifierSet işlevi (yönetilmeyen API Başvurusu)"
description: "GetMethodQualifierSet işlevi bir yöntemin niteleyicisi kümesini alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- GetMethodQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodQualifierSet
helpviewer_keywords:
- GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2999bef31576cf2bc025868260c2b1782a9b69f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="98708-103">GetMethodQualifierSet işlevi</span><span class="sxs-lookup"><span data-stu-id="98708-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="98708-104">Belirli bir yöntem için ayarlanmış niteleyicisi alır.</span><span class="sxs-lookup"><span data-stu-id="98708-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="98708-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98708-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="98708-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98708-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="98708-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="98708-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="98708-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="98708-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="98708-109">[in] Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="98708-109">[in] The method  name.</span></span> <span data-ttu-id="98708-110">`wszMethod`Geçerli bir işaret etmelidir `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="98708-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="98708-111">[out] Yönteminin niteleyicileri erişmesini sağlayan arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="98708-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="98708-112">`ppQualSet`olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="98708-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="98708-113">Bir hata oluştuğunda yeni bir nesne değil döndürülür ve işaretçi işaret edecek şekilde ayarlanır `null`.</span><span class="sxs-lookup"><span data-stu-id="98708-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="98708-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="98708-114">Return value</span></span>

<span data-ttu-id="98708-115">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="98708-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="98708-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="98708-116">Constant</span></span>  |<span data-ttu-id="98708-117">Değer</span><span class="sxs-lookup"><span data-stu-id="98708-117">Value</span></span>  |<span data-ttu-id="98708-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98708-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="98708-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="98708-119">0x80041002</span></span> | <span data-ttu-id="98708-120">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="98708-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="98708-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="98708-121">0x80041008</span></span> | <span data-ttu-id="98708-122">Parametre `null`.</span><span class="sxs-lookup"><span data-stu-id="98708-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="98708-123">0</span><span class="sxs-lookup"><span data-stu-id="98708-123">0</span></span> | <span data-ttu-id="98708-124">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="98708-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="98708-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98708-125">Remarks</span></span>

<span data-ttu-id="98708-126">Bu işlev çağrısı sarmalar [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="98708-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](https://msdn.microsoft.com/library/aa391446(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="98708-127">Yalnızca geçerli nesne bir CIM sınıfı tanımı ise bu işlev için bir çağrı desteklenir.</span><span class="sxs-lookup"><span data-stu-id="98708-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="98708-128">Yöntem işleme için kullanılabilir olmadığından [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) CIM örneklerine noktası ponters.</span><span class="sxs-lookup"><span data-stu-id="98708-128">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="98708-129">Her yöntemin kendi niteleyicileri olabileceğinden [IWbemQualifierSet işaretçi](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) eklemek, düzenlemek veya silmek bu niteleyicileri çağıran olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="98708-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="98708-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98708-130">Requirements</span></span>  
<span data-ttu-id="98708-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98708-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98708-132">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="98708-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="98708-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="98708-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98708-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98708-134">See also</span></span>  
[<span data-ttu-id="98708-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="98708-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
