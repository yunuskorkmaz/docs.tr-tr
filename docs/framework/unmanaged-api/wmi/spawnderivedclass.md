---
title: SpawnDerivedClass işlevi (yönetilmeyen API Başvurusu)
description: SpawnDerivedClass işlevi, bir nesneden türetilen yeni bir nesne oluşturur.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04df65a29584f7e2de44389d815b915a541e38f0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489805"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="3e542-103">SpawnDerivedClass işlevi</span><span class="sxs-lookup"><span data-stu-id="3e542-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="3e542-104">Belirtilen bir nesneden bir yeni türetilmiş bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e542-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="3e542-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e542-105">Syntax</span></span>  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="3e542-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e542-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3e542-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="3e542-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3e542-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="3e542-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="3e542-109">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="3e542-109">[in] Reserved.</span></span> <span data-ttu-id="3e542-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e542-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="3e542-111">[out] Yeni sınıf tanımı nesnesi işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="3e542-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="3e542-112">Bir hata oluşursa, yeni bir nesne değil döndürdü ve `ppNewClass` sol değiştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="3e542-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="3e542-113">Değeri olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="3e542-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="3e542-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="3e542-114">Return value</span></span>

<span data-ttu-id="3e542-115">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="3e542-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3e542-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="3e542-116">Constant</span></span>  |<span data-ttu-id="3e542-117">Değer</span><span class="sxs-lookup"><span data-stu-id="3e542-117">Value</span></span>  |<span data-ttu-id="3e542-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e542-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="3e542-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="3e542-119">0x80041001</span></span> | <span data-ttu-id="3e542-120">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3e542-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="3e542-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="3e542-121">0x80041016</span></span> | <span data-ttu-id="3e542-122">Bir sınıftan bir örnek UNICODE gibi bir geçersiz işlem istendi.</span><span class="sxs-lookup"><span data-stu-id="3e542-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="3e542-123">Kaynak sınıfı tamamen tanımlanan veya yeni bir türetilmiş sınıf izin verilmeyen biçimde ile Windows Yönetimi, kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="3e542-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="3e542-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="3e542-124">0x80041006</span></span> | <span data-ttu-id="3e542-125">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="3e542-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3e542-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3e542-126">0x80041008</span></span> | <span data-ttu-id="3e542-127">`ppNewClass` olan `null`.</span><span class="sxs-lookup"><span data-stu-id="3e542-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="3e542-128">0</span><span class="sxs-lookup"><span data-stu-id="3e542-128">0</span></span> | <span data-ttu-id="3e542-129">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="3e542-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3e542-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e542-130">Remarks</span></span>

<span data-ttu-id="3e542-131">Bu işlev bir çağrı sarılır [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3e542-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="3e542-132">`ptr` üst sınıfın üretilmiş nesne haline gelir. bir sınıf tanımı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e542-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="3e542-133">Döndürülen nesne geçerli nesneye öğesinin olur.</span><span class="sxs-lookup"><span data-stu-id="3e542-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="3e542-134">Yeni Nesne döndürdü `ppNewClass` otomatik olarak geçerli nesne öğesinin alt sınıfı haline gelir.</span><span class="sxs-lookup"><span data-stu-id="3e542-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="3e542-135">Bu davranışı geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="3e542-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="3e542-136">Alt sınıflar (türetilmiş sınıflar) oluşturulabilmesi için diğer bir yöntem yoktur.</span><span class="sxs-lookup"><span data-stu-id="3e542-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e542-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e542-137">Requirements</span></span>  
 <span data-ttu-id="3e542-138">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e542-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e542-139">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3e542-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3e542-140">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3e542-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e542-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e542-141">See also</span></span>  
[<span data-ttu-id="3e542-142">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3e542-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
