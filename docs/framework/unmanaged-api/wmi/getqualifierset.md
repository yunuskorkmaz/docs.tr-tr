---
title: GetQualifierSet işlevi (yönetilmeyen API Başvurusu)
description: GetQualifierSet işlevi, bir sınıf veya örnek için niteleyici kümesini alır.
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
ms.openlocfilehash: 845d5ea93a06859840c87c65b415ead0f846d538
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798469"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="8f1a7-103">GetQualifierSet işlevi</span><span class="sxs-lookup"><span data-stu-id="8f1a7-103">GetQualifierSet function</span></span>
<span data-ttu-id="8f1a7-104">Bir sınıf örneği veya sınıf tanımı için niteleyici kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="8f1a7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f1a7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="8f1a7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f1a7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8f1a7-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="8f1a7-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="8f1a7-109">dışı Sınıf nesnesinin niteleyicilerine erişime izin veren arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="8f1a7-110">`ppQualSet``null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="8f1a7-111">Bir hata oluşursa, yeni bir nesne döndürülmez ve işaretçi değiştirilmemiş olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span> 

## <a name="return-value"></a><span data-ttu-id="8f1a7-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="8f1a7-112">Return value</span></span>

<span data-ttu-id="8f1a7-113">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8f1a7-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8f1a7-114">Sabit</span><span class="sxs-lookup"><span data-stu-id="8f1a7-114">Constant</span></span>  |<span data-ttu-id="8f1a7-115">Değer</span><span class="sxs-lookup"><span data-stu-id="8f1a7-115">Value</span></span>  |<span data-ttu-id="8f1a7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f1a7-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="8f1a7-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8f1a7-117">0x80041001</span></span> | <span data-ttu-id="8f1a7-118">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="8f1a7-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="8f1a7-119">0x80041002</span></span> | <span data-ttu-id="8f1a7-120">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8f1a7-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8f1a7-121">0x80041006</span></span> | <span data-ttu-id="8f1a7-122">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8f1a7-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8f1a7-123">0x80041008</span></span> | <span data-ttu-id="8f1a7-124">Bir parametre `null`.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8f1a7-125">0</span><span class="sxs-lookup"><span data-stu-id="8f1a7-125">0</span></span> | <span data-ttu-id="8f1a7-126">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="8f1a7-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f1a7-127">Remarks</span></span>

<span data-ttu-id="8f1a7-128">Bu işlev, [IWbemClassObject:: GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span> 

<span data-ttu-id="8f1a7-129">[IWbemQualifierSet işaretçisi](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) , çağıranın bu niteleyicileri eklemesine, düzenlemesine veya silmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="8f1a7-130">Bu tür eklenmiş, düzenlenmiş veya silinen niteleyiciler, tüm örnek veya sınıf tanımı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="8f1a7-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f1a7-131">Requirements</span></span>  
<span data-ttu-id="8f1a7-132">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f1a7-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f1a7-133">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="8f1a7-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8f1a7-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8f1a7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f1a7-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f1a7-135">See also</span></span>

- [<span data-ttu-id="8f1a7-136">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8f1a7-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
