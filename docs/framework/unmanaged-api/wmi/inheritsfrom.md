---
title: DevralmalarFrom işlevi (Yönetilmeyen API Başvurusu)
description: InheritsFrom işlevi, bir sınıfın veya örneğin belirli bir üst sınıftan türediğini belirler.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c735c01c45beda8a1ba988a5c580e6b04ae46312
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174946"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="eb823-103">DevralmalarFrom işlevi</span><span class="sxs-lookup"><span data-stu-id="eb823-103">InheritsFrom function</span></span>
<span data-ttu-id="eb823-104">Geçerli sınıfın veya örneğin belirli bir üst sınıftan türetilip türedip türetilemeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="eb823-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="eb823-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb823-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a><span data-ttu-id="eb823-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb823-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="eb823-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="eb823-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="eb823-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eb823-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="eb823-109">[içinde] Sınıfın adı.</span><span class="sxs-lookup"><span data-stu-id="eb823-109">[in] The name of the class.</span></span> <span data-ttu-id="eb823-110">`wszAncestor`geçerli `LPCWSTR`bir işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="eb823-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="eb823-111">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="eb823-111">Return value</span></span>

<span data-ttu-id="eb823-112">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb823-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="eb823-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="eb823-113">Constant</span></span>  |<span data-ttu-id="eb823-114">Değer</span><span class="sxs-lookup"><span data-stu-id="eb823-114">Value</span></span>  |<span data-ttu-id="eb823-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb823-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="eb823-116">0</span><span class="sxs-lookup"><span data-stu-id="eb823-116">0</span></span> | <span data-ttu-id="eb823-117">Geçerli nesne `wszAncestor`devralır.</span><span class="sxs-lookup"><span data-stu-id="eb823-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="eb823-118">1</span><span class="sxs-lookup"><span data-stu-id="eb823-118">1</span></span> | <span data-ttu-id="eb823-119">Geçerli nesne ' den `wszAncestor`devralmaz.</span><span class="sxs-lookup"><span data-stu-id="eb823-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="eb823-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="eb823-120">0x80041008</span></span> | <span data-ttu-id="eb823-121">`wszAncestor``null`.</span><span class="sxs-lookup"><span data-stu-id="eb823-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="eb823-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb823-122">Remarks</span></span>

<span data-ttu-id="eb823-123">Bu [işlev, IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="eb823-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb823-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb823-124">Requirements</span></span>  
 <span data-ttu-id="eb823-125">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb823-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb823-126">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="eb823-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="eb823-127">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eb823-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb823-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb823-128">See also</span></span>

- [<span data-ttu-id="eb823-129">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="eb823-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
