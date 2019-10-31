---
title: QualifierSet_EndEnumeration işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_EndEnumeration işlevi bir numaralandırmayı sonlandırır.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 82627fa416f71e123ed2c03bae4584e4433310eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127285"
---
# <a name="qualifierset_endenumeration-function"></a><span data-ttu-id="e06c8-103">QualifierSet_EndEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="e06c8-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="e06c8-104">[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevine yapılan bir çağrıyla başlatılan numaralandırmayı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e06c8-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e06c8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e06c8-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="e06c8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e06c8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e06c8-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e06c8-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="e06c8-108">'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e06c8-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="e06c8-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e06c8-109">Return value</span></span>

<span data-ttu-id="e06c8-110">Bu işlev tarafından döndürülen aşağıdaki değer *Wbemcli. h* üstbilgi dosyasında tanımlanır veya kodunuzda bir sabit olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e06c8-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="e06c8-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="e06c8-111">Constant</span></span>  |<span data-ttu-id="e06c8-112">Değer</span><span class="sxs-lookup"><span data-stu-id="e06c8-112">Value</span></span>  |<span data-ttu-id="e06c8-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e06c8-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e06c8-114">0</span><span class="sxs-lookup"><span data-stu-id="e06c8-114">0</span></span> | <span data-ttu-id="e06c8-115">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="e06c8-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e06c8-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e06c8-116">Remarks</span></span>

<span data-ttu-id="e06c8-117">Bu işlev, [IWbemQualifierSet:: EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="e06c8-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="e06c8-118">Bu çağrı önerilir, ancak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e06c8-118">This call is recommended, but not required.</span></span> <span data-ttu-id="e06c8-119">Numaralandırmada ilişkili kaynakları hemen yayınlar.</span><span class="sxs-lookup"><span data-stu-id="e06c8-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="e06c8-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e06c8-120">Requirements</span></span>  

<span data-ttu-id="e06c8-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e06c8-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="e06c8-122">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="e06c8-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="e06c8-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e06c8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06c8-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e06c8-124">See also</span></span>

- [<span data-ttu-id="e06c8-125">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e06c8-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
