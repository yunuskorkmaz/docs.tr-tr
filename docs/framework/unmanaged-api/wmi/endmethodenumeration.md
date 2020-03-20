---
title: EndMethodEnumeration fonksiyonu (Yönetilmeyen API Başvurusu)
description: EndMethodEnumeration işlevi bir yöntem numaralandırma dizisini sonlandırır.
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 63667d0668f905ded2aedd961be0d1831faf838c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175011"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="59847-103">EndMethodEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="59847-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="59847-104">[BeginMethodEnumeration işlevine](beginmethodenumeration.md)yapılan çağrıyla başlayan numaralandırma dizisini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="59847-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="59847-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59847-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a><span data-ttu-id="59847-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59847-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="59847-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="59847-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="59847-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="59847-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="59847-109">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="59847-109">Return value</span></span>

<span data-ttu-id="59847-110">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="59847-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="59847-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="59847-111">Constant</span></span>  |<span data-ttu-id="59847-112">Değer</span><span class="sxs-lookup"><span data-stu-id="59847-112">Value</span></span>  |<span data-ttu-id="59847-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59847-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="59847-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="59847-114">0x8004101d</span></span> | <span data-ttu-id="59847-115">Bir iç hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="59847-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="59847-116">0</span><span class="sxs-lookup"><span data-stu-id="59847-116">0</span></span> | <span data-ttu-id="59847-117">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="59847-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="59847-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59847-118">Remarks</span></span>

<span data-ttu-id="59847-119">Bu [işlev, IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) yöntemine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="59847-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="59847-120">Arayan, [BeginMethodEnumeration işlevini](beginmethodenumeration.md)kullanarak numaralandırma sırasını başlatır ve yöntem dönene `WBEM_S_NO_MORE_DATA`kadar [NextMethod işlevini](nextmethod.md )çağırır.</span><span class="sxs-lookup"><span data-stu-id="59847-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="59847-121">Arayan isteğe bağlı olarak arayarak `EndMethodEnumeration`sırayı tamamlar.</span><span class="sxs-lookup"><span data-stu-id="59847-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="59847-122">Arayan, herhangi bir zamanda arayarak `EndMethodEnumeration` numaralandırmayı erken sonlandırabilir.</span><span class="sxs-lookup"><span data-stu-id="59847-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="59847-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59847-123">Requirements</span></span>  
 <span data-ttu-id="59847-124">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59847-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59847-125">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="59847-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="59847-126">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="59847-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59847-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59847-127">See also</span></span>

- [<span data-ttu-id="59847-128">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="59847-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
