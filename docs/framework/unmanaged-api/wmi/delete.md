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
ms.openlocfilehash: 6b8f287be831702dd31a8335f9b2f6447bcee540
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127661"
---
# <a name="delete-function"></a><span data-ttu-id="68aee-103">Delete işlevi</span><span class="sxs-lookup"><span data-stu-id="68aee-103">Delete function</span></span>

<span data-ttu-id="68aee-104">Belirtilen özelliği ve tüm niteleyicileri bir CıM sınıf tanımından siler.</span><span class="sxs-lookup"><span data-stu-id="68aee-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="68aee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68aee-105">Syntax</span></span>

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a><span data-ttu-id="68aee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68aee-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="68aee-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="68aee-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="68aee-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="68aee-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="68aee-109">'ndaki Silinecek özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="68aee-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="68aee-110">`wszName` geçerli bir `LPCWSTR`işaretçisi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="68aee-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="68aee-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="68aee-111">Return value</span></span>

<span data-ttu-id="68aee-112">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68aee-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="68aee-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="68aee-113">Constant</span></span>  |<span data-ttu-id="68aee-114">Değer</span><span class="sxs-lookup"><span data-stu-id="68aee-114">Value</span></span>  |<span data-ttu-id="68aee-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68aee-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="68aee-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="68aee-116">0x80041001</span></span> | <span data-ttu-id="68aee-117">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="68aee-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="68aee-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="68aee-118">0x80041016</span></span> | <span data-ttu-id="68aee-119">Özellik silinemiyor.</span><span class="sxs-lookup"><span data-stu-id="68aee-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="68aee-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="68aee-120">0x80041008</span></span> | <span data-ttu-id="68aee-121">`wszName` geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="68aee-121">`wszName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="68aee-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="68aee-122">0x80041002</span></span> | <span data-ttu-id="68aee-123">Belirtilen özellik yok.</span><span class="sxs-lookup"><span data-stu-id="68aee-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="68aee-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="68aee-124">0x80041006</span></span> | <span data-ttu-id="68aee-125">İşlemi tamamlamaya yetecek bellek yok.</span><span class="sxs-lookup"><span data-stu-id="68aee-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="68aee-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="68aee-126">0x8004101c</span></span> | <span data-ttu-id="68aee-127">Özelliği bir temel sınıftan devralınır.</span><span class="sxs-lookup"><span data-stu-id="68aee-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="68aee-128">Özelliği bir sistem özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="68aee-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="68aee-129">0</span><span class="sxs-lookup"><span data-stu-id="68aee-129">0</span></span> | <span data-ttu-id="68aee-130">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="68aee-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="68aee-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="68aee-131">0x80041030</span></span> | <span data-ttu-id="68aee-132">İşlev geçerli sınıf için geçersiz kılma varsayılan değerini sildi.</span><span class="sxs-lookup"><span data-stu-id="68aee-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="68aee-133">Üst sınıftaki bu özellik için varsayılan değer yeniden etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="68aee-133">The default value for this property in the parent class has been reactivated.</span></span> |

## <a name="remarks"></a><span data-ttu-id="68aee-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68aee-134">Remarks</span></span>

<span data-ttu-id="68aee-135">Bu işlev, [IWbemClassObject::D Sil](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="68aee-135">This function wraps a call to the [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="68aee-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68aee-136">Requirements</span></span>

<span data-ttu-id="68aee-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68aee-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="68aee-138">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="68aee-138">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="68aee-139">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="68aee-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="68aee-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68aee-140">See also</span></span>

- [<span data-ttu-id="68aee-141">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="68aee-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
