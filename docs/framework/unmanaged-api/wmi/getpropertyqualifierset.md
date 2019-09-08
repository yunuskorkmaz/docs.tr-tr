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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7bce241d10051e4c6be94cdfa40de23773fb0bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798477"
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="a7c76-103">GetPropertyQualifierSet işlevi</span><span class="sxs-lookup"><span data-stu-id="a7c76-103">GetPropertyQualifierSet function</span></span>

<span data-ttu-id="a7c76-104">Belirli bir özellik için niteleyici kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="a7c76-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a7c76-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7c76-105">Syntax</span></span>

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="a7c76-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7c76-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="a7c76-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a7c76-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="a7c76-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a7c76-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="a7c76-109">'ndaki Özellik adı.</span><span class="sxs-lookup"><span data-stu-id="a7c76-109">[in] The property  name.</span></span> <span data-ttu-id="a7c76-110">`wszProperty`geçerli `LPCWSTR`bir işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="a7c76-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="a7c76-111">dışı Özelliğin niteleyicilerine erişim sağlayan arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="a7c76-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="a7c76-112">`ppQualSet``null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="a7c76-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="a7c76-113">Bir hata oluşursa, yeni bir nesne döndürülmez ve işaretçi öğesine `null`işaret etmek üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a7c76-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="a7c76-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="a7c76-114">Return value</span></span>

<span data-ttu-id="a7c76-115">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a7c76-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a7c76-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="a7c76-116">Constant</span></span>  |<span data-ttu-id="a7c76-117">Değer</span><span class="sxs-lookup"><span data-stu-id="a7c76-117">Value</span></span>  |<span data-ttu-id="a7c76-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7c76-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="a7c76-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a7c76-119">0x80041001</span></span> | <span data-ttu-id="a7c76-120">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a7c76-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="a7c76-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a7c76-121">0x80041002</span></span> | <span data-ttu-id="a7c76-122">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="a7c76-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a7c76-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a7c76-123">0x80041006</span></span> | <span data-ttu-id="a7c76-124">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="a7c76-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a7c76-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a7c76-125">0x80041008</span></span> | <span data-ttu-id="a7c76-126">Bir parametre `null`.</span><span class="sxs-lookup"><span data-stu-id="a7c76-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="a7c76-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="a7c76-127">0x80041030</span></span> | <span data-ttu-id="a7c76-128">İşlev bir sistem özelliğinin niteleyicilerini almaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="a7c76-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a7c76-129">0</span><span class="sxs-lookup"><span data-stu-id="a7c76-129">0</span></span> | <span data-ttu-id="a7c76-130">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="a7c76-130">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="a7c76-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7c76-131">Remarks</span></span>

<span data-ttu-id="a7c76-132">Bu işlev, [IWbemClassObject:: GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="a7c76-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) method.</span></span>

<span data-ttu-id="a7c76-133">Bu işleve yapılan çağrı yalnızca geçerli nesne bir CıM sınıf tanımınız ise desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a7c76-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="a7c76-134">CıM örneklerine işaret eden [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçileri için yöntem düzenleme kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a7c76-134">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="a7c76-135">Her yöntemin kendi niteleyicileri olabileceğinden, [IWbemQualifierSet işaretçisi](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) çağıranın bu niteleyicileri eklemesini, düzenlemesini veya silmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="a7c76-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="a7c76-136">Sistem Özellikleri niteleyicisi olmadığından, bir sistem özelliği için bir `WBEM_E_SYSTEM_PROPERTY` [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) işaretçisi elde etmeye çalışırsanız işlev döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7c76-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="a7c76-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7c76-137">Requirements</span></span>

<span data-ttu-id="a7c76-138">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7c76-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a7c76-139">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="a7c76-139">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="a7c76-140">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a7c76-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a7c76-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7c76-141">See also</span></span>

- [<span data-ttu-id="a7c76-142">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a7c76-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
