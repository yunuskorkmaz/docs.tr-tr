---
title: GetMethodOrigin işlevi (yönetilmeyen API Başvurusu)
description: GetMethodOrigin işlevi, bir yöntemin bildirildiği sınıfı belirler.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 434392ffb4d9124e319bcd9c42fdd340d3fec5b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722784"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="eeea4-103">GetMethodOrigin işlevi</span><span class="sxs-lookup"><span data-stu-id="eeea4-103">GetMethodOrigin function</span></span>

<span data-ttu-id="eeea4-104">Bir yöntemin bildirildiği sınıfı belirler.</span><span class="sxs-lookup"><span data-stu-id="eeea4-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="eeea4-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="eeea4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a><span data-ttu-id="eeea4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eeea4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="eeea4-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="eeea4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="eeea4-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eeea4-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="eeea4-109">'ndaki Sahip sınıfı istenen nesne için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="eeea4-109">[in] The name of the method for the object whose owning class is being requested.</span></span>

`pstrClassName`  
<span data-ttu-id="eeea4-110">dışı Yöntemine sahip olan sınıfın adını alır.</span><span class="sxs-lookup"><span data-stu-id="eeea4-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="eeea4-111">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="eeea4-111">Return value</span></span>

<span data-ttu-id="eeea4-112">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eeea4-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="eeea4-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="eeea4-113">Constant</span></span>  |<span data-ttu-id="eeea4-114">Değer</span><span class="sxs-lookup"><span data-stu-id="eeea4-114">Value</span></span>  |<span data-ttu-id="eeea4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eeea4-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="eeea4-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="eeea4-116">0x80041002</span></span> | <span data-ttu-id="eeea4-117">Belirtilen yöntem bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="eeea4-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="eeea4-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="eeea4-118">0x80041008</span></span> | <span data-ttu-id="eeea4-119">Bir veya daha fazla parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="eeea4-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="eeea4-120">0</span><span class="sxs-lookup"><span data-stu-id="eeea4-120">0</span></span> | <span data-ttu-id="eeea4-121">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="eeea4-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="eeea4-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eeea4-122">Remarks</span></span>

<span data-ttu-id="eeea4-123">Bu işlev, [IWbemClassObject:: GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="eeea4-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="eeea4-124">Bir sınıf bir veya daha fazla taban sınıftan Yöntemler devraldığı için, geliştiriciler genellikle belirli bir yöntemin tanımlandığı sınıfı belirleyebilmek ister.</span><span class="sxs-lookup"><span data-stu-id="eeea4-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="eeea4-125">Parametresi `pstrClassName` bir parametre olduğundan, işlev çağrılmadan önce geçerli bir işaret içermemelidir `BSTR` `out` ; Bu işaretçi, işlev çağrıldıktan sonra serbest bırakılmaz.</span><span class="sxs-lookup"><span data-stu-id="eeea4-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="eeea4-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eeea4-126">Requirements</span></span>  

<span data-ttu-id="eeea4-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eeea4-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeea4-128">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="eeea4-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="eeea4-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eeea4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeea4-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eeea4-130">See also</span></span>

- [<span data-ttu-id="eeea4-131">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="eeea4-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
