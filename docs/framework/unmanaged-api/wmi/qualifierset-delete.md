---
title: QualifierSet_Delete işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Delete işlev adına göre bir niteleyici siler.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ca4cc9fb65d1a4bd8713f969bbda5551ce5a2e2
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46325386"
---
# <a name="qualifiersetdelete-function"></a><span data-ttu-id="8ae26-103">QualifierSet_Delete işlevi</span><span class="sxs-lookup"><span data-stu-id="8ae26-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="8ae26-104">Belirtilen bir niteleyici adıyla siler.</span><span class="sxs-lookup"><span data-stu-id="8ae26-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="8ae26-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ae26-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="8ae26-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ae26-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="8ae26-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="8ae26-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="8ae26-108">[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.</span><span class="sxs-lookup"><span data-stu-id="8ae26-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="8ae26-109">[in] Silinecek niteleyicisi adı.</span><span class="sxs-lookup"><span data-stu-id="8ae26-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="8ae26-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="8ae26-110">Return value</span></span>

<span data-ttu-id="8ae26-111">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="8ae26-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8ae26-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="8ae26-112">Constant</span></span>  |<span data-ttu-id="8ae26-113">Değer</span><span class="sxs-lookup"><span data-stu-id="8ae26-113">Value</span></span>  |<span data-ttu-id="8ae26-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ae26-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8ae26-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="8ae26-115">0x80041008</span></span> | <span data-ttu-id="8ae26-116">`wszName` Parametresi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="8ae26-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="8ae26-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="8ae26-117">0x80041016</span></span> | <span data-ttu-id="8ae26-118">Bu niteleyici silme geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="8ae26-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="8ae26-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="8ae26-119">0x80041002</span></span> | <span data-ttu-id="8ae26-120">Belirtilen niteleyicisi nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="8ae26-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8ae26-121">0</span><span class="sxs-lookup"><span data-stu-id="8ae26-121">0</span></span> | <span data-ttu-id="8ae26-122">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="8ae26-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="8ae26-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="8ae26-123">0x40002</span></span> | <span data-ttu-id="8ae26-124">Yerel geçersiz kılma silindi ve özgün niteleyici üst nesneden kapsam devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="8ae26-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="8ae26-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ae26-125">Remarks</span></span>

<span data-ttu-id="8ae26-126">Bu işlev bir çağrı sarılır [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8ae26-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="8ae26-127">Niteleyici yayma kuralları nedeniyle, belirli bir niteleyici alınan başka bir nesneden ve yalnızca geçerli sınıf veya örnek içinde geçersiz kılındı.</span><span class="sxs-lookup"><span data-stu-id="8ae26-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="8ae26-128">Bu durumda, `QualifierSet_Delete` yöntemi niteleyici özgün devralınan değerine sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="8ae26-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="8ae26-129">İşlev bu durumda, durum kodu döndürür `WBEM_S_RESET_TO_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="8ae26-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="8ae26-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ae26-130">Requirements</span></span>  
 <span data-ttu-id="8ae26-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ae26-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ae26-132">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8ae26-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8ae26-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8ae26-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae26-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ae26-134">See also</span></span>  
[<span data-ttu-id="8ae26-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8ae26-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
