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
ms.openlocfilehash: 043fce26870e5af2850b9f2e91e7e97c7bee6c90
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="endenumeration-function"></a><span data-ttu-id="a3459-103">Örneğin işlevi</span><span class="sxs-lookup"><span data-stu-id="a3459-103">EndEnumeration function</span></span>
<span data-ttu-id="a3459-104">Çağrı kullanmaya bir numaralandırma sırasını sonlandırır [BeginEnumeration işlevi](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a3459-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="a3459-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3459-105">Syntax</span></span>  
  
```  
HRESULT EndEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="a3459-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3459-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a3459-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a3459-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a3459-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="a3459-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>


## <a name="return-value"></a><span data-ttu-id="a3459-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="a3459-109">Return value</span></span>

<span data-ttu-id="a3459-110">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="a3459-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a3459-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="a3459-111">Constant</span></span>  |<span data-ttu-id="a3459-112">Değer</span><span class="sxs-lookup"><span data-stu-id="a3459-112">Value</span></span>  |<span data-ttu-id="a3459-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3459-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="a3459-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a3459-114">0x80041001</span></span> | <span data-ttu-id="a3459-115">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a3459-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a3459-116">0</span><span class="sxs-lookup"><span data-stu-id="a3459-116">0</span></span> | <span data-ttu-id="a3459-117">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="a3459-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a3459-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3459-118">Remarks</span></span>

<span data-ttu-id="a3459-119">Bu işlev çağrısı sarmalar [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a3459-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="a3459-120">Çağrı `EndEnumeration` işlevi gerekli değildir, ancak numaralandırması ile ilişkili kaynakları serbest nedeniyle önerilir.</span><span class="sxs-lookup"><span data-stu-id="a3459-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="a3459-121">Ancak, resoruces otomatik olarak sonraki numaralandırma başlatıldığında veya nesne serbest serbest.</span><span class="sxs-lookup"><span data-stu-id="a3459-121">However, the resoruces are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="a3459-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3459-122">Requirements</span></span>  
 <span data-ttu-id="a3459-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3459-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3459-124">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a3459-124">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a3459-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a3459-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3459-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3459-126">See also</span></span>  
[<span data-ttu-id="a3459-127">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a3459-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
