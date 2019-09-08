---
title: Delete işlevi (yönetilmeyen API Başvurusu)
description: Delete işlevi, belirtilen özelliği ve tüm niteleyicileri bir CıM sınıf tanımından siler.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1bf9bd5d93d1affee649588138456269411d280
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798675"
---
# <a name="delete-function"></a><span data-ttu-id="d3f6d-103">Delete işlevi</span><span class="sxs-lookup"><span data-stu-id="d3f6d-103">Delete function</span></span>

<span data-ttu-id="d3f6d-104">Belirtilen özelliği ve tüm niteleyicileri bir CıM sınıf tanımından siler.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="d3f6d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3f6d-105">Syntax</span></span>

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a><span data-ttu-id="d3f6d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3f6d-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="d3f6d-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="d3f6d-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="d3f6d-109">'ndaki Silinecek özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="d3f6d-110">`wszName`geçerli `LPCWSTR`bir işaretçi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="d3f6d-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d3f6d-111">Return value</span></span>

<span data-ttu-id="d3f6d-112">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d3f6d-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d3f6d-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="d3f6d-113">Constant</span></span>  |<span data-ttu-id="d3f6d-114">Değer</span><span class="sxs-lookup"><span data-stu-id="d3f6d-114">Value</span></span>  |<span data-ttu-id="d3f6d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3f6d-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="d3f6d-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="d3f6d-116">0x80041001</span></span> | <span data-ttu-id="d3f6d-117">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="d3f6d-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="d3f6d-118">0x80041016</span></span> | <span data-ttu-id="d3f6d-119">Özellik silinemiyor.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d3f6d-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d3f6d-120">0x80041008</span></span> | <span data-ttu-id="d3f6d-121">`wszName` geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-121">`wszName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="d3f6d-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="d3f6d-122">0x80041002</span></span> | <span data-ttu-id="d3f6d-123">Belirtilen özellik yok.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d3f6d-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d3f6d-124">0x80041006</span></span> | <span data-ttu-id="d3f6d-125">İşlemi tamamlamaya yetecek bellek yok.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="d3f6d-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="d3f6d-126">0x8004101c</span></span> | <span data-ttu-id="d3f6d-127">Özelliği bir temel sınıftan devralınır.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="d3f6d-128">Özelliği bir sistem özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d3f6d-129">0</span><span class="sxs-lookup"><span data-stu-id="d3f6d-129">0</span></span> | <span data-ttu-id="d3f6d-130">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="d3f6d-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="d3f6d-131">0x80041030</span></span> | <span data-ttu-id="d3f6d-132">İşlev geçerli sınıf için geçersiz kılma varsayılan değerini sildi.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="d3f6d-133">Üst sınıftaki bu özellik için varsayılan değer yeniden etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-133">The default value for this property in the parent class has been reactivated.</span></span> |

## <a name="remarks"></a><span data-ttu-id="d3f6d-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3f6d-134">Remarks</span></span>

<span data-ttu-id="d3f6d-135">Bu işlev, [IWbemClassObject::D Sil](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-135">This function wraps a call to the [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d3f6d-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3f6d-136">Requirements</span></span>

<span data-ttu-id="d3f6d-137">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3f6d-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="d3f6d-138">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="d3f6d-138">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="d3f6d-139">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d3f6d-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d3f6d-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3f6d-140">See also</span></span>

- [<span data-ttu-id="d3f6d-141">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d3f6d-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
