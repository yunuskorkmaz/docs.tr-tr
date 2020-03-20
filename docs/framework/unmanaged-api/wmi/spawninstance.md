---
title: SpawnInstance işlevi (Yönetilmeyen API Başvurusu)
description: SpawnInstance işlevi sınıfın yeni bir örneğini oluşturur.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a15eb8123c1ee807444bdb4c6fe71cdccc08f434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176727"
---
# <a name="spawninstance-function"></a><span data-ttu-id="f1f18-103">SpawnInstance fonksiyonu</span><span class="sxs-lookup"><span data-stu-id="f1f18-103">SpawnInstance function</span></span>
<span data-ttu-id="f1f18-104">Sınıfın yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1f18-104">Creates a new instance of a class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f1f18-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1f18-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a><span data-ttu-id="f1f18-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1f18-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f1f18-107">[içinde] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="f1f18-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f1f18-108">[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1f18-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="f1f18-109">[içinde] Saklı -dır.</span><span class="sxs-lookup"><span data-stu-id="f1f18-109">[in] Reserved.</span></span> <span data-ttu-id="f1f18-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1f18-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="f1f18-111">[çıkış] İşaretçiyi sınıfın yeni örneğine alır.</span><span class="sxs-lookup"><span data-stu-id="f1f18-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="f1f18-112">Bir hata oluşursa, yeni bir nesne `ppNewInstance` döndürülür ve değiştirilmemiş bırakılır.</span><span class="sxs-lookup"><span data-stu-id="f1f18-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="f1f18-113">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="f1f18-113">Return value</span></span>

<span data-ttu-id="f1f18-114">Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f1f18-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f1f18-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="f1f18-115">Constant</span></span>  |<span data-ttu-id="f1f18-116">Değer</span><span class="sxs-lookup"><span data-stu-id="f1f18-116">Value</span></span>  |<span data-ttu-id="f1f18-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1f18-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="f1f18-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="f1f18-118">0x80041020</span></span> | <span data-ttu-id="f1f18-119">`ptr`geçerli bir sınıf tanımı değildir ve yeni örnekler doğuramaz.</span><span class="sxs-lookup"><span data-stu-id="f1f18-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="f1f18-120">Ya eksik ya da [PutClassWmi](putclasswmi.md)çağırarak Windows Yönetimi kayıtlı olmamıştır.</span><span class="sxs-lookup"><span data-stu-id="f1f18-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f1f18-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f1f18-121">0x80041006</span></span> | <span data-ttu-id="f1f18-122">İşlemi tamamlamak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="f1f18-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f1f18-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f1f18-123">0x80041008</span></span> | <span data-ttu-id="f1f18-124">`ppNewClass``null`.</span><span class="sxs-lookup"><span data-stu-id="f1f18-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f1f18-125">0</span><span class="sxs-lookup"><span data-stu-id="f1f18-125">0</span></span> | <span data-ttu-id="f1f18-126">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="f1f18-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f1f18-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1f18-127">Remarks</span></span>

<span data-ttu-id="f1f18-128">Bu [işlev, IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) yöntemine bir çağrı yıklar.</span><span class="sxs-lookup"><span data-stu-id="f1f18-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="f1f18-129">`ptr`Windows Yönetimi'nden elde edilen bir sınıf tanımı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1f18-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="f1f18-130">(Bir örnekten bir örnek yumurtlamanın desteklenir, ancak döndürülen örnek boş olduğunu unutmayın.) Daha sonra yeni örnekler oluşturmak için bu sınıf tanımını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f1f18-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="f1f18-131">Örneği Windows Yönetimi'ne yazmak istiyorsanız [PutInstanceWmi](putinstancewmi.md) işlevine bir çağrı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f1f18-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="f1f18-132">Otomatik `ppNewClass` olarak döndürülen yeni nesne, geçerli nesnenin bir alt sınıfı olur.</span><span class="sxs-lookup"><span data-stu-id="f1f18-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="f1f18-133">Bu davranış geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="f1f18-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="f1f18-134">Alt sınıfların (türetilmiş sınıflar) oluşturulabileceği başka bir yöntem yoktur.</span><span class="sxs-lookup"><span data-stu-id="f1f18-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="f1f18-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1f18-135">Requirements</span></span>  
 <span data-ttu-id="f1f18-136">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1f18-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1f18-137">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f1f18-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f1f18-138">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f1f18-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f18-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1f18-139">See also</span></span>

- [<span data-ttu-id="f1f18-140">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f1f18-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
