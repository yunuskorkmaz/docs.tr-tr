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
ms.openlocfilehash: f72e6b1c356077a94b141e40d6efe485e77e7a9e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120187"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="9f3d2-103">SpawnDerivedClass işlevi</span><span class="sxs-lookup"><span data-stu-id="9f3d2-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="9f3d2-104">Belirtilen nesneden yeni türetilmiş sınıf nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9f3d2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f3d2-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="9f3d2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f3d2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="9f3d2-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="9f3d2-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="9f3d2-109">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-109">[in] Reserved.</span></span> <span data-ttu-id="9f3d2-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="9f3d2-111">dışı Yeni sınıf tanımı nesnesine yönelik işaretçiyi alır.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="9f3d2-112">Bir hata oluşursa, yeni bir nesne döndürülmez ve `ppNewClass` değiştirilmemiş olarak bırakılır.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="9f3d2-113">Değeri `null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="9f3d2-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9f3d2-114">Return value</span></span>

<span data-ttu-id="9f3d2-115">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9f3d2-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9f3d2-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="9f3d2-116">Constant</span></span>  |<span data-ttu-id="9f3d2-117">Değer</span><span class="sxs-lookup"><span data-stu-id="9f3d2-117">Value</span></span>  |<span data-ttu-id="9f3d2-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f3d2-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="9f3d2-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="9f3d2-119">0x80041001</span></span> | <span data-ttu-id="9f3d2-120">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="9f3d2-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="9f3d2-121">0x80041016</span></span> | <span data-ttu-id="9f3d2-122">Örnekten bir sınıfı oluşturmak gibi geçersiz bir işlem istendi.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="9f3d2-123">Kaynak sınıf tamamen tanımlanmamış veya Windows yönetimine kaydolmadı, bu nedenle yeni bir türetilmiş sınıfa izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9f3d2-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9f3d2-124">0x80041006</span></span> | <span data-ttu-id="9f3d2-125">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9f3d2-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9f3d2-126">0x80041008</span></span> | <span data-ttu-id="9f3d2-127">`ppNewClass` `null`.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="9f3d2-128">0</span><span class="sxs-lookup"><span data-stu-id="9f3d2-128">0</span></span> | <span data-ttu-id="9f3d2-129">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9f3d2-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f3d2-130">Remarks</span></span>

<span data-ttu-id="9f3d2-131">Bu işlev, [IWbemClassObject:: SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="9f3d2-132">`ptr`, üretilen nesnenin üst sınıfı haline gelen bir sınıf tanımı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="9f3d2-133">Döndürülen nesne geçerli nesnenin bir alt sınıfı olur.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="9f3d2-134">`ppNewClass` ' de döndürülen yeni nesne otomatik olarak geçerli nesnenin bir alt sınıfı olur.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="9f3d2-135">Bu davranışın üzerine yazılamıyor.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="9f3d2-136">Alt sınıfların (türetilmiş sınıflar) oluşturulabilmesi için başka bir yöntem yoktur.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f3d2-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f3d2-137">Requirements</span></span>  
 <span data-ttu-id="9f3d2-138">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f3d2-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f3d2-139">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="9f3d2-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9f3d2-140">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9f3d2-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f3d2-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f3d2-141">See also</span></span>

- [<span data-ttu-id="9f3d2-142">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9f3d2-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
