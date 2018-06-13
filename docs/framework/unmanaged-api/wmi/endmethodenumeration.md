---
title: EndMethodEnumeration işlevi (yönetilmeyen API Başvurusu)
description: EndMethodEnumeration işlevi bir yöntem numaralandırma sırası sonlandırır.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d09a2ee278dba7e711891bc6d72043bb3a499dd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458496"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="b575f-103">EndMethodEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="b575f-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="b575f-104">Çağrı kullanmaya bir numaralandırma sırasını sonlandırır [BeginMethodEnumeration işlevi](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b575f-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b575f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b575f-105">Syntax</span></span>  
  
```  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="b575f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b575f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b575f-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b575f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b575f-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="b575f-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="b575f-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b575f-109">Return value</span></span>

<span data-ttu-id="b575f-110">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="b575f-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b575f-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="b575f-111">Constant</span></span>  |<span data-ttu-id="b575f-112">Değer</span><span class="sxs-lookup"><span data-stu-id="b575f-112">Value</span></span>  |<span data-ttu-id="b575f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b575f-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="b575f-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="b575f-114">0x8004101d</span></span> | <span data-ttu-id="b575f-115">Bir iç hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b575f-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b575f-116">0</span><span class="sxs-lookup"><span data-stu-id="b575f-116">0</span></span> | <span data-ttu-id="b575f-117">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="b575f-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b575f-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b575f-118">Remarks</span></span>

<span data-ttu-id="b575f-119">Bu işlev çağrısı sarmalar [IWbemClassObject::EndMethodEnumeration](https://msdn.microsoft.com/library/aa391441(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b575f-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](https://msdn.microsoft.com/library/aa391441(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="b575f-120">Numaralandırma dizisi kullanarak arayan başlar [BeginMethodEnumeration işlevi](beginmethodenumeration.md)ve ardından çağırır [NextMethod işlevi](nextmethod.md )yöntemi dönene kadar `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="b575f-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="b575f-121">İsteğe bağlı olarak çağıran çağırarak sırası tamamlandıktan `EndMethodEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="b575f-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="b575f-122">Arayan numaralandırması erken çağırarak sonlandırabilir `EndMethodEnumeration` dilediğiniz zaman.</span><span class="sxs-lookup"><span data-stu-id="b575f-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="b575f-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b575f-123">Requirements</span></span>  
 <span data-ttu-id="b575f-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b575f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b575f-125">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b575f-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b575f-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b575f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b575f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b575f-127">See also</span></span>  
[<span data-ttu-id="b575f-128">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b575f-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
