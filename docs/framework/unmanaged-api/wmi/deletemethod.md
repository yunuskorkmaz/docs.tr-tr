---
title: DeleteMethod işlevi (yönetilmeyen API Başvurusu)
description: DeleteMethod işlevi, belirtilen yöntemi CıM sınıf tanımından siler.
ms.date: 11/06/2017
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4db81c4c7e123eed82b3092912b8d871edb54618
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798664"
---
# <a name="deletemethod-function"></a><span data-ttu-id="6ef06-103">DeleteMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="6ef06-103">DeleteMethod function</span></span>
<span data-ttu-id="6ef06-104">Belirtilen yöntemi CıM sınıf tanımından siler.</span><span class="sxs-lookup"><span data-stu-id="6ef06-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="6ef06-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ef06-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="6ef06-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ef06-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6ef06-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="6ef06-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6ef06-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6ef06-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="6ef06-109">'ndaki Sınıf tablosundan kaldırılacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="6ef06-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="6ef06-110">`wszName`geçerli `LPCWSTR`bir işaretçi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ef06-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="6ef06-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="6ef06-111">Return value</span></span>

<span data-ttu-id="6ef06-112">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ef06-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6ef06-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="6ef06-113">Constant</span></span>  |<span data-ttu-id="6ef06-114">Değer</span><span class="sxs-lookup"><span data-stu-id="6ef06-114">Value</span></span>  |<span data-ttu-id="6ef06-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ef06-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="6ef06-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="6ef06-116">0x80041002</span></span> | <span data-ttu-id="6ef06-117">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="6ef06-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6ef06-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6ef06-118">0x80041006</span></span> | <span data-ttu-id="6ef06-119">İşlemi tamamlamaya yetecek bellek yok.</span><span class="sxs-lookup"><span data-stu-id="6ef06-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="6ef06-120">0</span><span class="sxs-lookup"><span data-stu-id="6ef06-120">0</span></span> | <span data-ttu-id="6ef06-121">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="6ef06-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="6ef06-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ef06-122">Remarks</span></span>

<span data-ttu-id="6ef06-123">Bu işlev, [IWbemClassObject::D eleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="6ef06-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="6ef06-124">Metot silme, CıM örneklerini işaret eden [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçileri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6ef06-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="6ef06-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ef06-125">Requirements</span></span>  
 <span data-ttu-id="6ef06-126">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ef06-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ef06-127">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="6ef06-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6ef06-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6ef06-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ef06-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ef06-129">See also</span></span>

- [<span data-ttu-id="6ef06-130">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6ef06-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
