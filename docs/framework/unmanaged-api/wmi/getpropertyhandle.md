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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6dc2792b572aae30e9989c81967b86f340d7b83
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038254"
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="ac136-103">GetPropertyHandle işlevi</span><span class="sxs-lookup"><span data-stu-id="ac136-103">GetPropertyHandle function</span></span>

<span data-ttu-id="ac136-104">Bir özelliği tanımlayan benzersiz bir tanıtıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac136-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ac136-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac136-105">Syntax</span></span>

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a><span data-ttu-id="ac136-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac136-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="ac136-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ac136-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="ac136-108">'ndaki Bir [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ac136-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`wszPropertyName`\
<span data-ttu-id="ac136-109">'ndaki Özellik adını içeren UTF16 kodlu karakterlerin null ile sonlandırılmış dizesi.</span><span class="sxs-lookup"><span data-stu-id="ac136-109">[in] A null-terminated string of UTF16-encoded characters that contains the property name.</span></span>

`pType`\
<span data-ttu-id="ac136-110">dışı Özelliğin CIM türünü temsil [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) eden bir numaralandırma üyesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac136-110">[out] A pointer to a [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`\
<span data-ttu-id="ac136-111">dışı Özellik tanıtıcısını içeren tamsayıya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac136-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="ac136-112">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="ac136-112">Return value</span></span>

<span data-ttu-id="ac136-113">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ac136-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ac136-114">Sabit</span><span class="sxs-lookup"><span data-stu-id="ac136-114">Constant</span></span>  |<span data-ttu-id="ac136-115">Değer</span><span class="sxs-lookup"><span data-stu-id="ac136-115">Value</span></span>  |<span data-ttu-id="ac136-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac136-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="ac136-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="ac136-117">0x80041002</span></span> | <span data-ttu-id="ac136-118">Belirtilen özellik adı bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="ac136-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ac136-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ac136-119">0x80041008</span></span> | <span data-ttu-id="ac136-120">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="ac136-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="ac136-121">0x8004100C</span><span class="sxs-lookup"><span data-stu-id="ac136-121">0x8004100c</span></span> | <span data-ttu-id="ac136-122">İstenen özellik türü `CIM_OBJECT` veya `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="ac136-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ac136-123">0</span><span class="sxs-lookup"><span data-stu-id="ac136-123">0</span></span> | <span data-ttu-id="ac136-124">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="ac136-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="ac136-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac136-125">Remarks</span></span>

<span data-ttu-id="ac136-126">Bu işlev, [IWbemClassObject:: GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="ac136-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) method.</span></span>

<span data-ttu-id="ac136-127">Bu tanıtıcıyı, özellik değerlerini okumak veya yazmak için [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) yöntemlerini kullanırken özellikleri tanımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac136-127">You can use this handle to identify properties when using  [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) methods to read or write property values.</span></span>

<span data-ttu-id="ac136-128">Tutamaçları, `CIM_OBJECT` ve `CIM_ARRAY`dışındaki tüm veri türlerinin özellikleri için alınabilir.</span><span class="sxs-lookup"><span data-stu-id="ac136-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="ac136-129">Döndürülen tutamaçlar bir sınıfın tüm örneklerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="ac136-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="ac136-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac136-130">Requirements</span></span>

<span data-ttu-id="ac136-131">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac136-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="ac136-132">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="ac136-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="ac136-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ac136-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ac136-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac136-134">See also</span></span>

- [<span data-ttu-id="ac136-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ac136-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
