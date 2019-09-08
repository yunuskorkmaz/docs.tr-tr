---
title: QualifierSet_Delete işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_Delete işlevi bir niteleyiciyi ada göre siler.
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
ms.openlocfilehash: 4bc26a16650a5beecc17898e0421e79536713deb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798330"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="13c02-103">QualifierSet_Delete işlevi</span><span class="sxs-lookup"><span data-stu-id="13c02-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="13c02-104">Belirtilen niteleyiciyi ada göre siler.</span><span class="sxs-lookup"><span data-stu-id="13c02-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="13c02-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13c02-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="13c02-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13c02-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="13c02-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="13c02-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="13c02-108">'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="13c02-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="13c02-109">'ndaki Silinecek niteleyicinin adı.</span><span class="sxs-lookup"><span data-stu-id="13c02-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="13c02-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="13c02-110">Return value</span></span>

<span data-ttu-id="13c02-111">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="13c02-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="13c02-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="13c02-112">Constant</span></span>  |<span data-ttu-id="13c02-113">Değer</span><span class="sxs-lookup"><span data-stu-id="13c02-113">Value</span></span>  |<span data-ttu-id="13c02-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13c02-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="13c02-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="13c02-115">0x80041008</span></span> | <span data-ttu-id="13c02-116">`wszName` Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="13c02-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="13c02-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="13c02-117">0x80041016</span></span> | <span data-ttu-id="13c02-118">Bu niteleyiciyi silme geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="13c02-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="13c02-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="13c02-119">0x80041002</span></span> | <span data-ttu-id="13c02-120">Belirtilen niteleyici bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="13c02-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="13c02-121">0</span><span class="sxs-lookup"><span data-stu-id="13c02-121">0</span></span> | <span data-ttu-id="13c02-122">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="13c02-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="13c02-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="13c02-123">0x40002</span></span> | <span data-ttu-id="13c02-124">Yerel geçersiz kılma silindi ve üst nesneden gelen özgün niteleyici kapsamı sürdürüyor.</span><span class="sxs-lookup"><span data-stu-id="13c02-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="13c02-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13c02-125">Remarks</span></span>

<span data-ttu-id="13c02-126">Bu işlev, [IWbemQualifierSet::D Sil](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="13c02-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="13c02-127">Niteleyici yayma kuralları nedeniyle, belirli bir niteleyici başka bir nesneden devralınmış olabilir ve yalnızca geçerli sınıfta veya örnekte geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="13c02-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="13c02-128">Bu durumda, `QualifierSet_Delete` yöntemi niteleyiciyi özgün devralınmış değerine sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="13c02-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="13c02-129">Bu durumda işlev durum kodunu `WBEM_S_RESET_TO_DEFAULT`döndürür.</span><span class="sxs-lookup"><span data-stu-id="13c02-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="13c02-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13c02-130">Requirements</span></span>  
 <span data-ttu-id="13c02-131">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13c02-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c02-132">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="13c02-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="13c02-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="13c02-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c02-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13c02-134">See also</span></span>

- [<span data-ttu-id="13c02-135">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="13c02-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
