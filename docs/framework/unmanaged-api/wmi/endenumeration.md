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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0065dcd25430e102b965d5598c7e9a04c7857eb3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798818"
---
# <a name="endenumeration-function"></a><span data-ttu-id="3b9d2-103">EndEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="3b9d2-103">EndEnumeration function</span></span>

<span data-ttu-id="3b9d2-104">[Beginenumeration işlevi](beginenumeration.md)çağrısıyla başlatılan bir numaralandırma dizisini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="3b9d2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b9d2-105">Syntax</span></span>

```cpp
HRESULT EndEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```

## <a name="parameters"></a><span data-ttu-id="3b9d2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b9d2-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="3b9d2-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="3b9d2-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="3b9d2-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="3b9d2-109">Return value</span></span>

<span data-ttu-id="3b9d2-110">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3b9d2-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3b9d2-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="3b9d2-111">Constant</span></span>  |<span data-ttu-id="3b9d2-112">Değer</span><span class="sxs-lookup"><span data-stu-id="3b9d2-112">Value</span></span>  |<span data-ttu-id="3b9d2-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b9d2-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="3b9d2-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="3b9d2-114">0x80041001</span></span> | <span data-ttu-id="3b9d2-115">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3b9d2-116">0</span><span class="sxs-lookup"><span data-stu-id="3b9d2-116">0</span></span> | <span data-ttu-id="3b9d2-117">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-117">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="3b9d2-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b9d2-118">Remarks</span></span>

<span data-ttu-id="3b9d2-119">Bu işlev, [IWbemClassObject:: EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="3b9d2-120">`EndEnumeration` İşleve yapılan bir çağrı gerekli değildir, ancak numaralandırmada ilişkili kaynakları yayınlamadığından önerilir.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="3b9d2-121">Ancak, sonraki numaralandırma başlatıldığında veya nesne serbest bırakıldığında kaynaklar otomatik olarak serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-121">However, the resources are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="3b9d2-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b9d2-122">Requirements</span></span>

<span data-ttu-id="3b9d2-123">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b9d2-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3b9d2-124">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="3b9d2-124">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="3b9d2-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3b9d2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3b9d2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-126">See also</span></span>

- [<span data-ttu-id="3b9d2-127">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3b9d2-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
