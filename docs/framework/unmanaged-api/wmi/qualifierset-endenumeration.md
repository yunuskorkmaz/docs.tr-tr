---
title: "QualifierSet_EndEnumeration işlevi (yönetilmeyen API Başvurusu)"
description: "QualifierSet_EndEnumeration işlevi numaralandırma sonlandırır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_EndEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_EndEnumeration
helpviewer_keywords: QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7868a0c0ba5abb880af201ce73b35f5ffed6f223
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetendenumeration-function"></a><span data-ttu-id="f364e-103">QualifierSet_EndEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="f364e-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="f364e-104">Çağrısıyla başlamış numaralandırması sonlandırır [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="f364e-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f364e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f364e-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="f364e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f364e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f364e-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="f364e-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="f364e-108">[in] Bir işaretçi bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="f364e-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="f364e-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="f364e-109">Return value</span></span>

<span data-ttu-id="f364e-110">Bu işlev tarafından döndürülen değerin aşağıdaki tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz, bir sabit değer olarak, kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="f364e-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="f364e-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="f364e-111">Constant</span></span>  |<span data-ttu-id="f364e-112">Değer</span><span class="sxs-lookup"><span data-stu-id="f364e-112">Value</span></span>  |<span data-ttu-id="f364e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f364e-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f364e-114">0</span><span class="sxs-lookup"><span data-stu-id="f364e-114">0</span></span> | <span data-ttu-id="f364e-115">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="f364e-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f364e-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f364e-116">Remarks</span></span>

<span data-ttu-id="f364e-117">Bu işlev çağrısı sarmalar [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f364e-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="f364e-118">Bu çağrı, önerilir ancak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f364e-118">This call is recommended, but not required.</span></span> <span data-ttu-id="f364e-119">Hemen numaralandırması ile ilişkili kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="f364e-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="f364e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f364e-120">Requirements</span></span>  

<span data-ttu-id="f364e-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f364e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="f364e-122">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f364e-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="f364e-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f364e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f364e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f364e-124">See also</span></span>  
[<span data-ttu-id="f364e-125">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f364e-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
