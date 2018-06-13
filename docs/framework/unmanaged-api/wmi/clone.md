---
title: Kopya işlevi (yönetilmeyen API Başvurusu)
description: Kopya işlevi geçerli bir tam bir kopyası olan yeni bir nesne döndürür.
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5841c89cf394502f68381dfed42593c9debdcb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457322"
---
# <a name="clone-function"></a><span data-ttu-id="792d4-103">Kopya işlevi</span><span class="sxs-lookup"><span data-stu-id="792d4-103">Clone function</span></span>
<span data-ttu-id="792d4-104">Geçerli nesnenin tam bir kopyası olan yeni bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="792d4-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="792d4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="792d4-105">Syntax</span></span>  
  
```  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="792d4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="792d4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="792d4-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="792d4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="792d4-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="792d4-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`ppCopy`  
<span data-ttu-id="792d4-109">[out] Bir tam olan yeni bir nesne, silmenizin `ptr`.</span><span class="sxs-lookup"><span data-stu-id="792d4-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="792d4-110">Bu bağımsız değişken olamaz `null` geçerli nesnenin kopyasını alırsa.</span><span class="sxs-lookup"><span data-stu-id="792d4-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="792d4-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="792d4-111">Return value</span></span>

<span data-ttu-id="792d4-112">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="792d4-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="792d4-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="792d4-113">Constant</span></span>  |<span data-ttu-id="792d4-114">Değer</span><span class="sxs-lookup"><span data-stu-id="792d4-114">Value</span></span>  |<span data-ttu-id="792d4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="792d4-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="792d4-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="792d4-116">0x80041001</span></span> | <span data-ttu-id="792d4-117">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="792d4-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="792d4-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="792d4-118">0x80041008</span></span> | <span data-ttu-id="792d4-119">`null` bir parametre belirtildi ve bu kullanım yasal değil.</span><span class="sxs-lookup"><span data-stu-id="792d4-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="792d4-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="792d4-120">0x80041006</span></span> | <span data-ttu-id="792d4-121">Nesnesini kopyalamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="792d4-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="792d4-122">0</span><span class="sxs-lookup"><span data-stu-id="792d4-122">0</span></span> | <span data-ttu-id="792d4-123">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="792d4-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="792d4-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="792d4-124">Remarks</span></span>

<span data-ttu-id="792d4-125">Bu işlev çağrısı sarmalar [IWbemClassObject::Clone](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="792d4-125">This function wraps a call to the [IWbemClassObject::Clone](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="792d4-126">Kopyalanan nesne başvurusu sayısı 1 olan bir COM nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="792d4-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="792d4-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="792d4-127">Requirements</span></span>  
 <span data-ttu-id="792d4-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="792d4-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="792d4-129">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="792d4-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="792d4-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="792d4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="792d4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="792d4-131">See also</span></span>  
[<span data-ttu-id="792d4-132">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="792d4-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
