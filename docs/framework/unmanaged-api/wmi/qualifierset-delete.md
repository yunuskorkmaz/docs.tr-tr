---
title: QualifierSet_Delete işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Delete işlevi bir niteleyici adıyla siler.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0e96ba458edfe7261fd5857b7bcb8486f4a6636
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460051"
---
# <a name="qualifiersetdelete-function"></a><span data-ttu-id="c7a11-103">QualifierSet_Delete işlevi</span><span class="sxs-lookup"><span data-stu-id="c7a11-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="c7a11-104">Belirtilen bir niteleyici adıyla siler.</span><span class="sxs-lookup"><span data-stu-id="c7a11-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c7a11-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7a11-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="c7a11-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7a11-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="c7a11-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c7a11-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="c7a11-108">[in] Bir işaretçi bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="c7a11-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="c7a11-109">[in] Silmek için Niteleyici adı.</span><span class="sxs-lookup"><span data-stu-id="c7a11-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="c7a11-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="c7a11-110">Return value</span></span>

<span data-ttu-id="c7a11-111">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="c7a11-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c7a11-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="c7a11-112">Constant</span></span>  |<span data-ttu-id="c7a11-113">Değer</span><span class="sxs-lookup"><span data-stu-id="c7a11-113">Value</span></span>  |<span data-ttu-id="c7a11-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7a11-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c7a11-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c7a11-115">0x80041008</span></span> | <span data-ttu-id="c7a11-116">`wszName` Parametresi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="c7a11-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="c7a11-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="c7a11-117">0x80041016</span></span> | <span data-ttu-id="c7a11-118">Bu niteleyici silme geçersiz.</span><span class="sxs-lookup"><span data-stu-id="c7a11-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="c7a11-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="c7a11-119">0x80041002</span></span> | <span data-ttu-id="c7a11-120">Belirtilen niteleyici bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="c7a11-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c7a11-121">0</span><span class="sxs-lookup"><span data-stu-id="c7a11-121">0</span></span> | <span data-ttu-id="c7a11-122">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="c7a11-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="c7a11-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="c7a11-123">0x40002</span></span> | <span data-ttu-id="c7a11-124">Yerel geçersiz kılma silindi ve özgün niteleyici üst nesneden kapsam sürdürdü.</span><span class="sxs-lookup"><span data-stu-id="c7a11-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c7a11-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7a11-125">Remarks</span></span>

<span data-ttu-id="c7a11-126">Bu işlev çağrısı sarmalar [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c7a11-126">This function wraps a call to the [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="c7a11-127">Niteleyici yayma kuralları nedeniyle, belirli bir niteleyici alınan başka bir nesneden ve yalnızca geçerli sınıf veya örnek geçersiz kılındı.</span><span class="sxs-lookup"><span data-stu-id="c7a11-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="c7a11-128">Bu durumda, `QualifierSet_Delete` yöntemi özgün devralınan değerine niteleyici sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="c7a11-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="c7a11-129">İşlev, bu durumda durum kodunu döndürür `WBEM_S_RESET_TO_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="c7a11-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7a11-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7a11-130">Requirements</span></span>  
 <span data-ttu-id="c7a11-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7a11-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7a11-132">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c7a11-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c7a11-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c7a11-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a11-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7a11-134">See also</span></span>  
[<span data-ttu-id="c7a11-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c7a11-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
