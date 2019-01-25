---
title: BeginMethodEnumeration işlevi (yönetilmeyen API Başvurusu)
description: BeginMethodEnumeration işlevi nesnesinin yöntemlerini numaralandırması başlar.
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
ms.openlocfilehash: b682904a8e7f2eafa8833d784febe7b3b2a1e5f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611091"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="d37b7-103">BeginEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="d37b7-103">BeginEnumeration function</span></span>
<span data-ttu-id="d37b7-104">Nesne için kullanılabilen yöntemler numaralandırması başlar.</span><span class="sxs-lookup"><span data-stu-id="d37b7-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="d37b7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d37b7-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="d37b7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d37b7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d37b7-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="d37b7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d37b7-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="d37b7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="d37b7-109">[in] Tüm yöntemler veya numaralandırma kapsamını belirten bir bayrak için sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="d37b7-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="d37b7-110">Aşağıdaki bayraklar tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="d37b7-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="d37b7-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="d37b7-111">Constant</span></span>  |<span data-ttu-id="d37b7-112">Değer</span><span class="sxs-lookup"><span data-stu-id="d37b7-112">Value</span></span>  |<span data-ttu-id="d37b7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d37b7-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="d37b7-114">0x10</span><span class="sxs-lookup"><span data-stu-id="d37b7-114">0x10</span></span> | <span data-ttu-id="d37b7-115">Sabit listesi sınıfı içinde tanımlanan yöntemleri sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="d37b7-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="d37b7-116">0x20</span><span class="sxs-lookup"><span data-stu-id="d37b7-116">0x20</span></span> | <span data-ttu-id="d37b7-117">Temel sınıftan devralınan özellikler için sabit sınırlar.</span><span class="sxs-lookup"><span data-stu-id="d37b7-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="d37b7-118">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d37b7-118">Return value</span></span>

<span data-ttu-id="d37b7-119">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="d37b7-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d37b7-120">Sabit</span><span class="sxs-lookup"><span data-stu-id="d37b7-120">Constant</span></span>  |<span data-ttu-id="d37b7-121">Değer</span><span class="sxs-lookup"><span data-stu-id="d37b7-121">Value</span></span>  |<span data-ttu-id="d37b7-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d37b7-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d37b7-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d37b7-123">0x80041008</span></span> | <span data-ttu-id="d37b7-124">`lEnnumFlags` sıfır olmayan ve belirtilen bayraklar biri değil.</span><span class="sxs-lookup"><span data-stu-id="d37b7-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d37b7-125">0</span><span class="sxs-lookup"><span data-stu-id="d37b7-125">0</span></span> | <span data-ttu-id="d37b7-126">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="d37b7-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d37b7-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d37b7-127">Remarks</span></span>

<span data-ttu-id="d37b7-128">Bu işlev bir çağrı sarılır [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d37b7-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="d37b7-129">Geçerli nesne bir sınıf tanımı ise bu yöntem çağrısı yalnızca desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d37b7-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="d37b7-130">Yöntem işleme kullanılabilir değil [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneklerine işaret eden işaretçilerin.</span><span class="sxs-lookup"><span data-stu-id="d37b7-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="d37b7-131">Yöntemleri numaralandırılan sırasını belirli bir örneği için sabit olması garanti [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="d37b7-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="d37b7-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d37b7-132">Requirements</span></span>  
 <span data-ttu-id="d37b7-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d37b7-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d37b7-134">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d37b7-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d37b7-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d37b7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d37b7-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d37b7-136">See also</span></span>
- [<span data-ttu-id="d37b7-137">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d37b7-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
