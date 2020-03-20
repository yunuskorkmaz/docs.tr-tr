---
title: SpawnDerivedClass işlevi (Yönetilmeyen API Başvurusu)
description: SpawnDerivedClass işlevi bir nesneden türeyen yeni bir nesne oluşturur.
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
ms.openlocfilehash: e9784f8a024c788823dc702794b2b86eea1827bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174855"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="c7443-103">SpawnDerivedClass fonksiyonu</span><span class="sxs-lookup"><span data-stu-id="c7443-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="c7443-104">Belirtilen bir nesneden yeni türetilmiş bir sınıf nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7443-104">Creates a newly derived class object from a specified object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c7443-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7443-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a><span data-ttu-id="c7443-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7443-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="c7443-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="c7443-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="c7443-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c7443-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="c7443-109">[içinde] Saklı -dır.</span><span class="sxs-lookup"><span data-stu-id="c7443-109">[in] Reserved.</span></span> <span data-ttu-id="c7443-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7443-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="c7443-111">[çıkış] Yeni sınıf tanımı nesnesinin işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="c7443-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="c7443-112">Bir hata oluşursa, yeni bir nesne `ppNewClass` döndürülür ve değiştirilmemiş bırakılır.</span><span class="sxs-lookup"><span data-stu-id="c7443-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="c7443-113">Değeri. `null`</span><span class="sxs-lookup"><span data-stu-id="c7443-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="c7443-114">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="c7443-114">Return value</span></span>

<span data-ttu-id="c7443-115">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c7443-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c7443-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="c7443-116">Constant</span></span>  |<span data-ttu-id="c7443-117">Değer</span><span class="sxs-lookup"><span data-stu-id="c7443-117">Value</span></span>  |<span data-ttu-id="c7443-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7443-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="c7443-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="c7443-119">0x80041001</span></span> | <span data-ttu-id="c7443-120">Genel bir başarısızlık oldu.</span><span class="sxs-lookup"><span data-stu-id="c7443-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="c7443-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="c7443-121">0x80041016</span></span> | <span data-ttu-id="c7443-122">Bir örnekten bir sınıf yumurtlama gibi geçersiz bir işlem istendi.</span><span class="sxs-lookup"><span data-stu-id="c7443-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="c7443-123">Kaynak sınıf windows yönetimi ile tam olarak tanımlanmadı veya kaydedilmedi, bu nedenle yeni bir türetilmiş sınıfa izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="c7443-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c7443-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c7443-124">0x80041006</span></span> | <span data-ttu-id="c7443-125">İşlemi tamamlamak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="c7443-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c7443-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c7443-126">0x80041008</span></span> | <span data-ttu-id="c7443-127">`ppNewClass``null`.</span><span class="sxs-lookup"><span data-stu-id="c7443-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="c7443-128">0</span><span class="sxs-lookup"><span data-stu-id="c7443-128">0</span></span> | <span data-ttu-id="c7443-129">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="c7443-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c7443-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7443-130">Remarks</span></span>

<span data-ttu-id="c7443-131">Bu [işlev, IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) yöntemine bir çağrı yıkLar.</span><span class="sxs-lookup"><span data-stu-id="c7443-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="c7443-132">`ptr`oluşturulan nesnenin ana sınıfı haline gelen bir sınıf tanımı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7443-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="c7443-133">Döndürülen nesne, geçerli nesnenin bir alt sınıfı olur.</span><span class="sxs-lookup"><span data-stu-id="c7443-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="c7443-134">Otomatik `ppNewClass` olarak döndürülen yeni nesne, geçerli nesnenin bir alt sınıfı olur.</span><span class="sxs-lookup"><span data-stu-id="c7443-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="c7443-135">Bu davranış geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="c7443-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="c7443-136">Alt sınıfların (türetilmiş sınıflar) oluşturulabileceği başka bir yöntem yoktur.</span><span class="sxs-lookup"><span data-stu-id="c7443-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7443-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7443-137">Requirements</span></span>  
 <span data-ttu-id="c7443-138">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7443-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7443-139">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c7443-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c7443-140">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c7443-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7443-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7443-141">See also</span></span>

- [<span data-ttu-id="c7443-142">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c7443-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
