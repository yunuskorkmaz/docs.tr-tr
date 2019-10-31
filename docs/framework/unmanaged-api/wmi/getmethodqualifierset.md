---
title: GetMethodQualifierSet işlevi (yönetilmeyen API Başvurusu)
description: GetMethodQualifierSet işlevi, bir yöntemin niteleyici kümesini alır.
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
ms.openlocfilehash: 1a36200fd214d013a10ed21c22e1f652de2cbf17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102569"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="60284-103">GetMethodQualifierSet işlevi</span><span class="sxs-lookup"><span data-stu-id="60284-103">GetMethodQualifierSet function</span></span>

<span data-ttu-id="60284-104">Belirli bir yöntem için niteleyici kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="60284-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="60284-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60284-105">Syntax</span></span>

```cpp
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="60284-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60284-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="60284-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="60284-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="60284-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="60284-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="60284-109">'ndaki Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="60284-109">[in] The method  name.</span></span> <span data-ttu-id="60284-110">`wszMethod` geçerli bir `LPCWSTR`işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="60284-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="60284-111">dışı Metodun niteleyicilerine erişime izin veren arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="60284-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="60284-112">`ppQualSet` `null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="60284-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="60284-113">Bir hata oluşursa, yeni bir nesne döndürülmez ve işaretçi `null`işaret etmek üzere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="60284-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="60284-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="60284-114">Return value</span></span>

<span data-ttu-id="60284-115">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60284-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="60284-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="60284-116">Constant</span></span>  |<span data-ttu-id="60284-117">Değer</span><span class="sxs-lookup"><span data-stu-id="60284-117">Value</span></span>  |<span data-ttu-id="60284-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60284-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="60284-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="60284-119">0x80041002</span></span> | <span data-ttu-id="60284-120">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="60284-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="60284-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="60284-121">0x80041008</span></span> | <span data-ttu-id="60284-122">Bir parametre `null`.</span><span class="sxs-lookup"><span data-stu-id="60284-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="60284-123">0</span><span class="sxs-lookup"><span data-stu-id="60284-123">0</span></span> | <span data-ttu-id="60284-124">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="60284-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="60284-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60284-125">Remarks</span></span>

<span data-ttu-id="60284-126">Bu işlev, [IWbemClassObject:: GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="60284-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span>

<span data-ttu-id="60284-127">Bu işleve yapılan çağrı yalnızca geçerli nesne bir CıM sınıf tanımınız ise desteklenir.</span><span class="sxs-lookup"><span data-stu-id="60284-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="60284-128">CıM örneklerine işaret eden [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçileri için yöntem düzenleme kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="60284-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="60284-129">Her yöntemin kendi niteleyicileri olabileceğinden, [IWbemQualifierSet işaretçisi](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) çağıranın bu niteleyicileri eklemesini, düzenlemesini veya silmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="60284-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="60284-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60284-130">Requirements</span></span>

<span data-ttu-id="60284-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60284-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="60284-132">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="60284-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="60284-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="60284-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="60284-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60284-134">See also</span></span>

- [<span data-ttu-id="60284-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="60284-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
