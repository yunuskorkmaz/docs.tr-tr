---
title: "GetQualifierSet işlevi (yönetilmeyen API Başvurusu)"
description: "GetQualifierSet işlevi bir sınıf veya örnek için ayarlanmış niteleyicisi alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 127e7862d0cb0d204e91cd5ee36f2d32f1453a8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getqualifierset-function"></a><span data-ttu-id="26129-103">GetQualifierSet işlevi</span><span class="sxs-lookup"><span data-stu-id="26129-103">GetQualifierSet function</span></span>
<span data-ttu-id="26129-104">Sınıf örneği veya bir sınıf tanımı için ayarlamak niteleyicisi alır.</span><span class="sxs-lookup"><span data-stu-id="26129-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="26129-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26129-105">Syntax</span></span>  
  
```  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="26129-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26129-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="26129-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="26129-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="26129-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="26129-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="26129-109">[out] Sınıf nesnesi niteleyicileri erişime arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="26129-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="26129-110">`ppQualSet`olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="26129-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="26129-111">Bir hata oluşursa, yeni bir nesne değil döndürülür ve işaretçiyi sol değiştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="26129-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span> 

## <a name="return-value"></a><span data-ttu-id="26129-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="26129-112">Return value</span></span>

<span data-ttu-id="26129-113">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="26129-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="26129-114">Sabit</span><span class="sxs-lookup"><span data-stu-id="26129-114">Constant</span></span>  |<span data-ttu-id="26129-115">Değer</span><span class="sxs-lookup"><span data-stu-id="26129-115">Value</span></span>  |<span data-ttu-id="26129-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26129-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="26129-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="26129-117">0x80041001</span></span> | <span data-ttu-id="26129-118">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="26129-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="26129-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="26129-119">0x80041002</span></span> | <span data-ttu-id="26129-120">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="26129-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="26129-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="26129-121">0x80041006</span></span> | <span data-ttu-id="26129-122">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="26129-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="26129-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="26129-123">0x80041008</span></span> | <span data-ttu-id="26129-124">Parametre `null`.</span><span class="sxs-lookup"><span data-stu-id="26129-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="26129-125">0</span><span class="sxs-lookup"><span data-stu-id="26129-125">0</span></span> | <span data-ttu-id="26129-126">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="26129-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="26129-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26129-127">Remarks</span></span>

<span data-ttu-id="26129-128">Bu işlev çağrısı sarmalar [IWbemClassObject::GetQualifierSet](https://msdn.microsoft.com/library/aa391451(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="26129-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](https://msdn.microsoft.com/library/aa391451(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="26129-129">[IWbemQualifierSet işaretçi](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) eklemek, düzenlemek veya silmek bu niteleyicileri çağıran olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="26129-129">The [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="26129-130">Bu tür eklenen, düzenlenen veya silinen niteleyicileri tüm örneği veya sınıf tanımını uygulayın.</span><span class="sxs-lookup"><span data-stu-id="26129-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="26129-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26129-131">Requirements</span></span>  
<span data-ttu-id="26129-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26129-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26129-133">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="26129-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="26129-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="26129-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26129-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26129-135">See also</span></span>  
[<span data-ttu-id="26129-136">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="26129-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
