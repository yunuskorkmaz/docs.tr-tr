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
ms.openlocfilehash: ab0e28bd21b66f370a1a1e82359fe474574fd7bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987975"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="edae6-102">ICorDebugModule2::ApplyChanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="edae6-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="edae6-103">Meta veri değişiklikleri ve Microsoft Ara dil (MSIL) kodu değişiklikleri çalışan işlemi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="edae6-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edae6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edae6-104">Syntax</span></span>  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edae6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="edae6-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="edae6-106">[in] Delta meta verilerin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="edae6-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="edae6-107">[in] Delta meta veriler içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="edae6-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="edae6-108">Arabelleğin adresi döndürüldüğü [Imetadataemit2::savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="edae6-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="edae6-109">Meta verilerde göreli sanal adreslerine (RVA) göre MSIL kodu başlangıcını olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="edae6-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="edae6-110">[in] MSIL kodu delta bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="edae6-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="edae6-111">[in] Güncelleştirilmiş MSIL kodu içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="edae6-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edae6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="edae6-112">Remarks</span></span>  
 <span data-ttu-id="edae6-113">`pbMetadata` Parametresi, bir özel delta meta veri biçiminde (tarafından çıkış [Imetadataemit2::savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="edae6-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="edae6-114">`pbMetadata` temel olarak önceki meta verileri alır ve bu Bankası'na uygulamak için tek tek değişiklikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="edae6-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="edae6-115">Buna karşılık, `pbIL[`] parametresi güncelleştirilmiş yöntemi için yeni MSIL içerir ve bu yöntem için önceki MSIL tamamen değiştirmek için tasarlanmıştır</span><span class="sxs-lookup"><span data-stu-id="edae6-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="edae6-116">Hata Ayıklayıcı'nın bellekte delta MSIL ve meta veriler oluşturulmuş hata ayıklayıcı çağırır `ApplyChanges` ortak dil çalışma zamanı (CLR) değişiklikleri göndermek için.</span><span class="sxs-lookup"><span data-stu-id="edae6-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="edae6-117">Çalışma zamanı meta veri tablolarından güncelleştirmeleri, yeni MSIL işlemine yerleştirir ve yeni MSIL bir just-ın-time (JIT) derleme ayarlar.</span><span class="sxs-lookup"><span data-stu-id="edae6-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="edae6-118">Hata ayıklayıcı, değişiklikler uygulandığında, çağırmalıdır [Imetadataemit2::resetenclog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) sonraki düzenleme oturumu için hazırlamak için.</span><span class="sxs-lookup"><span data-stu-id="edae6-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="edae6-119">Hata ayıklayıcı, sonra işlemi devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="edae6-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="edae6-120">Her hata ayıklayıcı çağırır `ApplyChanges` delta meta verileri olan bir modülde, aynı zamanda çağırmalıdır [Imetadataemit::applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) tüm Bu modülün meta veri kopyalama dışında bulunan kopyalarını aynı delta meta verilerle değişiklikleri yaymak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="edae6-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="edae6-121">Meta verilerinin bir kopyasını şekilde eşitleme dışı hale gelirse gerçek meta veriler ile hata ayıklayıcı her zaman hemen bu kopyayı atar ve yeni bir kopyasını alın.</span><span class="sxs-lookup"><span data-stu-id="edae6-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="edae6-122">Varsa `ApplyChanges` yöntem başarısız, hata ayıklama oturumu geçersiz bir durumda ve yeniden başlatılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="edae6-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edae6-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="edae6-123">Requirements</span></span>  
 <span data-ttu-id="edae6-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edae6-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edae6-125">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edae6-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edae6-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edae6-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edae6-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edae6-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
