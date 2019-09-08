---
title: GetPropertyOrigin işlevi (yönetilmeyen API Başvurusu)
description: GetPropertyOrigin işlevi, bir özelliğin bildirildiği sınıfı belirler.
ms.date: 11/06/2017
api_name:
- GetPropertyOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyOrigin
helpviewer_keywords:
- GetPropertyOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c2d0f23f3dd2d52f73f09c32d4e3118a9ed5ea3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798486"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="eb4e9-103">GetPropertyOrigin işlevi</span><span class="sxs-lookup"><span data-stu-id="eb4e9-103">GetPropertyOrigin function</span></span>

<span data-ttu-id="eb4e9-104">Özelliğin bildirildiği sınıfı belirler.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="eb4e9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb4e9-105">Syntax</span></span>

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a><span data-ttu-id="eb4e9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb4e9-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="eb4e9-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="eb4e9-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`\
<span data-ttu-id="eb4e9-109">'ndaki Sahibi olan sınıfı istenen nesnenin özelliğinin adı.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-109">[in] The name of the property for the object whose owning class is being requested.</span></span>

`pstrClassName`\
<span data-ttu-id="eb4e9-110">dışı Özelliğin sahibi olan sınıfın adını alır.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="eb4e9-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="eb4e9-111">Return value</span></span>

<span data-ttu-id="eb4e9-112">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb4e9-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="eb4e9-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="eb4e9-113">Constant</span></span>  |<span data-ttu-id="eb4e9-114">Değer</span><span class="sxs-lookup"><span data-stu-id="eb4e9-114">Value</span></span>  |<span data-ttu-id="eb4e9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb4e9-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="eb4e9-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="eb4e9-116">0x80041001</span></span> | <span data-ttu-id="eb4e9-117">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="eb4e9-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="eb4e9-118">0x80041002</span></span> | <span data-ttu-id="eb4e9-119">Belirtilen özellik bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="eb4e9-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="eb4e9-120">0x80041008</span></span> | <span data-ttu-id="eb4e9-121">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="eb4e9-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="eb4e9-122">0x80041006</span></span> | <span data-ttu-id="eb4e9-123">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="eb4e9-124">0</span><span class="sxs-lookup"><span data-stu-id="eb4e9-124">0</span></span> | <span data-ttu-id="eb4e9-125">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-125">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="eb4e9-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb4e9-126">Remarks</span></span>

<span data-ttu-id="eb4e9-127">Bu işlev, [IWbemClassObject:: GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) metoduna bir çağrıyı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="eb4e9-128">Bir sınıf bir veya daha fazla taban sınıftan özellikleri devralmasını sağladığından, geliştiriciler genellikle belirli bir yöntemin tanımlandığı özelliği belirlemede tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="eb4e9-129">`pstrClassName` Parametresi `BSTR` bir parametre`out` olduğundan, işlev çağrılmadan önce geçerli bir işaret içermemelidir; Bu işaretçi, işlev çağrıldıktan sonra serbest bırakılmaz.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb4e9-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb4e9-130">Requirements</span></span>

<span data-ttu-id="eb4e9-131">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb4e9-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="eb4e9-132">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="eb4e9-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="eb4e9-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eb4e9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="eb4e9-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb4e9-134">See also</span></span>

- [<span data-ttu-id="eb4e9-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="eb4e9-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
