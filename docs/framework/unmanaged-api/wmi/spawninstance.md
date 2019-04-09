---
title: SpawnInstance işlevi (yönetilmeyen API Başvurusu)
description: SpawnInstance işlev bir sınıfın yeni bir örneğini oluşturur.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8056ef18089f56f1f9b6717d505fa3d058957541
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074423"
---
# <a name="spawninstance-function"></a><span data-ttu-id="9074b-103">SpawnInstance işlevi</span><span class="sxs-lookup"><span data-stu-id="9074b-103">SpawnInstance function</span></span>
<span data-ttu-id="9074b-104">Bir sınıfın yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9074b-104">Creates a new instance of a class.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9074b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9074b-105">Syntax</span></span>  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a><span data-ttu-id="9074b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9074b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="9074b-107">[in] Bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="9074b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="9074b-108">[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.</span><span class="sxs-lookup"><span data-stu-id="9074b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="9074b-109">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="9074b-109">[in] Reserved.</span></span> <span data-ttu-id="9074b-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9074b-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="9074b-111">[out] Sınıfının yeni örneğini işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="9074b-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="9074b-112">Bir hata oluşursa, yeni bir nesne değil döndürdü ve `ppNewInstance` sol değiştirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="9074b-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="9074b-113">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="9074b-113">Return value</span></span>

<span data-ttu-id="9074b-114">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="9074b-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9074b-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="9074b-115">Constant</span></span>  |<span data-ttu-id="9074b-116">Değer</span><span class="sxs-lookup"><span data-stu-id="9074b-116">Value</span></span>  |<span data-ttu-id="9074b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9074b-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="9074b-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="9074b-118">0x80041020</span></span> | `ptr` <span data-ttu-id="9074b-119">Geçerli bir sınıf tanımı değil ve yeni örnekleri oluşturma olamaz.</span><span class="sxs-lookup"><span data-stu-id="9074b-119">is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="9074b-120">Windows yönetimiyle çağırarak kayıtlı değil veya eksik olduğu [PutClassWmi](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="9074b-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9074b-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9074b-121">0x80041006</span></span> | <span data-ttu-id="9074b-122">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="9074b-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9074b-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9074b-123">0x80041008</span></span> | `ppNewClass` <span data-ttu-id="9074b-124">olan `null`.</span><span class="sxs-lookup"><span data-stu-id="9074b-124">is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="9074b-125">0</span><span class="sxs-lookup"><span data-stu-id="9074b-125">0</span></span> | <span data-ttu-id="9074b-126">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="9074b-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9074b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9074b-127">Remarks</span></span>

<span data-ttu-id="9074b-128">Bu işlev bir çağrı sarılır [IWbemclassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9074b-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

`ptr` <span data-ttu-id="9074b-129">bir sınıf tanımı Windows yönetiminden alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9074b-129">must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="9074b-130">(Bir örneği bir örnekten UNICODE desteklenir, ancak döndürülen örneği boş unutmayın.) Yeni örnekleri oluşturmak için bu sınıf tanımı kullanın.</span><span class="sxs-lookup"><span data-stu-id="9074b-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="9074b-131">Bir çağrı [PutInstanceWmi](putinstancewmi.md) işlevi, örneği için Windows Yönetim yazmak istiyorsanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9074b-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="9074b-132">Yeni Nesne döndürdü `ppNewClass` otomatik olarak geçerli nesne öğesinin alt sınıfı haline gelir.</span><span class="sxs-lookup"><span data-stu-id="9074b-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="9074b-133">Bu davranışı geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="9074b-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="9074b-134">Alt sınıflar (türetilmiş sınıflar) oluşturulabilmesi için diğer bir yöntem yoktur.</span><span class="sxs-lookup"><span data-stu-id="9074b-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="9074b-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9074b-135">Requirements</span></span>  
 <span data-ttu-id="9074b-136">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9074b-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9074b-137">**Üst bilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9074b-137">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="9074b-138">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9074b-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9074b-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9074b-139">See also</span></span>

- [<span data-ttu-id="9074b-140">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9074b-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
