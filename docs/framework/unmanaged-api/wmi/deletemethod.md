---
title: DeleteMethod işlevi (Yönetilmeyen API Başvurusu)
description: DeleteMethod işlevi belirtilen yöntemi CIM sınıf tanımından siler.
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
ms.openlocfilehash: 4059555d74c0b0f151332ddcf9faedecf238e795
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174998"
---
# <a name="deletemethod-function"></a><span data-ttu-id="c223c-103">DeleteMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="c223c-103">DeleteMethod function</span></span>
<span data-ttu-id="c223c-104">Belirtilen yöntemi CIM sınıfı tanımından siler.</span><span class="sxs-lookup"><span data-stu-id="c223c-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="c223c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c223c-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="c223c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c223c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="c223c-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="c223c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="c223c-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c223c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="c223c-109">[içinde] Sınıf tablosundan kaldırılacak yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="c223c-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="c223c-110">`wszName`geçerli `LPCWSTR`bir işaretçi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c223c-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="c223c-111">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="c223c-111">Return value</span></span>

<span data-ttu-id="c223c-112">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c223c-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c223c-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="c223c-113">Constant</span></span>  |<span data-ttu-id="c223c-114">Değer</span><span class="sxs-lookup"><span data-stu-id="c223c-114">Value</span></span>  |<span data-ttu-id="c223c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c223c-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="c223c-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="c223c-116">0x80041002</span></span> | <span data-ttu-id="c223c-117">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="c223c-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c223c-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c223c-118">0x80041006</span></span> | <span data-ttu-id="c223c-119">İşlemi tamamlamak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="c223c-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="c223c-120">0</span><span class="sxs-lookup"><span data-stu-id="c223c-120">0</span></span> | <span data-ttu-id="c223c-121">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="c223c-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="c223c-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c223c-122">Remarks</span></span>

<span data-ttu-id="c223c-123">Bu [işlev, IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="c223c-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="c223c-124">Yöntem silme CIM örneklerine işaret eden [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçileri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="c223c-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="c223c-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c223c-125">Requirements</span></span>  
 <span data-ttu-id="c223c-126">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c223c-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c223c-127">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c223c-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c223c-128">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c223c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c223c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c223c-129">See also</span></span>

- [<span data-ttu-id="c223c-130">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c223c-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
