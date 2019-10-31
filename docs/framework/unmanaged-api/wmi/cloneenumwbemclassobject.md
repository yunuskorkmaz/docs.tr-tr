---
title: CloneEnumWbemClassObject işlevi (yönetilmeyen API Başvurusu)
description: CloneEnumWbemClassObject işlevi bir Numaralandırıcı 'nın mantıksal bir kopyasını oluşturur.
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
ms.openlocfilehash: 9d2442161aaa83693a33f9efc230c09b8c4426e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128729"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="2b9fc-103">CloneEnumWbemClassObject işlevi</span><span class="sxs-lookup"><span data-stu-id="2b9fc-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="2b9fc-104">Bir Numaralandırıcının mantıksal bir kopyasını oluşturur ve geçerli konumunu bir numaralandırıcıda korur.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="2b9fc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b9fc-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="2b9fc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b9fc-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="2b9fc-107">dışı Yeni bir [ıenumwbemclassobject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="2b9fc-108">'ndaki Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="2b9fc-109">'ndaki Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="2b9fc-110">dışı Kopyalanacak [ıenumwbemclassobject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="2b9fc-111">'ndaki Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-111">[in] The user name.</span></span> <span data-ttu-id="2b9fc-112">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="2b9fc-113">'ndaki Parola.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-113">[in] The password.</span></span> <span data-ttu-id="2b9fc-114">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="2b9fc-115">`strAuthority`\ [in] kullanıcının etki alanı adıdır.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-115">`strAuthority`\ [in] The domain name of the user.</span></span> <span data-ttu-id="2b9fc-116">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="2b9fc-117">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="2b9fc-117">Return value</span></span>

<span data-ttu-id="2b9fc-118">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b9fc-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2b9fc-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="2b9fc-119">Constant</span></span>  |<span data-ttu-id="2b9fc-120">Değer</span><span class="sxs-lookup"><span data-stu-id="2b9fc-120">Value</span></span>  |<span data-ttu-id="2b9fc-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b9fc-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="2b9fc-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="2b9fc-122">0x80041001</span></span> | <span data-ttu-id="2b9fc-123">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2b9fc-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2b9fc-124">0x80041008</span></span> | <span data-ttu-id="2b9fc-125">Bir parametre geçersiz.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2b9fc-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2b9fc-126">0x80041006</span></span> | <span data-ttu-id="2b9fc-127">Yeterli bellek yok. işlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="2b9fc-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="2b9fc-128">0x80041015</span></span> | <span data-ttu-id="2b9fc-129">Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2b9fc-130">0</span><span class="sxs-lookup"><span data-stu-id="2b9fc-130">0</span></span> | <span data-ttu-id="2b9fc-131">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="2b9fc-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b9fc-132">Remarks</span></span>

<span data-ttu-id="2b9fc-133">Bu işlev, [ıenumwbemclassobject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="2b9fc-134">Bu yöntem yalnızca bir "en iyi çaba" kopyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="2b9fc-135">Birçok CıM nesnesinin dinamik doğası nedeniyle, yeni Numaralandırıcı kaynak numaralandırıcı olarak aynı nesne kümesini Numaralandırmıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="2b9fc-136">İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="2b9fc-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b9fc-137">Example</span></span>

<span data-ttu-id="2b9fc-138">Bir örnek için, bkz. [ıenumwbemclassobject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b9fc-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b9fc-139">Requirements</span></span>
 <span data-ttu-id="2b9fc-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b9fc-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="2b9fc-141">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="2b9fc-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="2b9fc-142">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2b9fc-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2b9fc-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b9fc-143">See also</span></span>

- [<span data-ttu-id="2b9fc-144">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2b9fc-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
