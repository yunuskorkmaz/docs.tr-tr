---
title: BeginMethodEnumeration işlevi (yönetilmeyen API Başvurusu)
description: BeginMethodEnumeration işlevi, nesne yöntemlerinin bir listesini başlatır
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a7b93bacabdfdd0551418644a7d9a4b1643c3d9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798769"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="93db4-103">BeginEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="93db4-103">BeginEnumeration function</span></span>
<span data-ttu-id="93db4-104">Nesne için kullanılabilen yöntemlerin bir listesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="93db4-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="93db4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93db4-105">Syntax</span></span>  
  
```cpp 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="93db4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93db4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="93db4-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="93db4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="93db4-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="93db4-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="93db4-109">'ndaki Tüm yöntemler için sıfır (0) veya numaralandırmanın kapsamını belirten bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="93db4-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="93db4-110">Aşağıdaki bayraklar, *Wbemcli. h* üstbilgi dosyasında tanımlanmıştır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93db4-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="93db4-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="93db4-111">Constant</span></span>  |<span data-ttu-id="93db4-112">Değer</span><span class="sxs-lookup"><span data-stu-id="93db4-112">Value</span></span>  |<span data-ttu-id="93db4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93db4-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="93db4-114">0x10</span><span class="sxs-lookup"><span data-stu-id="93db4-114">0x10</span></span> | <span data-ttu-id="93db4-115">Sabit listesini sınıfta tanımlanan yöntemlerle sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="93db4-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="93db4-116">0x20</span><span class="sxs-lookup"><span data-stu-id="93db4-116">0x20</span></span> | <span data-ttu-id="93db4-117">Sabit listesini temel sınıflardan devralınan özelliklerle sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="93db4-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="93db4-118">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="93db4-118">Return value</span></span>

<span data-ttu-id="93db4-119">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93db4-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="93db4-120">Sabit</span><span class="sxs-lookup"><span data-stu-id="93db4-120">Constant</span></span>  |<span data-ttu-id="93db4-121">Değer</span><span class="sxs-lookup"><span data-stu-id="93db4-121">Value</span></span>  |<span data-ttu-id="93db4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93db4-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="93db4-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="93db4-123">0x80041008</span></span> | <span data-ttu-id="93db4-124">`lEnnumFlags`sıfır değil ve belirtilen bayraklardan biri değil.</span><span class="sxs-lookup"><span data-stu-id="93db4-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="93db4-125">0</span><span class="sxs-lookup"><span data-stu-id="93db4-125">0</span></span> | <span data-ttu-id="93db4-126">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="93db4-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="93db4-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93db4-127">Remarks</span></span>

<span data-ttu-id="93db4-128">Bu işlev, [IWbemClassObject:: BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="93db4-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="93db4-129">Bu yöntem çağrısı yalnızca geçerli nesne bir sınıf tanımı ise desteklenir.</span><span class="sxs-lookup"><span data-stu-id="93db4-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="93db4-130">Yöntem işleme, örnekleri işaret eden [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçilerinden kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="93db4-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="93db4-131">Yöntemlerin numaralandırıldıkları sıranın belirli bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)örneği için sabit olması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="93db4-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="93db4-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93db4-132">Requirements</span></span>  
 <span data-ttu-id="93db4-133">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93db4-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93db4-134">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="93db4-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="93db4-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="93db4-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93db4-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93db4-136">See also</span></span>

- [<span data-ttu-id="93db4-137">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="93db4-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
