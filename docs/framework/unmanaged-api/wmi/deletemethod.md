---
title: "DeleteMethod işlevi (yönetilmeyen API Başvurusu)"
description: "DeleteMethod işlevi belirtilen yöntem bir CIM sınıfı tanımından siler."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: DeleteMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: DeleteMethod
helpviewer_keywords: DeleteMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d931cb76eeaf19ddeb80bdde412fabeea4b70203
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="deletemethod-function"></a><span data-ttu-id="06f59-103">DeleteMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="06f59-103">DeleteMethod function</span></span>
<span data-ttu-id="06f59-104">Belirtilen yöntem bir CIM sınıfı tanımından siler.</span><span class="sxs-lookup"><span data-stu-id="06f59-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="06f59-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06f59-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="06f59-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06f59-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="06f59-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="06f59-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="06f59-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="06f59-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="06f59-109">[in] Sınıf tablodan kaldırmak için yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="06f59-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="06f59-110">`wszName`Geçerli bir işaretçi olmalıdır `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="06f59-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="06f59-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="06f59-111">Return value</span></span>

<span data-ttu-id="06f59-112">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="06f59-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="06f59-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="06f59-113">Constant</span></span>  |<span data-ttu-id="06f59-114">Değer</span><span class="sxs-lookup"><span data-stu-id="06f59-114">Value</span></span>  |<span data-ttu-id="06f59-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="06f59-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="06f59-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="06f59-116">0x80041002</span></span> | <span data-ttu-id="06f59-117">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="06f59-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="06f59-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="06f59-118">0x80041006</span></span> | <span data-ttu-id="06f59-119">İşlemi tamamlamak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="06f59-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="06f59-120">0</span><span class="sxs-lookup"><span data-stu-id="06f59-120">0</span></span> | <span data-ttu-id="06f59-121">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="06f59-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="06f59-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06f59-122">Remarks</span></span>

<span data-ttu-id="06f59-123">Bu işlev çağrısı sarmalar [IWbemClassObject::DeleteMethod](https://msdn.microsoft.com/library/aa391439(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06f59-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](https://msdn.microsoft.com/library/aa391439(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="06f59-124">Yöntem silme işlemi için desteklenmez [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) CIM örneklerine noktası işaretçileri.</span><span class="sxs-lookup"><span data-stu-id="06f59-124">Method deletion is not supported for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="06f59-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06f59-125">Requirements</span></span>  
 <span data-ttu-id="06f59-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06f59-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06f59-127">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="06f59-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="06f59-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="06f59-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f59-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06f59-129">See also</span></span>  
[<span data-ttu-id="06f59-130">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="06f59-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
