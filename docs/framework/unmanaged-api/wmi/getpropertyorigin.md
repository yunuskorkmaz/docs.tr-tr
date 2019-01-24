---
title: GetPropertyOrigin işlevi (Unmnaged API Başvurusu)
description: GetPropertyOrigin işlevi, bir özellik içinde bildirildiği sınıf belirler.
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
ms.openlocfilehash: b61c0359b8b18cb5082b1739defc65371476af25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529927"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="8be82-103">GetPropertyOrigin işlevi</span><span class="sxs-lookup"><span data-stu-id="8be82-103">GetPropertyOrigin function</span></span>
<span data-ttu-id="8be82-104">Bir özellik içinde bildirildiği sınıf belirler.</span><span class="sxs-lookup"><span data-stu-id="8be82-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="8be82-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8be82-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="8be82-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8be82-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8be82-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="8be82-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="8be82-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="8be82-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="8be82-109">[in] Özelliğin adı, sahibi olan sınıfı istenen nesne için.</span><span class="sxs-lookup"><span data-stu-id="8be82-109">[in] The name of the property for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="8be82-110">[out] Özellik sahibi sınıfının adını alır.</span><span class="sxs-lookup"><span data-stu-id="8be82-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="8be82-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="8be82-111">Return value</span></span>

<span data-ttu-id="8be82-112">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="8be82-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8be82-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="8be82-113">Constant</span></span>  |<span data-ttu-id="8be82-114">Değer</span><span class="sxs-lookup"><span data-stu-id="8be82-114">Value</span></span>  |<span data-ttu-id="8be82-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8be82-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="8be82-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="8be82-116">0x80041001</span></span> | <span data-ttu-id="8be82-117">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8be82-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="8be82-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="8be82-118">0x80041002</span></span> | <span data-ttu-id="8be82-119">Belirtilen özellik bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="8be82-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8be82-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8be82-120">0x80041008</span></span> | <span data-ttu-id="8be82-121">Bir parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="8be82-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8be82-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8be82-122">0x80041006</span></span> | <span data-ttu-id="8be82-123">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="8be82-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8be82-124">0</span><span class="sxs-lookup"><span data-stu-id="8be82-124">0</span></span> | <span data-ttu-id="8be82-125">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="8be82-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="8be82-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8be82-126">Remarks</span></span>

<span data-ttu-id="8be82-127">Bu işlev bir çağrı sarılır [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8be82-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="8be82-128">Bir sınıf özelliklerini bir veya daha fazla temel sınıftan devralabilir olduğundan, geliştiriciler genellikle belirli bir yöntemin tanımlandığı özellik belirlemek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="8be82-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="8be82-129">`pstrClassName` Parametre gerekir işaret geçerli bir `BSTR` çünkü bu işlevi çağrılmadan önce bir `out` parametre; bu işaretçisi işlev döndürdükten sonra serbest.</span><span class="sxs-lookup"><span data-stu-id="8be82-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="8be82-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8be82-130">Requirements</span></span>  
<span data-ttu-id="8be82-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8be82-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8be82-132">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8be82-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8be82-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8be82-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be82-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8be82-134">See also</span></span>
- [<span data-ttu-id="8be82-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8be82-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
