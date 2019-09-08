---
title: GetMethod işlevi (yönetilmeyen API Başvurusu)
description: GetMethod işlevi bir yöntem hakkında bilgi alır.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9cc185bf8cccb8ed3c24e28954afd86464602d7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798573"
---
# <a name="getmethod-function"></a><span data-ttu-id="db810-103">GetMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="db810-103">GetMethod function</span></span>

<span data-ttu-id="db810-104">Belirtilen yöntem hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="db810-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="db810-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db810-105">Syntax</span></span>

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a><span data-ttu-id="db810-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db810-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="db810-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="db810-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="db810-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db810-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="db810-109">'ndaki Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="db810-109">[in] The method name.</span></span> <span data-ttu-id="db810-110">Bu parametre geçerli olamaz `null` ve geçerli `LPCWSTR`bir işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="db810-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`\
<span data-ttu-id="db810-111">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="db810-111">[in] Reserved.</span></span> <span data-ttu-id="db810-112">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db810-112">This parameter must be 0.</span></span>

`ppInSignature`\
<span data-ttu-id="db810-113">dışı Yöntemine yönelik parametreleri açıklayan bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db810-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in parameters to the method.</span></span> <span data-ttu-id="db810-114">Bu parametre, olarak `null`ayarlandıysa yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="db810-114">This parameter is ignored if it is set to `null`.</span></span>

`ppOutSignature`\
<span data-ttu-id="db810-115">dışı Yönteme giden parametreleri açıklayan bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db810-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="db810-116">Bu parametre, olarak `null`ayarlandıysa yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="db810-116">This parameter is ignored if it is set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="db810-117">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="db810-117">Return value</span></span>

<span data-ttu-id="db810-118">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="db810-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="db810-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="db810-119">Constant</span></span>  |<span data-ttu-id="db810-120">Değer</span><span class="sxs-lookup"><span data-stu-id="db810-120">Value</span></span>  |<span data-ttu-id="db810-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db810-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="db810-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="db810-122">0x80041002</span></span> | <span data-ttu-id="db810-123">Belirtilen özellik bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="db810-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="db810-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="db810-124">0x80041006</span></span> | <span data-ttu-id="db810-125">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="db810-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="db810-126">0</span><span class="sxs-lookup"><span data-stu-id="db810-126">0</span></span> | <span data-ttu-id="db810-127">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="db810-127">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="db810-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db810-128">Remarks</span></span>

<span data-ttu-id="db810-129">Bu işlev, [IWbemClassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="db810-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="db810-130">Windows yönetimi, metotta parametre yoksa, [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçisini `null` ' a ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="db810-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="db810-131">`IWbemClassObject` Ve `ppInSignature` '`ppOutSignature` de, bir sistem sınıfı [_parametreleri](/windows/desktop/WmiSdk/--parameters)örneğindeki özellikler olarak sırasıyla ve içinde ve dışarı parametreleri açıklama.</span><span class="sxs-lookup"><span data-stu-id="db810-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="db810-132">`ppInSignature` İçindeki Özellikler *n*olarak adlandırılır `Param`; burada *n* , yöntem imzasında `Param1` `Param2`parametre konumudur (örneğin, vb.).</span><span class="sxs-lookup"><span data-stu-id="db810-132">The properties in `ppInSignature` are named `Param`*n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="db810-133">İçindeki `ppOutSignature` özellikler de n olarak adlandırılır `Param`ve dönüş değeri olarak adlandırılır. `ReturnValue`</span><span class="sxs-lookup"><span data-stu-id="db810-133">The properties in `ppOutSignature` are also named `Param`*n*, and the return value is named `ReturnValue`.</span></span> <span data-ttu-id="db810-134">Daha fazla bilgi ve örnek için bkz. [IWbemClassObject:: GetMethod metodu](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span><span class="sxs-lookup"><span data-stu-id="db810-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="db810-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db810-135">Requirements</span></span>

<span data-ttu-id="db810-136">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db810-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="db810-137">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="db810-137">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="db810-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="db810-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="db810-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db810-139">See also</span></span>

- [<span data-ttu-id="db810-140">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="db810-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
