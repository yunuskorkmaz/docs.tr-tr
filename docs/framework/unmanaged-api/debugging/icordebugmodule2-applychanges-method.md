---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a406e945a67352bc7f126b40bd56f4a11dd693b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419549"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="99170-102">ICorDebugModule2::ApplyChanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99170-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="99170-103">Meta veri değişiklikleri ve Microsoft Ara dili (MSIL) kod değişiklikleri çalışan işlemi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="99170-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99170-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99170-104">Syntax</span></span>  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99170-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99170-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="99170-106">[in] Delta meta verilerin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="99170-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="99170-107">[in] Delta meta veriler içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="99170-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="99170-108">Arabellek adres alanından döndürülür [Imetadataemit2::savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="99170-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="99170-109">Meta verilerde göreli sanal adresleri (RVAs) MSIL kod başlangıç göreli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="99170-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="99170-110">[in] MSIL kod delta bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="99170-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="99170-111">[in] Güncelleştirilmiş MSIL kodu içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="99170-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99170-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99170-112">Remarks</span></span>  
 <span data-ttu-id="99170-113">`pbMetadata` Parametredir özel delta meta veri biçiminde (tarafından çıkış [Imetadataemit2::savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="99170-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="99170-114">`pbMetadata` temel olarak önceki meta verileri alır ve bu Bankası'na uygulamak için ayrı ayrı değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="99170-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="99170-115">Buna karşılık, `pbIL[`] parametresi güncelleştirilmiş yöntemi için yeni MSIL içerir ve bu yöntem için önceki MSIL tamamen değiştirmek için tasarlanmıştır</span><span class="sxs-lookup"><span data-stu-id="99170-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="99170-116">Hata Ayıklayıcı'nın bellekte delta MSIL ve meta veri oluşturulduğunda, hata ayıklayıcı çağırır `ApplyChanges` ortak dil çalışma zamanı (CLR) değişiklikleri göndermek için.</span><span class="sxs-lookup"><span data-stu-id="99170-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="99170-117">Çalışma zamanı meta veri tablolarından güncelleştirir, yeni MSIL işlemine yerleştirir ve yeni MSIL bir tam zamanında (JIT) derleme ayarlar.</span><span class="sxs-lookup"><span data-stu-id="99170-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="99170-118">Değişikliklerin uygulanması, hata ayıklayıcı çağırmalıdır [Imetadataemit2::resetenclog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) sonraki düzenleme oturumu için hazırlamak için.</span><span class="sxs-lookup"><span data-stu-id="99170-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="99170-119">Hata ayıklayıcı, sonra işlemi devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="99170-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="99170-120">Hata ayıklayıcıyı zaman çağırır `ApplyChanges` delta meta veri olan bir modül üzerinde bu da çağırmalıdır [Imetadataemit::applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) tüm Bu modülün meta kopyalama dışında kendi kopyalarını aynı delta meta verilerle değişiklikleri yaymak üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99170-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="99170-121">Meta verilerinin bir kopyasını şekilde eşitleme hale gelirse gerçek meta verileriyle hata ayıklayıcı her zaman hemen bu kopyayı throw ve yeni bir kopyasını edinin.</span><span class="sxs-lookup"><span data-stu-id="99170-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="99170-122">Varsa `ApplyChanges` yöntem başarısız, hata ayıklama oturumu geçersiz bir durumda ve yeniden başlatılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="99170-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99170-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99170-123">Requirements</span></span>  
 <span data-ttu-id="99170-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99170-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99170-125">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99170-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99170-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99170-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99170-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99170-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
