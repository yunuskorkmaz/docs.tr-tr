---
title: QualifierSet_Delete işlevi (Yönetilmeyen API Başvurusu)
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
ms.openlocfilehash: 0d2a02ba9d89ba16e776bb73563eaebf8a92f1fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174907"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="e4e1b-103">QualifierSet_Delete fonksiyonu</span><span class="sxs-lookup"><span data-stu-id="e4e1b-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="e4e1b-104">Belirtilen bir niteleyiciyi ada göre siler.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e4e1b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4e1b-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="e4e1b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4e1b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e4e1b-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="e4e1b-108">`ptr`[içinde] [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="e4e1b-109">`wszName`[içinde] Silinecek varamanın adı.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-109">`wszName` [in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="e4e1b-110">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="e4e1b-110">Return value</span></span>

<span data-ttu-id="e4e1b-111">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e4e1b-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e4e1b-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="e4e1b-112">Constant</span></span>  |<span data-ttu-id="e4e1b-113">Değer</span><span class="sxs-lookup"><span data-stu-id="e4e1b-113">Value</span></span>  |<span data-ttu-id="e4e1b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4e1b-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e4e1b-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e4e1b-115">0x80041008</span></span> | <span data-ttu-id="e4e1b-116">Parametre `wszName` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="e4e1b-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="e4e1b-117">0x80041016</span></span> | <span data-ttu-id="e4e1b-118">Bu elemeyi silerken yasa dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e4e1b-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="e4e1b-119">0x80041002</span></span> | <span data-ttu-id="e4e1b-120">Belirtilen niteleyici bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e4e1b-121">0</span><span class="sxs-lookup"><span data-stu-id="e4e1b-121">0</span></span> | <span data-ttu-id="e4e1b-122">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="e4e1b-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="e4e1b-123">0x40002</span></span> | <span data-ttu-id="e4e1b-124">Yerel geçersiz kılma silindi ve üst nesneden özgün niteleyici kapsam devam etti.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e4e1b-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4e1b-125">Remarks</span></span>

<span data-ttu-id="e4e1b-126">Bu işlev [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="e4e1b-127">Niteleyici yayılma kuralları nedeniyle, belirli bir niteleyici başka bir nesneden devralınmış ve yalnızca geçerli sınıf veya örnekte geçersiz kılınmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="e4e1b-128">Bu durumda, `QualifierSet_Delete` yöntem niteleyiciyi özgün devralınan değerine sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="e4e1b-129">Bu durumda işlev durum kodunu `WBEM_S_RESET_TO_DEFAULT`döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="e4e1b-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4e1b-130">Requirements</span></span>  
 <span data-ttu-id="e4e1b-131">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4e1b-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4e1b-132">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e4e1b-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e4e1b-133">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e4e1b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e1b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4e1b-134">See also</span></span>

- [<span data-ttu-id="e4e1b-135">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e4e1b-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
