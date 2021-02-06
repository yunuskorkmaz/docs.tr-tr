---
description: 'Daha fazla bilgi edinin: ICorDebugModule2:: ApplyChanges yöntemi'
title: ICorDebugModule2::ApplyChanges Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
ms.openlocfilehash: 09cbc395c8d656d1dc27de86305432b26308c885
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660082"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="8dbb1-103">ICorDebugModule2::ApplyChanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8dbb1-103">ICorDebugModule2::ApplyChanges Method</span></span>

<span data-ttu-id="8dbb1-104">Meta verilerde yapılan değişiklikleri ve Microsoft ara dili (MSIL) kodundaki değişiklikleri çalışan işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-104">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dbb1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8dbb1-105">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dbb1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8dbb1-106">Parameters</span></span>  

 `cbMetadata`  
 <span data-ttu-id="8dbb1-107">'ndaki Delta meta verilerinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-107">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="8dbb1-108">'ndaki Delta meta verilerini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-108">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="8dbb1-109">Arabelleğin adresi [IMetaDataEmit2:: SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) yönteminden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-109">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="8dbb1-110">Meta verilerdeki göreli sanal adresler (RVA) MSIL kodunun başlangıcına göre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-110">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="8dbb1-111">'ndaki Delta MSIL kodunun bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-111">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="8dbb1-112">'ndaki Güncelleştirilmiş MSIL kodunu içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-112">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dbb1-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8dbb1-113">Remarks</span></span>  

 <span data-ttu-id="8dbb1-114">`pbMetadata`Parametresi özel bir delta meta veri biçiminde ( [IMetaDataEmit2:: SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)olarak çıktı olarak).</span><span class="sxs-lookup"><span data-stu-id="8dbb1-114">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="8dbb1-115">`pbMetadata` önceki meta verileri temel olarak alır ve bu temele uygulanacak tek değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-115">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="8dbb1-116">Buna karşılık, `pbIL[` ] parametresi güncelleştirilmiş yöntemi için yenı MSIL içerir ve bu yöntem için ÖNCEKI MSIL 'i tamamen değiştirmek üzere tasarlanmıştır</span><span class="sxs-lookup"><span data-stu-id="8dbb1-116">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="8dbb1-117">Delta MSIL ve meta veriler hata ayıklayıcının belleğinde oluşturulduğunda, hata ayıklayıcı `ApplyChanges` değişiklikleri ortak dil çalışma zamanına (CLR) göndermek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-117">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="8dbb1-118">Çalışma zamanı, meta veri tablolarını güncelleştirir, yeni MSIL 'yi işleme koyar ve yeni MSIL 'nin tam zamanında (JıT) derlemesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-118">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="8dbb1-119">Değişiklikler uygulandığında, hata ayıklayıcı sonraki Düzenle oturumuna hazırlanmak için [IMetaDataEmit2:: ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) çağrısını çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-119">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="8dbb1-120">Hata ayıklayıcı daha sonra işleme devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-120">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="8dbb1-121">Hata ayıklayıcı, `ApplyChanges` Delta meta verilerini içeren bir modüle her çağırdığında, değişiklikleri yaymak için kullanılan kopya hariç, Bu modülün meta verilerinin tüm kopyalarında aynı Delta meta verileriyle birlikte [ımetadatayayma:: ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) ' ı çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-121">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="8dbb1-122">Meta verilerin bir kopyası gerçek meta verilerle eşitlenmemiş hale gelirse, hata ayıklayıcı her zaman o kopyayı oluşturabilir ve yeni bir kopya alabilir.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-122">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="8dbb1-123">`ApplyChanges`Yöntem başarısız olursa, hata ayıklama oturumu geçersiz bir durumdaydı ve yeniden başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8dbb1-123">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dbb1-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8dbb1-124">Requirements</span></span>  

 <span data-ttu-id="8dbb1-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dbb1-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dbb1-126">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8dbb1-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8dbb1-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8dbb1-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8dbb1-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dbb1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
