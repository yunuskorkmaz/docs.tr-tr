---
title: "SpawnInstance işlevi (yönetilmeyen API Başvurusu)"
description: "SpawnInstance işlevi bir sınıfının yeni bir örneğini oluşturur."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 68508f3000e7f4ac481f940ef4c715366c37125c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="spawninstance-function"></a><span data-ttu-id="91950-103">SpawnInstance işlevi</span><span class="sxs-lookup"><span data-stu-id="91950-103">SpawnInstance function</span></span>
<span data-ttu-id="91950-104">Bir sınıfın yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91950-104">Creates a new instance of a class.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="91950-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91950-105">Syntax</span></span>  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a><span data-ttu-id="91950-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91950-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="91950-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="91950-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="91950-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="91950-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="91950-109">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="91950-109">[in] Reserved.</span></span> <span data-ttu-id="91950-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91950-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="91950-111">[out] İşaretçi sınıfının yeni örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="91950-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="91950-112">Bir hata oluşursa, yeni bir nesne değil döndürülen ve `ppNewInstance` sol değiştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="91950-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="91950-113">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="91950-113">Return value</span></span>

<span data-ttu-id="91950-114">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="91950-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="91950-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="91950-115">Constant</span></span>  |<span data-ttu-id="91950-116">Değer</span><span class="sxs-lookup"><span data-stu-id="91950-116">Value</span></span>  |<span data-ttu-id="91950-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91950-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="91950-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="91950-118">0x80041020</span></span> | <span data-ttu-id="91950-119">`ptr`Geçerli bir sınıf tanımı değil ve yeni örnekleri oluşturma olamaz.</span><span class="sxs-lookup"><span data-stu-id="91950-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="91950-120">Eksik ya da, Windows yönetimiyle çağırarak kaydedilmedi [PutClassWmi](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="91950-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="91950-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="91950-121">0x80041006</span></span> | <span data-ttu-id="91950-122">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="91950-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="91950-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="91950-123">0x80041008</span></span> | <span data-ttu-id="91950-124">`ppNewClass`olan `null`.</span><span class="sxs-lookup"><span data-stu-id="91950-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="91950-125">0</span><span class="sxs-lookup"><span data-stu-id="91950-125">0</span></span> | <span data-ttu-id="91950-126">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="91950-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="91950-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91950-127">Remarks</span></span>

<span data-ttu-id="91950-128">Bu işlev çağrısı sarmalar [IWbemclassObject::SpawnInstance](https://msdn.microsoft.com/library/aa391458(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="91950-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](https://msdn.microsoft.com/library/aa391458(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="91950-129">`ptr`bir sınıf tanımı Windows Yönetimi'nden alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="91950-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="91950-130">(Örneğini örneğinden oluşturma desteklenir, ancak döndürülen örneği boştur unutmayın.) Ardından yeni örnekleri oluşturmak için bu sınıf tanımını kullanın.</span><span class="sxs-lookup"><span data-stu-id="91950-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="91950-131">Çağrı [PutInstanceWmi](putinstancewmi.md) işlevi, Windows Yönetimi için örnek yazmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="91950-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>




<span data-ttu-id="91950-132">Döndürülen yeni nesne `ppNewClass` otomatik olarak geçerli nesnenin bir alt sınıfı haline gelir.</span><span class="sxs-lookup"><span data-stu-id="91950-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="91950-133">Bu davranışı geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="91950-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="91950-134">Alt sınıfların (türetilmiş sınıflar) oluşturulabilmesi için diğer bir yöntem yoktur.</span><span class="sxs-lookup"><span data-stu-id="91950-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="91950-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91950-135">Requirements</span></span>  
 <span data-ttu-id="91950-136">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91950-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91950-137">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="91950-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="91950-138">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="91950-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91950-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91950-139">See also</span></span>  
[<span data-ttu-id="91950-140">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="91950-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
