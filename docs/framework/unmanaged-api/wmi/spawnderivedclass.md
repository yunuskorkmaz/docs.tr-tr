---
title: "SpawnDerivedClass işlevi (yönetilmeyen API Başvurusu)"
description: "SpawnDerivedClass işlevi bir nesne türetilen yeni bir nesne oluşturur."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SpawnDerivedClass
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SpawnDerivedClass
helpviewer_keywords: SpawnDerivedClass function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16f9a762c87e1e181202739b70cd978a80864f04
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="75cce-103">SpawnDerivedClass işlevi</span><span class="sxs-lookup"><span data-stu-id="75cce-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="75cce-104">Belirtilen bir nesneden bir yeni türetilmiş bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75cce-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="75cce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75cce-105">Syntax</span></span>  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="75cce-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75cce-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="75cce-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="75cce-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="75cce-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="75cce-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lFlags`  
<span data-ttu-id="75cce-109">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="75cce-109">[in] Reserved.</span></span> <span data-ttu-id="75cce-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75cce-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="75cce-111">[out] Yeni sınıf tanımı nesnesi işaretçisine alır.</span><span class="sxs-lookup"><span data-stu-id="75cce-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="75cce-112">Bir hata oluşursa, yeni bir nesne değil döndürülen ve `ppNewClass` sol değiştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="75cce-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="75cce-113">Değeri olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="75cce-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="75cce-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="75cce-114">Return value</span></span>

<span data-ttu-id="75cce-115">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="75cce-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="75cce-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="75cce-116">Constant</span></span>  |<span data-ttu-id="75cce-117">Değer</span><span class="sxs-lookup"><span data-stu-id="75cce-117">Value</span></span>  |<span data-ttu-id="75cce-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75cce-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="75cce-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="75cce-119">0x80041001</span></span> | <span data-ttu-id="75cce-120">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="75cce-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="75cce-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="75cce-121">0x80041016</span></span> | <span data-ttu-id="75cce-122">Bir örnekten bir sınıfı örnekten oluşturmak gibi geçersiz bir işlem istendi.</span><span class="sxs-lookup"><span data-stu-id="75cce-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="75cce-123">Kaynak sınıf tamamen tanımlanan veya yeni bir türetilmiş sınıf izin şekilde ile Windows Yönetimi, kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="75cce-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="75cce-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="75cce-124">0x80041006</span></span> | <span data-ttu-id="75cce-125">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="75cce-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="75cce-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="75cce-126">0x80041008</span></span> | <span data-ttu-id="75cce-127">`ppNewClass`olan `null`.</span><span class="sxs-lookup"><span data-stu-id="75cce-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="75cce-128">0</span><span class="sxs-lookup"><span data-stu-id="75cce-128">0</span></span> | <span data-ttu-id="75cce-129">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="75cce-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="75cce-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75cce-130">Remarks</span></span>

<span data-ttu-id="75cce-131">Bu işlev çağrısı sarmalar [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="75cce-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="75cce-132">`ptr`oluşturulan nesnenin üst sınıfı haline gelir bir sınıf tanımı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="75cce-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="75cce-133">Döndürülen nesne geçerli nesneye öğesinin bir alt kümesi olur.</span><span class="sxs-lookup"><span data-stu-id="75cce-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="75cce-134">Döndürülen yeni nesne `ppNewClass` otomatik olarak geçerli nesnenin bir alt sınıfı haline gelir.</span><span class="sxs-lookup"><span data-stu-id="75cce-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="75cce-135">Bu davranışı geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="75cce-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="75cce-136">Alt sınıfların (türetilmiş sınıflar) oluşturulabilmesi için diğer bir yöntem yoktur.</span><span class="sxs-lookup"><span data-stu-id="75cce-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="75cce-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75cce-137">Requirements</span></span>  
 <span data-ttu-id="75cce-138">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75cce-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75cce-139">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="75cce-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="75cce-140">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="75cce-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75cce-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75cce-141">See also</span></span>  
[<span data-ttu-id="75cce-142">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="75cce-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
