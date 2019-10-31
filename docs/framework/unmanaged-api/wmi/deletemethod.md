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
ms.openlocfilehash: db360584dacf250be2f35e5e6666f8332b39a8dd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120653"
---
# <a name="deletemethod-function"></a><span data-ttu-id="669b9-103">DeleteMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="669b9-103">DeleteMethod function</span></span>
<span data-ttu-id="669b9-104">Belirtilen yöntemi CıM sınıf tanımından siler.</span><span class="sxs-lookup"><span data-stu-id="669b9-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="669b9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="669b9-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="669b9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="669b9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="669b9-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="669b9-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="669b9-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="669b9-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="669b9-109">'ndaki Sınıf tablosundan kaldırılacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="669b9-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="669b9-110">`wszName` geçerli bir `LPCWSTR`işaretçisi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="669b9-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="669b9-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="669b9-111">Return value</span></span>

<span data-ttu-id="669b9-112">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="669b9-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="669b9-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="669b9-113">Constant</span></span>  |<span data-ttu-id="669b9-114">Değer</span><span class="sxs-lookup"><span data-stu-id="669b9-114">Value</span></span>  |<span data-ttu-id="669b9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="669b9-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="669b9-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="669b9-116">0x80041002</span></span> | <span data-ttu-id="669b9-117">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="669b9-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="669b9-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="669b9-118">0x80041006</span></span> | <span data-ttu-id="669b9-119">İşlemi tamamlamaya yetecek bellek yok.</span><span class="sxs-lookup"><span data-stu-id="669b9-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="669b9-120">0</span><span class="sxs-lookup"><span data-stu-id="669b9-120">0</span></span> | <span data-ttu-id="669b9-121">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="669b9-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="669b9-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="669b9-122">Remarks</span></span>

<span data-ttu-id="669b9-123">Bu işlev, [IWbemClassObject::D eleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="669b9-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="669b9-124">Metot silme, CıM örneklerini işaret eden [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçileri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="669b9-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="669b9-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="669b9-125">Requirements</span></span>  
 <span data-ttu-id="669b9-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="669b9-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="669b9-127">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="669b9-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="669b9-128">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="669b9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="669b9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="669b9-129">See also</span></span>

- [<span data-ttu-id="669b9-130">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="669b9-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
