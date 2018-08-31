---
title: EndEnumeration işlevi (yönetilmeyen API Başvurusu)
description: EndEnumeration işlevi, bir numaralandırma sonlandırır.
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
ms.openlocfilehash: 33c73e58be39a7f1ffa9300947c3ee552231adab
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257499"
---
# <a name="endenumeration-function"></a><span data-ttu-id="e66b7-103">EndEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="e66b7-103">EndEnumeration function</span></span>
<span data-ttu-id="e66b7-104">Bir çağrı ile başlatılan bir numaralandırma sırasını sonlandırıyor [BeginEnumeration işlevi](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="e66b7-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="e66b7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e66b7-105">Syntax</span></span>  
  
```  
HRESULT EndEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="e66b7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e66b7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e66b7-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e66b7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="e66b7-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="e66b7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>


## <a name="return-value"></a><span data-ttu-id="e66b7-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e66b7-109">Return value</span></span>

<span data-ttu-id="e66b7-110">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="e66b7-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e66b7-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="e66b7-111">Constant</span></span>  |<span data-ttu-id="e66b7-112">Değer</span><span class="sxs-lookup"><span data-stu-id="e66b7-112">Value</span></span>  |<span data-ttu-id="e66b7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e66b7-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="e66b7-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e66b7-114">0x80041001</span></span> | <span data-ttu-id="e66b7-115">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e66b7-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e66b7-116">0</span><span class="sxs-lookup"><span data-stu-id="e66b7-116">0</span></span> | <span data-ttu-id="e66b7-117">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="e66b7-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="e66b7-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e66b7-118">Remarks</span></span>

<span data-ttu-id="e66b7-119">Bu işlev bir çağrı sarılır [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e66b7-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="e66b7-120">Bir çağrı `EndEnumeration` işlevi gerekli değildir, ancak numaralandırma ile ilişkili kaynakları serbest nedeniyle önerilir.</span><span class="sxs-lookup"><span data-stu-id="e66b7-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="e66b7-121">Ancak, resoruces otomatik olarak sonraki numaralandırma başlattığınızda veya nesne serbest serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="e66b7-121">However, the resoruces are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="e66b7-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e66b7-122">Requirements</span></span>  
 <span data-ttu-id="e66b7-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e66b7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e66b7-124">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e66b7-124">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e66b7-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e66b7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66b7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e66b7-126">See also</span></span>  
[<span data-ttu-id="e66b7-127">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e66b7-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
