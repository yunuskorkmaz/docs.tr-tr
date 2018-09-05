---
title: GetMethod işlevi (yönetilmeyen API Başvurusu)
description: GetMethod işlevi bir yöntem hakkındaki bilgileri alır.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a913de0ff20fba51295fd8282b58e3953be9bba2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554875"
---
# <a name="getmethod-function"></a><span data-ttu-id="58cbb-103">GetMethod işlevi</span><span class="sxs-lookup"><span data-stu-id="58cbb-103">GetMethod function</span></span>
<span data-ttu-id="58cbb-104">Belirtilen yöntem hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="58cbb-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="58cbb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58cbb-105">Syntax</span></span>  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="58cbb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58cbb-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="58cbb-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="58cbb-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="58cbb-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="58cbb-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="58cbb-109">[in] Yöntem adı.</span><span class="sxs-lookup"><span data-stu-id="58cbb-109">[in] The method name.</span></span> <span data-ttu-id="58cbb-110">Bu parametre olamaz `null` ve geçerli bir işaret etmelidir `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="58cbb-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`  
<span data-ttu-id="58cbb-111">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="58cbb-111">[in] Reserved.</span></span> <span data-ttu-id="58cbb-112">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58cbb-112">This parameter must be 0.</span></span>

`ppInSignature`   
<span data-ttu-id="58cbb-113">[out] Adresine bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yönteme giriş paramteers açıklayan örneği.</span><span class="sxs-lookup"><span data-stu-id="58cbb-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in paramteers to the method.</span></span> <span data-ttu-id="58cbb-114">Bu ayarlanırsa, bu parametre yoksayılır `null`.</span><span class="sxs-lookup"><span data-stu-id="58cbb-114">This parameter is ignored if it is set to `null`.</span></span> 

`ppOutSignature`  
<span data-ttu-id="58cbb-115">[out] Adresine bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yöntemin out Parametreleri açıklayan örneği.</span><span class="sxs-lookup"><span data-stu-id="58cbb-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="58cbb-116">Bu ayarlanırsa, bu parametre yoksayılır `null`.</span><span class="sxs-lookup"><span data-stu-id="58cbb-116">This parameter is ignored if it is set to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="58cbb-117">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="58cbb-117">Return value</span></span>

<span data-ttu-id="58cbb-118">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="58cbb-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="58cbb-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="58cbb-119">Constant</span></span>  |<span data-ttu-id="58cbb-120">Değer</span><span class="sxs-lookup"><span data-stu-id="58cbb-120">Value</span></span>  |<span data-ttu-id="58cbb-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58cbb-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="58cbb-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="58cbb-122">0x80041002</span></span> | <span data-ttu-id="58cbb-123">Belirtilen özellik bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="58cbb-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="58cbb-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="58cbb-124">0x80041006</span></span> | <span data-ttu-id="58cbb-125">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="58cbb-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="58cbb-126">0</span><span class="sxs-lookup"><span data-stu-id="58cbb-126">0</span></span> | <span data-ttu-id="58cbb-127">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="58cbb-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="58cbb-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58cbb-128">Remarks</span></span>

<span data-ttu-id="58cbb-129">Bu işlev bir çağrı sarılır [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="58cbb-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="58cbb-130">Windows Yönetim ayarlayabilirsiniz [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçisine `null` yöntemi hiçbir parametreleri varsa.</span><span class="sxs-lookup"><span data-stu-id="58cbb-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="58cbb-131">İçinde `ppInSignature` ve `ppOutSignature` iç ve dış parametrelerin, sırasıyla özellikleri olarak açıklayan bir `IWbemClassObject` sistem sınıfının örneğini [_upravit](/windows/desktop/WmiSdk/--parameters).</span><span class="sxs-lookup"><span data-stu-id="58cbb-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="58cbb-132">Özelliklerinde `ppInsignature` adlandırılır **Param *** n*burada *n* parametresi yöntem imzası konumudur (gibi `Param1`, `Param2`vb..).</span><span class="sxs-lookup"><span data-stu-id="58cbb-132">The properties in `ppInsignature` are named **Param***n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="58cbb-133">Özelliklerinde `ppOutSignature` olarak da adlandırılır **Param *** n*, ve dönüş değeri olarak adlandırılan **ReturnValue**.</span><span class="sxs-lookup"><span data-stu-id="58cbb-133">The properties in `ppOutSignature` are also named **Param***n*, and the return value is named **ReturnValue**.</span></span> <span data-ttu-id="58cbb-134">Daha fazla bilgi ve örnek için bkz. [IWbemClassObject::GetMethod yöntemi](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span><span class="sxs-lookup"><span data-stu-id="58cbb-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="58cbb-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58cbb-135">Requirements</span></span>  
<span data-ttu-id="58cbb-136">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58cbb-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58cbb-137">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="58cbb-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="58cbb-138">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="58cbb-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58cbb-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58cbb-139">See also</span></span>  
[<span data-ttu-id="58cbb-140">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="58cbb-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
