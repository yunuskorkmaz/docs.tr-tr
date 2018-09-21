---
title: GetQualifierSet işlevi (yönetilmeyen API Başvurusu)
description: Bir sınıf veya örnek için ayarlanmış niteleyicisi GetQualifierSet işlevi alır.
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 635dc7605af00f2662a9f9553adefafcd25f9452
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46488863"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="1257d-103">GetQualifierSet işlevi</span><span class="sxs-lookup"><span data-stu-id="1257d-103">GetQualifierSet function</span></span>
<span data-ttu-id="1257d-104">Bir sınıf örneği veya bir sınıf tanımı için ayarlanmış niteleyicisi alır.</span><span class="sxs-lookup"><span data-stu-id="1257d-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="1257d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1257d-105">Syntax</span></span>  
  
```  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="1257d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1257d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="1257d-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="1257d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="1257d-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="1257d-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="1257d-109">[out] Niteleyiciler sınıf nesnesi erişimi sağlayan bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="1257d-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="1257d-110">`ppQualSet` olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="1257d-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="1257d-111">Bir hata gerçekleşirse, yeni bir nesne döndürülmez ve işaretçi solda değiştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="1257d-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span> 

## <a name="return-value"></a><span data-ttu-id="1257d-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="1257d-112">Return value</span></span>

<span data-ttu-id="1257d-113">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="1257d-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1257d-114">Sabit</span><span class="sxs-lookup"><span data-stu-id="1257d-114">Constant</span></span>  |<span data-ttu-id="1257d-115">Değer</span><span class="sxs-lookup"><span data-stu-id="1257d-115">Value</span></span>  |<span data-ttu-id="1257d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1257d-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="1257d-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="1257d-117">0x80041001</span></span> | <span data-ttu-id="1257d-118">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1257d-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="1257d-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="1257d-119">0x80041002</span></span> | <span data-ttu-id="1257d-120">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="1257d-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="1257d-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="1257d-121">0x80041006</span></span> | <span data-ttu-id="1257d-122">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="1257d-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1257d-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1257d-123">0x80041008</span></span> | <span data-ttu-id="1257d-124">Bir parametre `null`.</span><span class="sxs-lookup"><span data-stu-id="1257d-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1257d-125">0</span><span class="sxs-lookup"><span data-stu-id="1257d-125">0</span></span> | <span data-ttu-id="1257d-126">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="1257d-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1257d-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1257d-127">Remarks</span></span>

<span data-ttu-id="1257d-128">Bu işlev bir çağrı sarılır [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1257d-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span> 

<span data-ttu-id="1257d-129">[IWbemQualifierSet işaretçi](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) eklemek, düzenlemek veya bu niteleyiciler silme çağıran olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1257d-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="1257d-130">Tüm örnek veya sınıf tanımına eklenen, düzenlenen veya silinen tür niteleyicileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1257d-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="1257d-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1257d-131">Requirements</span></span>  
<span data-ttu-id="1257d-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1257d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1257d-133">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1257d-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1257d-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1257d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1257d-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1257d-135">See also</span></span>  
[<span data-ttu-id="1257d-136">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1257d-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
