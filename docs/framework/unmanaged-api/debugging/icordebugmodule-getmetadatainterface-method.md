---
title: ICorDebugModule::GetMetaDataInterface Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetMetaDataInterface
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f4b1944c68db0cbdd8eb49e10433defc953e4494
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="94888-102">ICorDebugModule::GetMetaDataInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="94888-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="94888-103">Modül için meta verileri incelemek için kullanılan bir meta veri arabirimi nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="94888-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94888-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94888-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94888-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94888-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="94888-106">[in] Meta veri arabirimi belirtir başvuru kimliği.</span><span class="sxs-lookup"><span data-stu-id="94888-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="94888-107">[out] Adresine bir işaretçi bir `T:IUnknown` biri nesne [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="94888-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94888-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94888-108">Remarks</span></span>  
 <span data-ttu-id="94888-109">Hata ayıklayıcı kullanabilirsiniz `GetMetaDataInterface` yöntemi orijinal meta verileri bu modül düzenlemek için yapmanız gerekir bir modül için bir kopyasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="94888-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="94888-110">Hata ayıklayıcı çağrıları `GetMetaDataInterface` almak için bir [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) arabirimi nesnesi için modülü, daha sonra çağırır [Imetadataemit::savetomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) bellek modülün meta verilerinin bir kopyasını kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="94888-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94888-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94888-111">Requirements</span></span>  
 <span data-ttu-id="94888-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94888-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94888-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94888-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94888-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94888-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94888-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94888-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94888-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94888-116">See Also</span></span>  
 [<span data-ttu-id="94888-117">Meta veriler</span><span class="sxs-lookup"><span data-stu-id="94888-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
