---
title: Clone işlevi (yönetilmeyen API Başvurusu)
description: Kopyalama işlevi için geçerli bir tam bir kopyası olan yeni bir nesne döndürür.
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
ms.openlocfilehash: bf9cca10a580af7991889de6993e931347fc27ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120970"
---
# <a name="clone-function"></a><span data-ttu-id="d17ca-103">Clone işlevi</span><span class="sxs-lookup"><span data-stu-id="d17ca-103">Clone function</span></span>
<span data-ttu-id="d17ca-104">Geçerli nesnenin tam bir kopyası olan yeni bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="d17ca-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d17ca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d17ca-105">Syntax</span></span>  
  
```  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="d17ca-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d17ca-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d17ca-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="d17ca-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d17ca-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="d17ca-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="d17ca-109">[out] Tam olan yeni bir nesne, silmenizin `ptr`.</span><span class="sxs-lookup"><span data-stu-id="d17ca-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="d17ca-110">Bu bağımsız değişkeni olamaz `null` geçerli nesnenin bir kopyasını alırsa.</span><span class="sxs-lookup"><span data-stu-id="d17ca-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="d17ca-111">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d17ca-111">Return value</span></span>

<span data-ttu-id="d17ca-112">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="d17ca-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d17ca-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="d17ca-113">Constant</span></span>  |<span data-ttu-id="d17ca-114">Değer</span><span class="sxs-lookup"><span data-stu-id="d17ca-114">Value</span></span>  |<span data-ttu-id="d17ca-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d17ca-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="d17ca-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="d17ca-116">0x80041001</span></span> | <span data-ttu-id="d17ca-117">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d17ca-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d17ca-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d17ca-118">0x80041008</span></span> | `null` <span data-ttu-id="d17ca-119">bir parametre olarak belirtildi ve bu kullanımı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="d17ca-119">was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d17ca-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d17ca-120">0x80041006</span></span> | <span data-ttu-id="d17ca-121">Nesneyi kopyalamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="d17ca-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="d17ca-122">0</span><span class="sxs-lookup"><span data-stu-id="d17ca-122">0</span></span> | <span data-ttu-id="d17ca-123">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="d17ca-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d17ca-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d17ca-124">Remarks</span></span>

<span data-ttu-id="d17ca-125">Bu işlev bir çağrı sarılır [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d17ca-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="d17ca-126">Kopyalanan nesne başvuru sayısı 1 olan bir COM nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="d17ca-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="d17ca-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d17ca-127">Requirements</span></span>  
 <span data-ttu-id="d17ca-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d17ca-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d17ca-129">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d17ca-129">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="d17ca-130">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d17ca-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d17ca-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d17ca-131">See also</span></span>

- [<span data-ttu-id="d17ca-132">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d17ca-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
