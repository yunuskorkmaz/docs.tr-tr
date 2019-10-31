---
title: QualifierSet_BeginEnumeration işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_BeginEnumeration işlevi, bir nesnenin niteleyicilerinin bir numaralandırıcısı sıfırlar.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 79edbd876fc9992f088b9adb159e005c735a72cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127321"
---
# <a name="qualifierset_beginenumeration-function"></a><span data-ttu-id="3be6f-103">QualifierSet_BeginEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="3be6f-103">QualifierSet_BeginEnumeration function</span></span>

<span data-ttu-id="3be6f-104">Bir nesnenin niteleyicilerinin bir Numaralandırıcı, numaralandırmanın başlangıcına sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="3be6f-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="3be6f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3be6f-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a><span data-ttu-id="3be6f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3be6f-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="3be6f-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3be6f-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="3be6f-108">'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3be6f-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="3be6f-109">'ndaki Listelemenin dahil olduğu niteleyicileri belirten [açıklamalar](#remarks) bölümünde açıklanan bayrakların veya değerlerin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="3be6f-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="3be6f-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="3be6f-110">Return value</span></span>

<span data-ttu-id="3be6f-111">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3be6f-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3be6f-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="3be6f-112">Constant</span></span>  |<span data-ttu-id="3be6f-113">Değer</span><span class="sxs-lookup"><span data-stu-id="3be6f-113">Value</span></span>  |<span data-ttu-id="3be6f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3be6f-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3be6f-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3be6f-115">0x80041008</span></span> | <span data-ttu-id="3be6f-116">`lFlags` parametresi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="3be6f-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="3be6f-117">0x8004101D</span><span class="sxs-lookup"><span data-stu-id="3be6f-117">0x8004101d</span></span> | <span data-ttu-id="3be6f-118">`QualifierSet_BeginEnumeration` ikinci bir çağrısı, [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md)için araya giren bir çağrı olmadan yapıldı.</span><span class="sxs-lookup"><span data-stu-id="3be6f-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="3be6f-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="3be6f-119">0x80041006</span></span> | <span data-ttu-id="3be6f-120">Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="3be6f-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3be6f-121">0</span><span class="sxs-lookup"><span data-stu-id="3be6f-121">0</span></span> | <span data-ttu-id="3be6f-122">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="3be6f-122">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="3be6f-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3be6f-123">Remarks</span></span>

<span data-ttu-id="3be6f-124">Bu işlev, [IWbemQualifierSet:: BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="3be6f-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="3be6f-125">Bir nesnedeki tüm niteleyicileri numaralandırmak için, bu yöntemin [QualifierSet_Next](qualifierset-next.md)ilk çağrısından önce çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3be6f-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="3be6f-126">Niteleyicilerin numaralandırılma sırası, belirli bir numaralandırma için sabit değer olarak garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="3be6f-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="3be6f-127">`lEnumFlags` bağımsız değişkeni olarak geçirilebilecek bayraklar, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3be6f-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

|<span data-ttu-id="3be6f-128">Sabit</span><span class="sxs-lookup"><span data-stu-id="3be6f-128">Constant</span></span>  |<span data-ttu-id="3be6f-129">Değer</span><span class="sxs-lookup"><span data-stu-id="3be6f-129">Value</span></span>  |<span data-ttu-id="3be6f-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3be6f-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="3be6f-131">0</span><span class="sxs-lookup"><span data-stu-id="3be6f-131">0</span></span> | <span data-ttu-id="3be6f-132">Tüm niteleyicilerin adlarını döndürün.</span><span class="sxs-lookup"><span data-stu-id="3be6f-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="3be6f-133">0x10</span><span class="sxs-lookup"><span data-stu-id="3be6f-133">0x10</span></span> | <span data-ttu-id="3be6f-134">Yalnızca geçerli özelliğe veya nesneye özgü niteleyicilerin adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3be6f-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="3be6f-135">Bir özellik için: yalnızca özelliğe özgü niteleyicileri döndürün (geçersiz kılmalar dahil), sınıf tanımından yayılan niteleyiciler değildir.</span><span class="sxs-lookup"><span data-stu-id="3be6f-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="3be6f-136">Bir örnek için: yalnızca örneğe özgü niteleyici adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3be6f-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="3be6f-137">Bir sınıf için: yalnızca türetmekte olan sınıfa özgü niteleyicileri döndürün.</span><span class="sxs-lookup"><span data-stu-id="3be6f-137">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="3be6f-138">0x20</span><span class="sxs-lookup"><span data-stu-id="3be6f-138">0x20</span></span> | <span data-ttu-id="3be6f-139">Yalnızca başka bir nesneden yayılan niteleyicilerin adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3be6f-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="3be6f-140">Bir özellik için: yalnızca sınıf tanımından bu özelliğe yayılan niteleyicileri döndürün, özelliğin kendisinden değil.</span><span class="sxs-lookup"><span data-stu-id="3be6f-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="3be6f-141">Bir örnek için: yalnızca sınıf tanımından yayılan niteleyicileri döndürün.</span><span class="sxs-lookup"><span data-stu-id="3be6f-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="3be6f-142">Bir sınıf için: yalnızca üst sınıflardan devralınan niteleyici adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3be6f-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="3be6f-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3be6f-143">Requirements</span></span>

<span data-ttu-id="3be6f-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3be6f-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3be6f-145">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="3be6f-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="3be6f-146">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3be6f-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3be6f-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3be6f-147">See also</span></span>

- [<span data-ttu-id="3be6f-148">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3be6f-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
