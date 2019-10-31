---
title: GetPropertyHandle işlevi (yönetilmeyen API Başvurusu)
description: GetPropertyHandle işlevi bir özelliği tanımlayan benzersiz bir tanıtıcı döndürür.
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5af003f0295e0b403727f9af6b03ab81c4b8bccb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101867"
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="1b0b7-103">GetPropertyHandle işlevi</span><span class="sxs-lookup"><span data-stu-id="1b0b7-103">GetPropertyHandle function</span></span>

<span data-ttu-id="1b0b7-104">Bir özelliği tanımlayan benzersiz bir tanıtıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1b0b7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b0b7-105">Syntax</span></span>

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a><span data-ttu-id="1b0b7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b0b7-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="1b0b7-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="1b0b7-108">'ndaki Bir [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`wszPropertyName`\
<span data-ttu-id="1b0b7-109">'ndaki Özellik adını içeren UTF16 kodlu karakterlerin null ile sonlandırılmış dizesi.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-109">[in] A null-terminated string of UTF16-encoded characters that contains the property name.</span></span>

`pType`\
<span data-ttu-id="1b0b7-110">dışı Özelliğin CıM türünü temsil eden [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) numaralandırma üyesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-110">[out] A pointer to a [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`\
<span data-ttu-id="1b0b7-111">dışı Özellik tanıtıcısını içeren tamsayıya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="1b0b7-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="1b0b7-112">Return value</span></span>

<span data-ttu-id="1b0b7-113">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b0b7-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1b0b7-114">Sabit</span><span class="sxs-lookup"><span data-stu-id="1b0b7-114">Constant</span></span>  |<span data-ttu-id="1b0b7-115">Değer</span><span class="sxs-lookup"><span data-stu-id="1b0b7-115">Value</span></span>  |<span data-ttu-id="1b0b7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b0b7-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="1b0b7-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="1b0b7-117">0x80041002</span></span> | <span data-ttu-id="1b0b7-118">Belirtilen özellik adı bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1b0b7-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1b0b7-119">0x80041008</span></span> | <span data-ttu-id="1b0b7-120">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="1b0b7-121">0x8004100C</span><span class="sxs-lookup"><span data-stu-id="1b0b7-121">0x8004100c</span></span> | <span data-ttu-id="1b0b7-122">İstenen özellik `CIM_OBJECT` veya `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1b0b7-123">0</span><span class="sxs-lookup"><span data-stu-id="1b0b7-123">0</span></span> | <span data-ttu-id="1b0b7-124">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="1b0b7-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b0b7-125">Remarks</span></span>

<span data-ttu-id="1b0b7-126">Bu işlev, [IWbemClassObject:: GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) method.</span></span>

<span data-ttu-id="1b0b7-127">Bu tanıtıcıyı, özellik değerlerini okumak veya yazmak için [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) yöntemlerini kullanırken özellikleri tanımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-127">You can use this handle to identify properties when using  [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) methods to read or write property values.</span></span>

<span data-ttu-id="1b0b7-128">İşleyiciler, `CIM_OBJECT` ve `CIM_ARRAY`dışındaki tüm veri türlerinin özellikleri için alınabilir.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="1b0b7-129">Döndürülen tutamaçlar bir sınıfın tüm örneklerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b0b7-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b0b7-130">Requirements</span></span>

<span data-ttu-id="1b0b7-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b0b7-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1b0b7-132">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="1b0b7-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="1b0b7-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1b0b7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1b0b7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b0b7-134">See also</span></span>

- [<span data-ttu-id="1b0b7-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1b0b7-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
