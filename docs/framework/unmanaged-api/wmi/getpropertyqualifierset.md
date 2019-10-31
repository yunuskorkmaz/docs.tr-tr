---
title: GetPropertyQualifierSet işlevi (yönetilmeyen API Başvurusu)
description: GetPropertyQualifierSet işlevi, bir özelliğin niteleyici kümesini alır.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4133145c7bea1fb3c018d809b9fea3de38270619
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127450"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="e6c34-103">GetPropertyQualifierSet işlevi</span><span class="sxs-lookup"><span data-stu-id="e6c34-103">GetPropertyQualifierSet function</span></span>

<span data-ttu-id="e6c34-104">Belirli bir özellik için niteleyici kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="e6c34-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e6c34-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6c34-105">Syntax</span></span>

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="e6c34-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6c34-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="e6c34-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e6c34-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="e6c34-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6c34-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="e6c34-109">'ndaki Özellik adı.</span><span class="sxs-lookup"><span data-stu-id="e6c34-109">[in] The property  name.</span></span> <span data-ttu-id="e6c34-110">`wszProperty` geçerli bir `LPCWSTR`işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="e6c34-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="e6c34-111">dışı Özelliğin niteleyicilerine erişim sağlayan arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="e6c34-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="e6c34-112">`ppQualSet` `null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="e6c34-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="e6c34-113">Bir hata oluşursa, yeni bir nesne döndürülmez ve işaretçi `null`işaret etmek üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e6c34-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="e6c34-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e6c34-114">Return value</span></span>

<span data-ttu-id="e6c34-115">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e6c34-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e6c34-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="e6c34-116">Constant</span></span>  |<span data-ttu-id="e6c34-117">Değer</span><span class="sxs-lookup"><span data-stu-id="e6c34-117">Value</span></span>  |<span data-ttu-id="e6c34-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6c34-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e6c34-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e6c34-119">0x80041001</span></span> | <span data-ttu-id="e6c34-120">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e6c34-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="e6c34-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e6c34-121">0x80041002</span></span> | <span data-ttu-id="e6c34-122">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="e6c34-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e6c34-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e6c34-123">0x80041006</span></span> | <span data-ttu-id="e6c34-124">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="e6c34-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e6c34-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e6c34-125">0x80041008</span></span> | <span data-ttu-id="e6c34-126">Bir parametre `null`.</span><span class="sxs-lookup"><span data-stu-id="e6c34-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="e6c34-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="e6c34-127">0x80041030</span></span> | <span data-ttu-id="e6c34-128">İşlev bir sistem özelliğinin niteleyicilerini almaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="e6c34-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e6c34-129">0</span><span class="sxs-lookup"><span data-stu-id="e6c34-129">0</span></span> | <span data-ttu-id="e6c34-130">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="e6c34-130">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="e6c34-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6c34-131">Remarks</span></span>

<span data-ttu-id="e6c34-132">Bu işlev, [IWbemClassObject:: GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="e6c34-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span>

<span data-ttu-id="e6c34-133">Bu işleve yapılan çağrı yalnızca geçerli nesne bir CıM sınıf tanımınız ise desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e6c34-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="e6c34-134">CıM örneklerine işaret eden [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçileri için yöntem düzenleme kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e6c34-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="e6c34-135">Her yöntemin kendi niteleyicileri olabileceğinden, [IWbemQualifierSet işaretçisi](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) çağıranın bu niteleyicileri eklemesini, düzenlemesini veya silmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e6c34-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="e6c34-136">Sistem Özellikleri niteleyicisi olmadığından, bir sistem özelliği için bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) işaretçisi edinmeye çalışırsanız işlev `WBEM_E_SYSTEM_PROPERTY` döndürür.</span><span class="sxs-lookup"><span data-stu-id="e6c34-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6c34-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6c34-137">Requirements</span></span>

<span data-ttu-id="e6c34-138">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6c34-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="e6c34-139">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="e6c34-139">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="e6c34-140">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e6c34-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e6c34-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6c34-141">See also</span></span>

- [<span data-ttu-id="e6c34-142">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e6c34-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
