---
title: QualifierSet_BeginEnumeration işlevi (yönetilmeyen API Başvurusu)
description: Bir nesnenin niteleyicileri numaralandırması QualifierSet_BeginEnumeration işlevi sıfırlar.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663434d3e3d44dc0c406e71592651493bd8f8dc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375421"
---
# <a name="qualifiersetbeginenumeration-function"></a><span data-ttu-id="6cbbe-103">QualifierSet_BeginEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="6cbbe-103">QualifierSet_BeginEnumeration function</span></span>

<span data-ttu-id="6cbbe-104">Bir nesnenin niteleyicileri numaralandırması sabit başlangıcına sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="6cbbe-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6cbbe-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a><span data-ttu-id="6cbbe-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6cbbe-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="6cbbe-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="6cbbe-108">[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="6cbbe-109">[in] Bayrakları veya açıklanan değerler Bitsel bir birleşimi [açıklamalar](#remarks) numaralandırmada içerecek şekilde niteleyicileri belirten bölüm.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="6cbbe-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="6cbbe-110">Return value</span></span>

<span data-ttu-id="6cbbe-111">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="6cbbe-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6cbbe-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="6cbbe-112">Constant</span></span>  |<span data-ttu-id="6cbbe-113">Değer</span><span class="sxs-lookup"><span data-stu-id="6cbbe-113">Value</span></span>  |<span data-ttu-id="6cbbe-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cbbe-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6cbbe-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6cbbe-115">0x80041008</span></span> | <span data-ttu-id="6cbbe-116">`lFlags` Parametresi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="6cbbe-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="6cbbe-117">0x8004101d</span></span> | <span data-ttu-id="6cbbe-118">İkinci çağrı `QualifierSet_BeginEnumeration` bir çağrı göndermelisiniz olmadan yapılan [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="6cbbe-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6cbbe-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6cbbe-119">0x80041006</span></span> | <span data-ttu-id="6cbbe-120">Yeni bir numaralandırma başlatmak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6cbbe-121">0</span><span class="sxs-lookup"><span data-stu-id="6cbbe-121">0</span></span> | <span data-ttu-id="6cbbe-122">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-122">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="6cbbe-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6cbbe-123">Remarks</span></span>

<span data-ttu-id="6cbbe-124">Bu işlev bir çağrı sarılır [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="6cbbe-125">Tüm nesne üzerindeki niteleyiciler numaralandırmak için bu yöntem ilk çağırmadan önce çağrılmalıdır [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="6cbbe-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="6cbbe-126">Niteleyiciler numaralandırılan siparişi için belirli bir numaralandırma sabit olması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="6cbbe-127">Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişken tanımlanmış *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

|<span data-ttu-id="6cbbe-128">Sabit</span><span class="sxs-lookup"><span data-stu-id="6cbbe-128">Constant</span></span>  |<span data-ttu-id="6cbbe-129">Değer</span><span class="sxs-lookup"><span data-stu-id="6cbbe-129">Value</span></span>  |<span data-ttu-id="6cbbe-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cbbe-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="6cbbe-131">0</span><span class="sxs-lookup"><span data-stu-id="6cbbe-131">0</span></span> | <span data-ttu-id="6cbbe-132">Tüm niteleyicileri adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="6cbbe-133">0x10</span><span class="sxs-lookup"><span data-stu-id="6cbbe-133">0x10</span></span> | <span data-ttu-id="6cbbe-134">Yalnızca niteleyicileri adları belirli için geçerli bir özellik veya nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="6cbbe-135">Bir özellik için: Yalnızca (geçersiz kılmaları dahil) özelliğine belirli niteleyicileri ve olmayan sınıf tanımından yayılan niteleyicileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="6cbbe-136">Bir örneği için: Yalnızca örnek özgü niteleyicisi adlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="6cbbe-137">Bir sınıf için: Elde sınıf niteleyicileri yalnızca belirli döndürür.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-137">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="6cbbe-138">0x20</span><span class="sxs-lookup"><span data-stu-id="6cbbe-138">0x20</span></span> | <span data-ttu-id="6cbbe-139">Başka bir nesnenin dönüş yalnızca niteleyicileri adlarını yayılır.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="6cbbe-140">Bir özellik için: Bu özellik yalnızca niteleyicileri yayılan dön sınıf tanımı ve özelliğinden olanlar.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="6cbbe-141">Bir örneği için: Sınıf tanımı dönüş niteleyicileri yalnızca yayılır.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="6cbbe-142">Bir sınıf için: Return bu niteleyici adları yalnızca üst sınıflardan devralınır.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="6cbbe-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6cbbe-143">Requirements</span></span>

<span data-ttu-id="6cbbe-144">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cbbe-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="6cbbe-145">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6cbbe-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="6cbbe-146">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6cbbe-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6cbbe-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cbbe-147">See also</span></span>

- [<span data-ttu-id="6cbbe-148">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6cbbe-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)