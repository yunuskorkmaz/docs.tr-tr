---
title: "CloneEnumWbemClassObject işlevi (yönetilmeyen API Başvurusu)"
description: "CloneEnumWbemClassObject işlevi bir numaralandırıcı mantıksal bir kopyasını oluşturur."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CloneEnumWbemClassObject
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CloneEnumWbemClassObject
helpviewer_keywords: CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7a4103a0103a334a0e5eace32d8fcf1b365917b8
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="fe071-103">CloneEnumWbemClassObject işlevi</span><span class="sxs-lookup"><span data-stu-id="fe071-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="fe071-104">Numaralandırma içindeki geçerli konumunu koruyarak bir numaralandırıcı mantıksal bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fe071-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="fe071-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe071-105">Syntax</span></span>  
  
```  
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```  

## <a name="parameters"></a><span data-ttu-id="fe071-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe071-106">Parameters</span></span>

`ppEnum`  
<span data-ttu-id="fe071-107">[out] Yeni bir işaretçi alır [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="fe071-107">[out] Receives a pointer to a new [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx).</span></span>

`authLevel`  
<span data-ttu-id="fe071-108">[in] Kimlik doğrulama düzeyi.</span><span class="sxs-lookup"><span data-stu-id="fe071-108">[in] The authorization level.</span></span>

<span data-ttu-id="fe071-109">`impLevel`[in] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="fe071-109">`impLevel` [in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`  
<span data-ttu-id="fe071-110">[out] Bir işaretçi [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) kopyalanma örneği.</span><span class="sxs-lookup"><span data-stu-id="fe071-110">[out] A pointer to the [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx) instance to be cloned.</span></span>

`strUser`   
<span data-ttu-id="fe071-111">[in] Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="fe071-111">[in] The user name.</span></span> <span data-ttu-id="fe071-112">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="fe071-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="fe071-113">[in] Parola.</span><span class="sxs-lookup"><span data-stu-id="fe071-113">[in] The password.</span></span> <span data-ttu-id="fe071-114">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="fe071-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="fe071-115">[in] Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="fe071-115">[in] The domain name of the user.</span></span> <span data-ttu-id="fe071-116">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="fe071-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="fe071-117">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="fe071-117">Return value</span></span>

<span data-ttu-id="fe071-118">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="fe071-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fe071-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="fe071-119">Constant</span></span>  |<span data-ttu-id="fe071-120">Değer</span><span class="sxs-lookup"><span data-stu-id="fe071-120">Value</span></span>  |<span data-ttu-id="fe071-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe071-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="fe071-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="fe071-122">0x80041001</span></span> | <span data-ttu-id="fe071-123">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fe071-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="fe071-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="fe071-124">0x80041008</span></span> | <span data-ttu-id="fe071-125">Bir parametre geçersiz.</span><span class="sxs-lookup"><span data-stu-id="fe071-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="fe071-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="fe071-126">0x80041006</span></span> | <span data-ttu-id="fe071-127">Yeterli kullanılabilir bellek yok işlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="fe071-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="fe071-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="fe071-128">0x80041015</span></span> | <span data-ttu-id="fe071-129">Geçerli işlem ile WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="fe071-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="fe071-130">0</span><span class="sxs-lookup"><span data-stu-id="fe071-130">0</span></span> | <span data-ttu-id="fe071-131">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="fe071-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="fe071-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe071-132">Remarks</span></span>

<span data-ttu-id="fe071-133">Bu işlev çağrısı sarmalar [IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fe071-133">This function wraps a call to the [IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="fe071-134">Bu yöntem yalnızca bir "en iyi çaba" kopya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fe071-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="fe071-135">Birçok CIM Nesne dinamik yapısı nedeniyle, yeni Numaralandırıcı kaynak Numaralandırıcı aynı nesne kümesini numaralandırma olmayan mümkündür.</span><span class="sxs-lookup"><span data-stu-id="fe071-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>  

<span data-ttu-id="fe071-136">İşlev çağrısı başarısız olursa, çağırarak ek hata bilgileri elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="fe071-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="fe071-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe071-137">Example</span></span>

<span data-ttu-id="fe071-138">Bir örnek için bkz: [IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fe071-138">For an example, see the [IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fe071-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe071-139">Requirements</span></span>  
 <span data-ttu-id="fe071-140">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe071-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe071-141">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fe071-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="fe071-142">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fe071-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe071-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe071-143">See also</span></span>  
[<span data-ttu-id="fe071-144">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fe071-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
