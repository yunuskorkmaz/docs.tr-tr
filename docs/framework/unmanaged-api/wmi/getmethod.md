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
ms.openlocfilehash: 48986f5ff1cbbb45840ec1a059aa86711848d717
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102585"
---
# <a name="getmethod-function"></a><span data-ttu-id="99fa7-103">GetMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="99fa7-103">GetMethod function</span></span>

<span data-ttu-id="99fa7-104">Belirtilen yöntem hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="99fa7-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="99fa7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99fa7-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="99fa7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99fa7-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="99fa7-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="99fa7-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="99fa7-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="99fa7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="99fa7-109">'ndaki Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="99fa7-109">[in] The method name.</span></span> <span data-ttu-id="99fa7-110">Bu parametre `null` olamaz ve geçerli bir `LPCWSTR`işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="99fa7-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`\
<span data-ttu-id="99fa7-111">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="99fa7-111">[in] Reserved.</span></span> <span data-ttu-id="99fa7-112">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="99fa7-112">This parameter must be 0.</span></span>

`ppInSignature`\
<span data-ttu-id="99fa7-113">dışı Yöntemine yönelik parametreleri açıklayan bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="99fa7-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in parameters to the method.</span></span> <span data-ttu-id="99fa7-114">Bu parametre `null`olarak ayarlandıysa yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="99fa7-114">This parameter is ignored if it is set to `null`.</span></span>

`ppOutSignature`\
<span data-ttu-id="99fa7-115">dışı Yönteme giden parametreleri açıklayan bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="99fa7-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="99fa7-116">Bu parametre `null`olarak ayarlandıysa yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="99fa7-116">This parameter is ignored if it is set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="99fa7-117">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="99fa7-117">Return value</span></span>

<span data-ttu-id="99fa7-118">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="99fa7-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="99fa7-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="99fa7-119">Constant</span></span>  |<span data-ttu-id="99fa7-120">Değer</span><span class="sxs-lookup"><span data-stu-id="99fa7-120">Value</span></span>  |<span data-ttu-id="99fa7-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99fa7-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="99fa7-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="99fa7-122">0x80041002</span></span> | <span data-ttu-id="99fa7-123">Belirtilen özellik bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="99fa7-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="99fa7-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="99fa7-124">0x80041006</span></span> | <span data-ttu-id="99fa7-125">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="99fa7-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="99fa7-126">0</span><span class="sxs-lookup"><span data-stu-id="99fa7-126">0</span></span> | <span data-ttu-id="99fa7-127">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="99fa7-127">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="99fa7-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99fa7-128">Remarks</span></span>

<span data-ttu-id="99fa7-129">Bu işlev, [IWbemClassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="99fa7-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="99fa7-130">Yöntemin parametrelere sahip olmaması halinde, Windows Yönetimi [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçisini `null` olarak ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="99fa7-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="99fa7-131">`ppInSignature` ve `ppOutSignature`, sistem sınıfı [_parametrelerinin](/windows/desktop/WmiSdk/--parameters)`IWbemClassObject` örneğindeki özellikler olarak sırasıyla gelen ve dışarı parametreleri anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99fa7-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="99fa7-132">`ppInSignature` özellikler, `Param`*n*olarak adlandırılır; burada *n* , yöntem imzasında parametrenin konumudur (`Param1`, `Param2`, vb.).</span><span class="sxs-lookup"><span data-stu-id="99fa7-132">The properties in `ppInSignature` are named `Param`*n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="99fa7-133">`ppOutSignature` özellikler de `Param`*n*olarak adlandırılır ve döndürülen değer `ReturnValue`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="99fa7-133">The properties in `ppOutSignature` are also named `Param`*n*, and the return value is named `ReturnValue`.</span></span> <span data-ttu-id="99fa7-134">Daha fazla bilgi ve örnek için bkz. [IWbemClassObject:: GetMethod metodu](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span><span class="sxs-lookup"><span data-stu-id="99fa7-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="99fa7-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99fa7-135">Requirements</span></span>

<span data-ttu-id="99fa7-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99fa7-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="99fa7-137">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="99fa7-137">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="99fa7-138">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="99fa7-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="99fa7-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99fa7-139">See also</span></span>

- [<span data-ttu-id="99fa7-140">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="99fa7-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
