---
title: "QualifierSet_GetNames işlevi (yönetilmeyen API Başvurusu)"
description: "QualifierSet_GetNames işlevi, bir nesneye veya özelliğe niteleyicileri adlarını alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_GetNames
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_GetNames
helpviewer_keywords: QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b87518bdc1f6ac19eb48991538be5904fdb63f1f
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetgetnames-function"></a><span data-ttu-id="d0c74-103">QualifierSet_GetNames işlevi</span><span class="sxs-lookup"><span data-stu-id="d0c74-103">QualifierSet_GetNames function</span></span>
<span data-ttu-id="d0c74-104">Tüm niteleyicileri veya geçerli nesne ya da özellik kullanılabilir belirli niteleyicileri adlarını alır.</span><span class="sxs-lookup"><span data-stu-id="d0c74-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d0c74-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0c74-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a><span data-ttu-id="d0c74-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0c74-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="d0c74-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d0c74-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="d0c74-108">[in] Bir işaretçi bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="d0c74-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="d0c74-109">[in] Aşağıdaki bayraklar veya numaralandırmada dahil etmek için hangi adlarını belirtir değerleri biri.</span><span class="sxs-lookup"><span data-stu-id="d0c74-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="d0c74-110">Sabit</span><span class="sxs-lookup"><span data-stu-id="d0c74-110">Constant</span></span>  |<span data-ttu-id="d0c74-111">Değer</span><span class="sxs-lookup"><span data-stu-id="d0c74-111">Value</span></span>  |<span data-ttu-id="d0c74-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0c74-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="d0c74-113">0</span><span class="sxs-lookup"><span data-stu-id="d0c74-113">0</span></span> | <span data-ttu-id="d0c74-114">Tüm niteleyicileri adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0c74-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="d0c74-115">0x10</span><span class="sxs-lookup"><span data-stu-id="d0c74-115">0x10</span></span> | <span data-ttu-id="d0c74-116">Yalnızca niteleyicileri adlarını belirli geçerli özellik veya nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0c74-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="d0c74-117">Bir özellik için: yalnızca niteleyicileri (geçersiz kılmaları dahil) özelliğine belirli dönün ve bu niteleyicileri sınıf tanımı yayılır.</span><span class="sxs-lookup"><span data-stu-id="d0c74-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="d0c74-118">Bir örneği için: yalnızca örneğe özgü niteleyicisi adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0c74-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="d0c74-119">Bir sınıf için: yalnızca niteleyicileri türetilmiş sınıf beiong belirli döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0c74-119">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="d0c74-120">0x20</span><span class="sxs-lookup"><span data-stu-id="d0c74-120">0x20</span></span> | <span data-ttu-id="d0c74-121">Başka bir nesne yalnızca niteleyicileri adlarını yayılan dönüş.</span><span class="sxs-lookup"><span data-stu-id="d0c74-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="d0c74-122">Bir özellik için: sınıf tanımı ve özelliğinden olanlar geri dönmek için bu özelliği olarak yalnızca niteleyicileri yayılır.</span><span class="sxs-lookup"><span data-stu-id="d0c74-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="d0c74-123">Bir örneği için: sınıf tanımını dönüş yalnızca bu niteleyicileri yayılır.</span><span class="sxs-lookup"><span data-stu-id="d0c74-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="d0c74-124">Bir sınıf için: Return niteleyicisi adları yalnızca üst sınıflardan devralınır.</span><span class="sxs-lookup"><span data-stu-id="d0c74-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

<span data-ttu-id="d0c74-125">`pstrNames`[out] Yeni bir `SAFEARRAY` istenen adlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d0c74-125">`pstrNames` [out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="d0c74-126">Dizi 0 öğeler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="d0c74-126">The array can have 0 elements.</span></span> <span data-ttu-id="d0c74-127">Bir hata oluşursa, yeni bir `SAFEARRAY` döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="d0c74-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="d0c74-128">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d0c74-128">Return value</span></span>

<span data-ttu-id="d0c74-129">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="d0c74-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d0c74-130">Sabit</span><span class="sxs-lookup"><span data-stu-id="d0c74-130">Constant</span></span>  |<span data-ttu-id="d0c74-131">Değer</span><span class="sxs-lookup"><span data-stu-id="d0c74-131">Value</span></span>  |<span data-ttu-id="d0c74-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0c74-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d0c74-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d0c74-133">0x80041008</span></span> | <span data-ttu-id="d0c74-134">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="d0c74-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d0c74-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d0c74-135">0x80041006</span></span> | <span data-ttu-id="d0c74-136">Yeni bir numaralandırma başlatmak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="d0c74-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d0c74-137">0</span><span class="sxs-lookup"><span data-stu-id="d0c74-137">0</span></span> | <span data-ttu-id="d0c74-138">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="d0c74-138">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d0c74-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0c74-139">Remarks</span></span>

<span data-ttu-id="d0c74-140">Bu işlev çağrısı sarmalar [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d0c74-140">This function wraps a call to the [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="d0c74-141">Niteleyici adları elde sonra her niteleyicisi ada göre arayarak erişebilirsiniz [QualifierSet_Get](qualifierset-get.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="d0c74-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span> 

<span data-ttu-id="d0c74-142">Sıfır niteleyicileri olması belirli bir nesne için bir hata değildir dizelerde sayısı `pstrNames` işlevi döndürür olsa bile getirisi 0, olabilir `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="d0c74-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0c74-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0c74-143">Requirements</span></span>  
 <span data-ttu-id="d0c74-144">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0c74-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0c74-145">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d0c74-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d0c74-146">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d0c74-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0c74-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0c74-147">See also</span></span>  
[<span data-ttu-id="d0c74-148">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d0c74-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
