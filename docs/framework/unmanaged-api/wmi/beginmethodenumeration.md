---
title: BeginMethodEnumeration fonksiyonu (Yönetilmeyen API Başvurusu)
description: BeginMethodEnumeration işlevi nesnenin yöntemlerinin numaralandırma başlar
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 876f5810fffab7fa98cd4d46715e13569ab95f6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175050"
---
# <a name="beginmethodenumeration-function"></a><span data-ttu-id="7e16f-103">BeginMethodEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="7e16f-103">BeginMethodEnumeration function</span></span>
<span data-ttu-id="7e16f-104">Nesne için kullanılabilir yöntemlerin numaralandırmasını başlatın.</span><span class="sxs-lookup"><span data-stu-id="7e16f-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="7e16f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e16f-105">Syntax</span></span>  
  
```cpp
HRESULT BeginMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="7e16f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e16f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7e16f-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="7e16f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="7e16f-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7e16f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="7e16f-109">[içinde] Tüm yöntemler için Sıfır (0) veya numaralandırmanın kapsamını belirten bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="7e16f-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="7e16f-110">Aşağıdaki bayraklar *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7e16f-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="7e16f-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="7e16f-111">Constant</span></span>  |<span data-ttu-id="7e16f-112">Değer</span><span class="sxs-lookup"><span data-stu-id="7e16f-112">Value</span></span>  |<span data-ttu-id="7e16f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e16f-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="7e16f-114">0x10</span><span class="sxs-lookup"><span data-stu-id="7e16f-114">0x10</span></span> | <span data-ttu-id="7e16f-115">Numaralandırmayı sınıfın kendisinde tanımlanan yöntemlerle sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="7e16f-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="7e16f-116">0x20</span><span class="sxs-lookup"><span data-stu-id="7e16f-116">0x20</span></span> | <span data-ttu-id="7e16f-117">Numaralandırmayı temel sınıflardan devralınan özelliklerle sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="7e16f-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="7e16f-118">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="7e16f-118">Return value</span></span>

<span data-ttu-id="7e16f-119">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7e16f-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7e16f-120">Sabit</span><span class="sxs-lookup"><span data-stu-id="7e16f-120">Constant</span></span>  |<span data-ttu-id="7e16f-121">Değer</span><span class="sxs-lookup"><span data-stu-id="7e16f-121">Value</span></span>  |<span data-ttu-id="7e16f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e16f-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7e16f-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7e16f-123">0x80041008</span></span> | <span data-ttu-id="7e16f-124">`lEnnumFlags`sıfır değildir ve belirtilen bayraklardan biri değildir.</span><span class="sxs-lookup"><span data-stu-id="7e16f-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7e16f-125">0</span><span class="sxs-lookup"><span data-stu-id="7e16f-125">0</span></span> | <span data-ttu-id="7e16f-126">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="7e16f-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="7e16f-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e16f-127">Remarks</span></span>

<span data-ttu-id="7e16f-128">Bu [işlev, IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="7e16f-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="7e16f-129">Bu yöntem çağrısı yalnızca geçerli nesne bir sınıf tanımı ise desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7e16f-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="7e16f-130">Yöntem işleme örnekleri işaret [iWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçileri kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7e16f-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="7e16f-131">Yöntemleri numaralandırılan sıra, [IWbemClassObject'in](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)belirli bir örneği için değişmez olması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="7e16f-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="7e16f-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e16f-132">Requirements</span></span>  
 <span data-ttu-id="7e16f-133">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e16f-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e16f-134">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7e16f-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7e16f-135">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7e16f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e16f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e16f-136">See also</span></span>

- [<span data-ttu-id="7e16f-137">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7e16f-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
