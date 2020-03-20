---
title: GetQualifierSet fonksiyonu (Yönetilmeyen API Başvurusu)
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
ms.openlocfilehash: 368f0a13871bd48780fa30b370d37157d2724bb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176779"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="5b2e2-103">GetQualifierSet fonksiyonu</span><span class="sxs-lookup"><span data-stu-id="5b2e2-103">GetQualifierSet function</span></span>
<span data-ttu-id="5b2e2-104">Bir sınıf örneği veya sınıf tanımı için niteleyici kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="5b2e2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b2e2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [out] IWbemQualifierSet  **ppQualSet
);
```  

## <a name="parameters"></a><span data-ttu-id="5b2e2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b2e2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5b2e2-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5b2e2-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="5b2e2-109">[çıkış] Sınıf nesnesinin niteleyicilerine erişim sağlayan arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="5b2e2-110">`ppQualSet`olamaz. `null`</span><span class="sxs-lookup"><span data-stu-id="5b2e2-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="5b2e2-111">Bir hata oluşursa, yeni bir nesne döndürülür ve işaretçi değiştirilmemiş olarak bırakılır.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="5b2e2-112">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="5b2e2-112">Return value</span></span>

<span data-ttu-id="5b2e2-113">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5b2e2-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5b2e2-114">Sabit</span><span class="sxs-lookup"><span data-stu-id="5b2e2-114">Constant</span></span>  |<span data-ttu-id="5b2e2-115">Değer</span><span class="sxs-lookup"><span data-stu-id="5b2e2-115">Value</span></span>  |<span data-ttu-id="5b2e2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b2e2-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="5b2e2-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5b2e2-117">0x80041001</span></span> | <span data-ttu-id="5b2e2-118">Genel bir başarısızlık oldu.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="5b2e2-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="5b2e2-119">0x80041002</span></span> | <span data-ttu-id="5b2e2-120">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5b2e2-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5b2e2-121">0x80041006</span></span> | <span data-ttu-id="5b2e2-122">İşlemi tamamlamak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5b2e2-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5b2e2-123">0x80041008</span></span> | <span data-ttu-id="5b2e2-124">Bir parametre. `null`</span><span class="sxs-lookup"><span data-stu-id="5b2e2-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5b2e2-125">0</span><span class="sxs-lookup"><span data-stu-id="5b2e2-125">0</span></span> | <span data-ttu-id="5b2e2-126">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5b2e2-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b2e2-127">Remarks</span></span>

<span data-ttu-id="5b2e2-128">Bu [işlev, IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span>

<span data-ttu-id="5b2e2-129">[IWbemQualifierSet işaretçisi,](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) arayanın bu elemeleri eklemesini, düzenlemesini veya silmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="5b2e2-130">Bu tür eklenen, düzenlenen veya silinen niteleyiciler tüm örnek veya sınıf tanımı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="5b2e2-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b2e2-131">Requirements</span></span>  
<span data-ttu-id="5b2e2-132">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b2e2-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b2e2-133">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5b2e2-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5b2e2-134">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5b2e2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b2e2-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b2e2-135">See also</span></span>

- [<span data-ttu-id="5b2e2-136">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5b2e2-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
