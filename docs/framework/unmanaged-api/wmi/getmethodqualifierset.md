---
title: GetMethodQualifierSet işlevi (yönetilmeyen API Başvurusu)
description: GetMethodQualifierSet işlevi, bir yöntemin niteleyicisi kümesini alır.
ms.date: 11/06/2017
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
ms.openlocfilehash: a363591f5db7a2dbcba1147df35d8c023c9b0707
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389048"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="fe850-103">GetMethodQualifierSet işlevi</span><span class="sxs-lookup"><span data-stu-id="fe850-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="fe850-104">Belirli bir yöntem için ayarlanmış niteleyicisi alır.</span><span class="sxs-lookup"><span data-stu-id="fe850-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="fe850-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe850-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="fe850-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe850-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="fe850-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="fe850-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="fe850-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="fe850-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`  
<span data-ttu-id="fe850-109">[in] Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="fe850-109">[in] The method  name.</span></span> <span data-ttu-id="fe850-110">`wszMethod` Geçerli bir işaret etmelidir `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="fe850-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="fe850-111">[out] Yöntemin niteleyicileri erişmesini sağlayan arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="fe850-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="fe850-112">`ppQualSet` olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="fe850-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="fe850-113">Bir hata meydana gelir yeni bir nesne değil döndürülür ve işaretçi, işaret edecek şekilde ayarlanır `null`.</span><span class="sxs-lookup"><span data-stu-id="fe850-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="fe850-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="fe850-114">Return value</span></span>

<span data-ttu-id="fe850-115">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="fe850-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fe850-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="fe850-116">Constant</span></span>  |<span data-ttu-id="fe850-117">Değer</span><span class="sxs-lookup"><span data-stu-id="fe850-117">Value</span></span>  |<span data-ttu-id="fe850-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe850-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="fe850-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="fe850-119">0x80041002</span></span> | <span data-ttu-id="fe850-120">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="fe850-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="fe850-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="fe850-121">0x80041008</span></span> | <span data-ttu-id="fe850-122">Bir parametre `null`.</span><span class="sxs-lookup"><span data-stu-id="fe850-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="fe850-123">0</span><span class="sxs-lookup"><span data-stu-id="fe850-123">0</span></span> | <span data-ttu-id="fe850-124">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="fe850-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="fe850-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe850-125">Remarks</span></span>

<span data-ttu-id="fe850-126">Bu işlev bir çağrı sarılır [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fe850-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span> 

<span data-ttu-id="fe850-127">Bu işlev çağrısı, yalnızca geçerli nesneye bir CIM sınıf tanımı ise desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fe850-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="fe850-128">Yöntem işleme için kullanılabilir değil [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) CIM örneklerine noktası ponters.</span><span class="sxs-lookup"><span data-stu-id="fe850-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters that point to CIM instances.</span></span>

<span data-ttu-id="fe850-129">Her yöntem kendi niteleyicileri olabileceğinden [IWbemQualifierSet işaretçi](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) eklemek, düzenlemek veya bu niteleyiciler silme çağıran olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fe850-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="fe850-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe850-130">Requirements</span></span>  
<span data-ttu-id="fe850-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe850-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe850-132">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fe850-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="fe850-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fe850-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe850-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe850-134">See also</span></span>  
[<span data-ttu-id="fe850-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fe850-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
