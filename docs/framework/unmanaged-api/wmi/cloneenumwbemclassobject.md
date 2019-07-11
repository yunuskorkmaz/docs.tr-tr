---
title: CloneEnumWbemClassObject işlevi (yönetilmeyen API Başvurusu)
description: CloneEnumWbemClassObject işlevi bir numaralandırıcı mantıksal bir kopyasını oluşturur.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab660769a49cf12b129cb7f44b8378053a231f8c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761621"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="50acf-103">CloneEnumWbemClassObject işlevi</span><span class="sxs-lookup"><span data-stu-id="50acf-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="50acf-104">Numaralandırma içindeki geçerli konumu koruma Numaralandırıcı mantıksal bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50acf-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="50acf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50acf-105">Syntax</span></span>

```cpp
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

## <a name="parameters"></a><span data-ttu-id="50acf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50acf-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="50acf-107">[out] Yeni bir işaretçi alır [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="50acf-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="50acf-108">[in] Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="50acf-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="50acf-109">[in] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="50acf-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="50acf-110">[out] Bir işaretçi [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) kopyalanma örneği.</span><span class="sxs-lookup"><span data-stu-id="50acf-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="50acf-111">[in] Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="50acf-111">[in] The user name.</span></span> <span data-ttu-id="50acf-112">Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="50acf-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="50acf-113">[in] Parola.</span><span class="sxs-lookup"><span data-stu-id="50acf-113">[in] The password.</span></span> <span data-ttu-id="50acf-114">Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="50acf-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="50acf-115">`strAuthority`\ [in] kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="50acf-115">`strAuthority`\ [in] The domain name of the user.</span></span> <span data-ttu-id="50acf-116">Bkz: [ConnectServerWmi](connectserverwmi.md) işlevi daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="50acf-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="50acf-117">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="50acf-117">Return value</span></span>

<span data-ttu-id="50acf-118">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="50acf-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="50acf-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="50acf-119">Constant</span></span>  |<span data-ttu-id="50acf-120">Değer</span><span class="sxs-lookup"><span data-stu-id="50acf-120">Value</span></span>  |<span data-ttu-id="50acf-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50acf-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="50acf-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="50acf-122">0x80041001</span></span> | <span data-ttu-id="50acf-123">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="50acf-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="50acf-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="50acf-124">0x80041008</span></span> | <span data-ttu-id="50acf-125">Bir parametre geçersiz.</span><span class="sxs-lookup"><span data-stu-id="50acf-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="50acf-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="50acf-126">0x80041006</span></span> | <span data-ttu-id="50acf-127">Kullanılabilir yeterli bellek işlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="50acf-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="50acf-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="50acf-128">0x80041015</span></span> | <span data-ttu-id="50acf-129">Geçerli işlem WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="50acf-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="50acf-130">0</span><span class="sxs-lookup"><span data-stu-id="50acf-130">0</span></span> | <span data-ttu-id="50acf-131">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="50acf-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="50acf-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50acf-132">Remarks</span></span>

<span data-ttu-id="50acf-133">Bu işlev bir çağrı sarılır [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="50acf-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="50acf-134">Bu yöntem yalnızca bir "en iyi çaba" kopya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50acf-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="50acf-135">Birçok CIM Nesne dinamik doğası nedeniyle yeni Numaralandırıcı kaynak Numaralandırıcı aynı nesne kümesini numaralandırmaz mümkündür.</span><span class="sxs-lookup"><span data-stu-id="50acf-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="50acf-136">İşlev çağrısı başarısız olursa, ek hata bilgileri çağırarak elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="50acf-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="50acf-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="50acf-137">Example</span></span>

<span data-ttu-id="50acf-138">Bir örnek için bkz. [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="50acf-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="50acf-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50acf-139">Requirements</span></span>
 <span data-ttu-id="50acf-140">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50acf-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="50acf-141">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="50acf-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="50acf-142">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="50acf-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="50acf-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50acf-143">See also</span></span>

- [<span data-ttu-id="50acf-144">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="50acf-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
