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
ms.openlocfilehash: c213f311f1af1e56d0ce24eba3b76f33be541323
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798236"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="fcf7c-103">SpawnDerivedClass işlevi</span><span class="sxs-lookup"><span data-stu-id="fcf7c-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="fcf7c-104">Belirtilen nesneden yeni türetilmiş sınıf nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="fcf7c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcf7c-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="fcf7c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fcf7c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="fcf7c-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="fcf7c-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="fcf7c-109">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-109">[in] Reserved.</span></span> <span data-ttu-id="fcf7c-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="fcf7c-111">dışı Yeni sınıf tanımı nesnesine yönelik işaretçiyi alır.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="fcf7c-112">Bir hata oluşursa, yeni bir nesne döndürülmez ve `ppNewClass` değiştirilmemiş olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="fcf7c-113">Değeri `null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="fcf7c-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="fcf7c-114">Return value</span></span>

<span data-ttu-id="fcf7c-115">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fcf7c-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fcf7c-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="fcf7c-116">Constant</span></span>  |<span data-ttu-id="fcf7c-117">Değer</span><span class="sxs-lookup"><span data-stu-id="fcf7c-117">Value</span></span>  |<span data-ttu-id="fcf7c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcf7c-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="fcf7c-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="fcf7c-119">0x80041001</span></span> | <span data-ttu-id="fcf7c-120">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="fcf7c-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="fcf7c-121">0x80041016</span></span> | <span data-ttu-id="fcf7c-122">Örnekten bir sınıfı oluşturmak gibi geçersiz bir işlem istendi.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="fcf7c-123">Kaynak sınıf tamamen tanımlanmamış veya Windows yönetimine kaydolmadı, bu nedenle yeni bir türetilmiş sınıfa izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="fcf7c-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="fcf7c-124">0x80041006</span></span> | <span data-ttu-id="fcf7c-125">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="fcf7c-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="fcf7c-126">0x80041008</span></span> | <span data-ttu-id="fcf7c-127">`ppNewClass``null`.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="fcf7c-128">0</span><span class="sxs-lookup"><span data-stu-id="fcf7c-128">0</span></span> | <span data-ttu-id="fcf7c-129">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="fcf7c-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcf7c-130">Remarks</span></span>

<span data-ttu-id="fcf7c-131">Bu işlev, [IWbemClassObject:: SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="fcf7c-132">`ptr`oluşturulan nesnenin üst sınıfı haline gelen bir sınıf tanımı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="fcf7c-133">Döndürülen nesne geçerli nesnenin bir alt sınıfı olur.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="fcf7c-134">`ppNewClass` Otomatik olarak döndürülen yeni nesne, geçerli nesnenin bir alt sınıfı olur.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="fcf7c-135">Bu davranışın üzerine yazılamıyor.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="fcf7c-136">Alt sınıfların (türetilmiş sınıflar) oluşturulabilmesi için başka bir yöntem yoktur.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="fcf7c-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcf7c-137">Requirements</span></span>  
 <span data-ttu-id="fcf7c-138">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcf7c-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcf7c-139">**Üst bilgi** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="fcf7c-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="fcf7c-140">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fcf7c-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf7c-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcf7c-141">See also</span></span>

- [<span data-ttu-id="fcf7c-142">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fcf7c-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
