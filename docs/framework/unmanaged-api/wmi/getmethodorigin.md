---
title: GetMethodOrigin işlevi (yönetilmeyen API Başvurusu)
description: GetMethodOrigin işlevi bir yöntem içinde bildirildiği sınıf belirler.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76f449e52168001a2aaac6cbc3707361cf7f809a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582476"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="b77f6-103">GetMethodOrigin işlevi</span><span class="sxs-lookup"><span data-stu-id="b77f6-103">GetMethodOrigin function</span></span>
<span data-ttu-id="b77f6-104">Bir yöntem içinde bildirildiği sınıf belirler.</span><span class="sxs-lookup"><span data-stu-id="b77f6-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b77f6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b77f6-105">Syntax</span></span>  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="b77f6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b77f6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b77f6-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="b77f6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b77f6-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="b77f6-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="b77f6-109">[in] Sahip olan, sınıfı istenen nesne için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="b77f6-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="b77f6-110">[out] Yöntemi sahip olduğu sınıfın adını alır.</span><span class="sxs-lookup"><span data-stu-id="b77f6-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="b77f6-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b77f6-111">Return value</span></span>

<span data-ttu-id="b77f6-112">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="b77f6-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b77f6-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="b77f6-113">Constant</span></span>  |<span data-ttu-id="b77f6-114">Değer</span><span class="sxs-lookup"><span data-stu-id="b77f6-114">Value</span></span>  |<span data-ttu-id="b77f6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b77f6-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="b77f6-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="b77f6-116">0x80041002</span></span> | <span data-ttu-id="b77f6-117">Belirtilen yöntem bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="b77f6-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b77f6-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b77f6-118">0x80041008</span></span> | <span data-ttu-id="b77f6-119">Bir veya daha fazla parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b77f6-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b77f6-120">0</span><span class="sxs-lookup"><span data-stu-id="b77f6-120">0</span></span> | <span data-ttu-id="b77f6-121">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="b77f6-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b77f6-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b77f6-122">Remarks</span></span>

<span data-ttu-id="b77f6-123">Bu işlev bir çağrı sarılır [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b77f6-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="b77f6-124">Bir sınıfı yöntemleri bir veya daha fazla temel sınıftan devralınabilir. çünkü, geliştiriciler genellikle belirli bir yöntemin tanımlandığı sınıf belirlemek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="b77f6-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="b77f6-125">`pstrClassName` Parametre gerekir işaret geçerli bir `BSTR` çünkü bu işlevi çağrılmadan önce bir `out` parametre; bu işaretçisi işlev döndürdükten sonra serbest.</span><span class="sxs-lookup"><span data-stu-id="b77f6-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="b77f6-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b77f6-126">Requirements</span></span>  
<span data-ttu-id="b77f6-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b77f6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b77f6-128">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b77f6-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b77f6-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b77f6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b77f6-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b77f6-130">See also</span></span>
- [<span data-ttu-id="b77f6-131">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b77f6-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
