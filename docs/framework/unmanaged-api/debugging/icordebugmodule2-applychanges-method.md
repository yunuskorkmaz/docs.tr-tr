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
ms.openlocfilehash: c324019e1e62701f4f2aaba1c00948b292ba6847
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127908"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="e2a3d-102">ICorDebugModule2::ApplyChanges Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2a3d-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="e2a3d-103">Meta verilerde yapılan değişiklikleri ve Microsoft ara dili (MSIL) kodundaki değişiklikleri çalışan işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2a3d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2a3d-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2a3d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2a3d-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="e2a3d-106">'ndaki Delta meta verilerinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="e2a3d-107">'ndaki Delta meta verilerini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="e2a3d-108">Arabelleğin adresi [IMetaDataEmit2:: SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) yönteminden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="e2a3d-109">Meta verilerdeki göreli sanal adresler (RVA) MSIL kodunun başlangıcına göre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="e2a3d-110">'ndaki Delta MSIL kodunun bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="e2a3d-111">'ndaki Güncelleştirilmiş MSIL kodunu içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2a3d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2a3d-112">Remarks</span></span>  
 <span data-ttu-id="e2a3d-113">`pbMetadata` parametresi özel bir delta meta veri biçiminde ( [IMetaDataEmit2:: SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)olarak çıktı olarak).</span><span class="sxs-lookup"><span data-stu-id="e2a3d-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="e2a3d-114">`pbMetadata`, önceki meta verileri temel olarak alır ve bu temele uygulanacak tek değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="e2a3d-115">Buna karşılık, `pbIL[`] parametresi güncelleştirilmiş yöntemi için yeni MSIL içerir ve bu yöntem için önceki MSIL 'i tamamen değiştirmek üzere tasarlanmıştır</span><span class="sxs-lookup"><span data-stu-id="e2a3d-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="e2a3d-116">Delta MSIL ve meta veriler hata ayıklayıcının belleğinde oluşturulduğunda, hata ayıklayıcı, değişiklikleri ortak dil çalışma zamanına (CLR) göndermek için `ApplyChanges` çağırır.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="e2a3d-117">Çalışma zamanı, meta veri tablolarını güncelleştirir, yeni MSIL 'yi işleme koyar ve yeni MSIL 'nin tam zamanında (JıT) derlemesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="e2a3d-118">Değişiklikler uygulandığında, hata ayıklayıcı sonraki Düzenle oturumuna hazırlanmak için [IMetaDataEmit2:: ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) çağrısını çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="e2a3d-119">Hata ayıklayıcı daha sonra işleme devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="e2a3d-120">Hata ayıklayıcı, Delta meta verilerini içeren bir modülde `ApplyChanges` çağırdığında, değişiklikleri oluşturmak için kullanılan kopya hariç, Bu modülün meta verilerinin tüm kopyalarında aynı Delta meta verileriyle birlikte [ımetadatayayma:: ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) ' i çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="e2a3d-121">Meta verilerin bir kopyası gerçek meta verilerle eşitlenmemiş hale gelirse, hata ayıklayıcı her zaman o kopyayı oluşturabilir ve yeni bir kopya alabilir.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="e2a3d-122">`ApplyChanges` yöntemi başarısız olursa, hata ayıklama oturumu geçersiz bir durumdaydı ve yeniden başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2a3d-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2a3d-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2a3d-123">Requirements</span></span>  
 <span data-ttu-id="e2a3d-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2a3d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2a3d-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e2a3d-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2a3d-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e2a3d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2a3d-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2a3d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
