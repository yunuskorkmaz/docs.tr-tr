---
title: "QualifierSet_BeginEnumeration işlevi (yönetilmeyen API Başvurusu)"
description: "QualifierSet_BeginEnumeration işlevi bir nesnenin niteleyicileri numaralandırması sıfırlar."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_BeginEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_BeginEnumeration
helpviewer_keywords: QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 440dde03f4ed138a33eb6f817723d7c5c74f6d46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetbeginenumeration-function"></a><span data-ttu-id="34f71-103">QualifierSet_BeginEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="34f71-103">QualifierSet_BeginEnumeration function</span></span>
<span data-ttu-id="34f71-104">Bir nesnenin niteleyicileri numaralandırması sabit başlangıç durumuna sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="34f71-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="34f71-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34f71-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="34f71-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34f71-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="34f71-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="34f71-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="34f71-108">[in] Bir işaretçi bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="34f71-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="34f71-109">[in] Bayrakları veya açıklanan değerlerinin Bitsel bir birleşimi [açıklamalar](#remarks) numaralandırmada içerecek şekilde niteleyicileri belirtir bölümü.</span><span class="sxs-lookup"><span data-stu-id="34f71-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="34f71-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="34f71-110">Return value</span></span>

<span data-ttu-id="34f71-111">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="34f71-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="34f71-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="34f71-112">Constant</span></span>  |<span data-ttu-id="34f71-113">Değer</span><span class="sxs-lookup"><span data-stu-id="34f71-113">Value</span></span>  |<span data-ttu-id="34f71-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34f71-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="34f71-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="34f71-115">0x80041008</span></span> | <span data-ttu-id="34f71-116">`lFlags` Parametresi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="34f71-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="34f71-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="34f71-117">0x8004101d</span></span> | <span data-ttu-id="34f71-118">İkinci çağrı `QualifierSet_BeginEnumeration` olmadan müdahalede bulunan bir çağrı yapıldı [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="34f71-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="34f71-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="34f71-119">0x80041006</span></span> | <span data-ttu-id="34f71-120">Yeni bir numaralandırma başlatmak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="34f71-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="34f71-121">0</span><span class="sxs-lookup"><span data-stu-id="34f71-121">0</span></span> | <span data-ttu-id="34f71-122">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="34f71-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="34f71-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34f71-123">Remarks</span></span>

<span data-ttu-id="34f71-124">Bu işlev çağrısı sarmalar [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="34f71-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="34f71-125">Bir nesne üzerinde niteleyicileri tümünün numaralandırmak için bu yöntem ilk çağrıda önce çağrılmalıdır [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="34f71-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="34f71-126">Niteleyiciler numaralandırılan sipariş için belirli bir numaralandırma sabit olması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="34f71-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="34f71-127">Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişkeni tanımlanmış *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="34f71-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>   

|<span data-ttu-id="34f71-128">Sabit</span><span class="sxs-lookup"><span data-stu-id="34f71-128">Constant</span></span>  |<span data-ttu-id="34f71-129">Değer</span><span class="sxs-lookup"><span data-stu-id="34f71-129">Value</span></span>  |<span data-ttu-id="34f71-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34f71-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="34f71-131">0</span><span class="sxs-lookup"><span data-stu-id="34f71-131">0</span></span> | <span data-ttu-id="34f71-132">Tüm niteleyicileri adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="34f71-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="34f71-133">0x10</span><span class="sxs-lookup"><span data-stu-id="34f71-133">0x10</span></span> | <span data-ttu-id="34f71-134">Yalnızca niteleyicileri adlarını belirli geçerli özellik veya nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="34f71-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="34f71-135">Bir özellik için: yalnızca niteleyicileri (geçersiz kılmaları dahil) özelliğine belirli dönün ve bu niteleyicileri sınıf tanımı yayılır.</span><span class="sxs-lookup"><span data-stu-id="34f71-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="34f71-136">Bir örneği için: yalnızca örneğe özgü niteleyicisi adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="34f71-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="34f71-137">Bir sınıf için: yalnızca niteleyicileri türetilmiş sınıf beiong belirli döndürür.</span><span class="sxs-lookup"><span data-stu-id="34f71-137">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="34f71-138">0x20</span><span class="sxs-lookup"><span data-stu-id="34f71-138">0x20</span></span> | <span data-ttu-id="34f71-139">Başka bir nesne yalnızca niteleyicileri adlarını yayılan dönüş.</span><span class="sxs-lookup"><span data-stu-id="34f71-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="34f71-140">Bir özellik için: sınıf tanımı ve özelliğinden olanlar geri dönmek için bu özelliği olarak yalnızca niteleyicileri yayılır.</span><span class="sxs-lookup"><span data-stu-id="34f71-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="34f71-141">Bir örneği için: sınıf tanımını dönüş yalnızca bu niteleyicileri yayılır.</span><span class="sxs-lookup"><span data-stu-id="34f71-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="34f71-142">Bir sınıf için: Return niteleyicisi adları yalnızca üst sınıflardan devralınır.</span><span class="sxs-lookup"><span data-stu-id="34f71-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="34f71-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34f71-143">Requirements</span></span>  
 <span data-ttu-id="34f71-144">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34f71-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34f71-145">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="34f71-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="34f71-146">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="34f71-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f71-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34f71-147">See also</span></span>  
[<span data-ttu-id="34f71-148">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="34f71-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
