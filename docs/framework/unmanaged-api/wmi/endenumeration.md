---
title: EndEnumeration işlevi (yönetilmeyen API Başvurusu)
description: EndEnumeration işlevi bir numaralandırmayı sonlandırır.
ms.date: 11/06/2017
api_name:
- EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndEnumeration
helpviewer_keywords:
- EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b9fd1f094c8fb56c94421a07437aa25a3549c487
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132040"
---
# <a name="endenumeration-function"></a><span data-ttu-id="25072-103">EndEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="25072-103">EndEnumeration function</span></span>

<span data-ttu-id="25072-104">[Beginenumeration işlevi](beginenumeration.md)çağrısıyla başlatılan bir numaralandırma dizisini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="25072-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="25072-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25072-105">Syntax</span></span>

```cpp
HRESULT EndEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```

## <a name="parameters"></a><span data-ttu-id="25072-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25072-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="25072-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="25072-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="25072-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="25072-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="25072-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="25072-109">Return value</span></span>

<span data-ttu-id="25072-110">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="25072-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="25072-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="25072-111">Constant</span></span>  |<span data-ttu-id="25072-112">Değer</span><span class="sxs-lookup"><span data-stu-id="25072-112">Value</span></span>  |<span data-ttu-id="25072-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25072-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="25072-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="25072-114">0x80041001</span></span> | <span data-ttu-id="25072-115">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="25072-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="25072-116">0</span><span class="sxs-lookup"><span data-stu-id="25072-116">0</span></span> | <span data-ttu-id="25072-117">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="25072-117">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="25072-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25072-118">Remarks</span></span>

<span data-ttu-id="25072-119">Bu işlev, [IWbemClassObject:: EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="25072-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="25072-120">`EndEnumeration` işlevine yapılan bir çağrı gerekli değildir, ancak numaralandırmada ilişkili kaynakları yayınlamadığından bu önerilir.</span><span class="sxs-lookup"><span data-stu-id="25072-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="25072-121">Ancak, sonraki numaralandırma başlatıldığında veya nesne serbest bırakıldığında kaynaklar otomatik olarak serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="25072-121">However, the resources are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="25072-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25072-122">Requirements</span></span>

<span data-ttu-id="25072-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25072-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="25072-124">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="25072-124">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="25072-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="25072-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="25072-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25072-126">See also</span></span>

- [<span data-ttu-id="25072-127">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="25072-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
