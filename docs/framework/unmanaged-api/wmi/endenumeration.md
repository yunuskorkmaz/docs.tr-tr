---
title: "Örneğin işlevi (yönetilmeyen API Başvurusu)"
description: "Örneğin işlevi numaralandırma sonlandırır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: EndEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: EndEnumeration
helpviewer_keywords: EndEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fee3137dad3f89fa8849b28e9ca38b40040f916e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="endenumeration-function"></a><span data-ttu-id="93c47-103">Örneğin işlevi</span><span class="sxs-lookup"><span data-stu-id="93c47-103">EndEnumeration function</span></span>
<span data-ttu-id="93c47-104">Çağrı kullanmaya bir numaralandırma sırasını sonlandırır [BeginEnumeration işlevi](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="93c47-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="93c47-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93c47-105">Syntax</span></span>  
  
```  
HRESULT EndEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="93c47-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93c47-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="93c47-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="93c47-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="93c47-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="93c47-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>


## <a name="return-value"></a><span data-ttu-id="93c47-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="93c47-109">Return value</span></span>

<span data-ttu-id="93c47-110">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="93c47-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="93c47-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="93c47-111">Constant</span></span>  |<span data-ttu-id="93c47-112">Değer</span><span class="sxs-lookup"><span data-stu-id="93c47-112">Value</span></span>  |<span data-ttu-id="93c47-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93c47-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="93c47-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="93c47-114">0x80041001</span></span> | <span data-ttu-id="93c47-115">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="93c47-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="93c47-116">0</span><span class="sxs-lookup"><span data-stu-id="93c47-116">0</span></span> | <span data-ttu-id="93c47-117">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="93c47-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="93c47-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93c47-118">Remarks</span></span>

<span data-ttu-id="93c47-119">Bu işlev çağrısı sarmalar [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="93c47-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="93c47-120">Çağrı `EndEnumeration` işlevi gerekli değildir, ancak numaralandırması ile ilişkili kaynakları serbest nedeniyle önerilir.</span><span class="sxs-lookup"><span data-stu-id="93c47-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="93c47-121">Ancak, resoruces otomatik olarak sonraki numaralandırma başlatıldığında veya nesne serbest serbest.</span><span class="sxs-lookup"><span data-stu-id="93c47-121">However, the resoruces are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="93c47-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93c47-122">Requirements</span></span>  
 <span data-ttu-id="93c47-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93c47-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93c47-124">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="93c47-124">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="93c47-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="93c47-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93c47-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93c47-126">See also</span></span>  
[<span data-ttu-id="93c47-127">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="93c47-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
