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
ms.openlocfilehash: 7f197851d4d7d470c6c34e4f5607e1791e724770
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681631"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="47254-103">GetMethodQualifierSet işlevi</span><span class="sxs-lookup"><span data-stu-id="47254-103">GetMethodQualifierSet function</span></span>
<span data-ttu-id="47254-104">Belirli bir yöntem için ayarlanmış niteleyicisi alır.</span><span class="sxs-lookup"><span data-stu-id="47254-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="47254-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47254-105">Syntax</span></span>  
  
```  
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="47254-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47254-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="47254-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="47254-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="47254-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="47254-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`  
<span data-ttu-id="47254-109">[in] Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="47254-109">[in] The method  name.</span></span> <span data-ttu-id="47254-110">`wszMethod` Geçerli bir işaret etmelidir `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="47254-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="47254-111">[out] Yöntemin niteleyicileri erişmesini sağlayan arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="47254-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="47254-112">`ppQualSet` olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="47254-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="47254-113">Bir hata meydana gelir yeni bir nesne değil döndürülür ve işaretçi, işaret edecek şekilde ayarlanır `null`.</span><span class="sxs-lookup"><span data-stu-id="47254-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="47254-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="47254-114">Return value</span></span>

<span data-ttu-id="47254-115">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="47254-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="47254-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="47254-116">Constant</span></span>  |<span data-ttu-id="47254-117">Değer</span><span class="sxs-lookup"><span data-stu-id="47254-117">Value</span></span>  |<span data-ttu-id="47254-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47254-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="47254-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="47254-119">0x80041002</span></span> | <span data-ttu-id="47254-120">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="47254-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="47254-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="47254-121">0x80041008</span></span> | <span data-ttu-id="47254-122">Bir parametre `null`.</span><span class="sxs-lookup"><span data-stu-id="47254-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="47254-123">0</span><span class="sxs-lookup"><span data-stu-id="47254-123">0</span></span> | <span data-ttu-id="47254-124">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="47254-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="47254-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47254-125">Remarks</span></span>

<span data-ttu-id="47254-126">Bu işlev bir çağrı sarılır [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="47254-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span> 

<span data-ttu-id="47254-127">Bu işlev çağrısı, yalnızca geçerli nesneye bir CIM sınıf tanımı ise desteklenir.</span><span class="sxs-lookup"><span data-stu-id="47254-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="47254-128">Yöntem işleme için kullanılabilir değil [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) CIM örneklerine noktası ponters.</span><span class="sxs-lookup"><span data-stu-id="47254-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponters that point to CIM instances.</span></span>

<span data-ttu-id="47254-129">Her yöntem kendi niteleyicileri olabileceğinden [IWbemQualifierSet işaretçi](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) eklemek, düzenlemek veya bu niteleyiciler silme çağıran olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="47254-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="47254-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47254-130">Requirements</span></span>  
<span data-ttu-id="47254-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47254-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47254-132">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="47254-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="47254-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="47254-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47254-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47254-134">See also</span></span>
- [<span data-ttu-id="47254-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="47254-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
