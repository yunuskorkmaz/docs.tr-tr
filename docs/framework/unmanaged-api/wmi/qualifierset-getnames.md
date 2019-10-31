---
title: QualifierSet_GetNames işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_GetNames işlevi, bir nesne veya özellikten niteleyicilerin adlarını alır.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: bd0a67987dd8ffa825114726d066249aed40cf05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141700"
---
# <a name="qualifierset_getnames-function"></a><span data-ttu-id="feab1-103">QualifierSet_GetNames işlevi</span><span class="sxs-lookup"><span data-stu-id="feab1-103">QualifierSet_GetNames function</span></span>

<span data-ttu-id="feab1-104">Geçerli nesne veya özellikten kullanılabilen tüm niteleyicilerin veya belirli niteleyicilerin adlarını alır.</span><span class="sxs-lookup"><span data-stu-id="feab1-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="feab1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="feab1-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a><span data-ttu-id="feab1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="feab1-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="feab1-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="feab1-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="feab1-108">'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="feab1-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="feab1-109">'ndaki Aşağıdaki bayraklardan biri veya sabit listesine hangi adların ekleneceğini belirten değerler.</span><span class="sxs-lookup"><span data-stu-id="feab1-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="feab1-110">Sabit</span><span class="sxs-lookup"><span data-stu-id="feab1-110">Constant</span></span>  |<span data-ttu-id="feab1-111">Değer</span><span class="sxs-lookup"><span data-stu-id="feab1-111">Value</span></span>  |<span data-ttu-id="feab1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="feab1-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="feab1-113">0</span><span class="sxs-lookup"><span data-stu-id="feab1-113">0</span></span> | <span data-ttu-id="feab1-114">Tüm niteleyicilerin adlarını döndürün.</span><span class="sxs-lookup"><span data-stu-id="feab1-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="feab1-115">0x10</span><span class="sxs-lookup"><span data-stu-id="feab1-115">0x10</span></span> | <span data-ttu-id="feab1-116">Yalnızca geçerli özelliğe veya nesneye özgü niteleyicilerin adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="feab1-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="feab1-117">Bir özellik için: yalnızca özelliğe özgü niteleyicileri döndürün (geçersiz kılmalar dahil), sınıf tanımından yayılan niteleyiciler değildir.</span><span class="sxs-lookup"><span data-stu-id="feab1-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="feab1-118">Bir örnek için: yalnızca örneğe özgü niteleyici adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="feab1-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="feab1-119">Bir sınıf için: yalnızca türetmekte olan sınıfa özgü niteleyicileri döndürün.</span><span class="sxs-lookup"><span data-stu-id="feab1-119">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="feab1-120">0x20</span><span class="sxs-lookup"><span data-stu-id="feab1-120">0x20</span></span> | <span data-ttu-id="feab1-121">Yalnızca başka bir nesneden yayılan niteleyicilerin adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="feab1-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="feab1-122">Bir özellik için: yalnızca sınıf tanımından bu özelliğe yayılan niteleyicileri döndürün, özelliğin kendisinden değil.</span><span class="sxs-lookup"><span data-stu-id="feab1-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="feab1-123">Bir örnek için: yalnızca sınıf tanımından yayılan niteleyicileri döndürün.</span><span class="sxs-lookup"><span data-stu-id="feab1-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="feab1-124">Bir sınıf için: yalnızca üst sınıflardan devralınan niteleyici adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="feab1-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

`pstrNames`\
<span data-ttu-id="feab1-125">dışı İstenen adları içeren yeni bir `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="feab1-125">[out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="feab1-126">Dizide 0 öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="feab1-126">The array can have 0 elements.</span></span> <span data-ttu-id="feab1-127">Bir hata oluşursa, yeni bir `SAFEARRAY` döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="feab1-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="feab1-128">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="feab1-128">Return value</span></span>

<span data-ttu-id="feab1-129">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="feab1-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="feab1-130">Sabit</span><span class="sxs-lookup"><span data-stu-id="feab1-130">Constant</span></span>  |<span data-ttu-id="feab1-131">Değer</span><span class="sxs-lookup"><span data-stu-id="feab1-131">Value</span></span>  |<span data-ttu-id="feab1-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="feab1-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="feab1-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="feab1-133">0x80041008</span></span> | <span data-ttu-id="feab1-134">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="feab1-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="feab1-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="feab1-135">0x80041006</span></span> | <span data-ttu-id="feab1-136">Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="feab1-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="feab1-137">0</span><span class="sxs-lookup"><span data-stu-id="feab1-137">0</span></span> | <span data-ttu-id="feab1-138">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="feab1-138">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="feab1-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="feab1-139">Remarks</span></span>

<span data-ttu-id="feab1-140">Bu işlev, [IWbemQualifierSet:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="feab1-140">This function wraps a call to the [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) method.</span></span>

<span data-ttu-id="feab1-141">Niteleyici adlarını aldıktan sonra, [QualifierSet_Get](qualifierset-get.md) işlevini çağırarak her bir niteleyicisine ada göre erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="feab1-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span>

<span data-ttu-id="feab1-142">Belirli bir nesnenin sıfır niteleyicisi olması için bir hata değil, bu nedenle dönüşte `pstrNames` dize sayısı, işlev `WBEM_S_NO_ERROR`döndürse bile 0 olabilir.</span><span class="sxs-lookup"><span data-stu-id="feab1-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="feab1-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feab1-143">Requirements</span></span>

<span data-ttu-id="feab1-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feab1-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="feab1-145">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="feab1-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="feab1-146">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="feab1-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="feab1-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="feab1-147">See also</span></span>

- [<span data-ttu-id="feab1-148">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="feab1-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
