---
title: ICorDebugModule::GetMetaDataInterface Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
ms.openlocfilehash: fb96949e22b4edfc0e64780a54bb38da44eb8369
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129542"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="73202-102">ICorDebugModule::GetMetaDataInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="73202-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="73202-103">Modülün meta verilerini incelemek için kullanılabilecek bir meta veri arabirimi nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="73202-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73202-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73202-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73202-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73202-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="73202-106">'ndaki Meta veri arabirimini belirten başvuru Kımlığı.</span><span class="sxs-lookup"><span data-stu-id="73202-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="73202-107">dışı [Meta veri arabirimlerinden](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)biri olan `T:IUnknown` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="73202-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73202-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73202-108">Remarks</span></span>  
 <span data-ttu-id="73202-109">Hata ayıklayıcı, Bu modülün düzenlenmesi için yapması gereken bir modül için özgün meta verilerin bir kopyasını oluşturmak üzere `GetMetaDataInterface` yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="73202-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="73202-110">Hata ayıklayıcı, modül için bir [ımetadatayayma](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) arabirimi nesnesi almak üzere `GetMetaDataInterface` çağırır, ardından modülün meta verilerinin bir kopyasını belleğe kaydetmek Için [ımetadatayayma:: SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="73202-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73202-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73202-111">Requirements</span></span>  
 <span data-ttu-id="73202-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73202-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73202-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73202-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73202-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="73202-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73202-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73202-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73202-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73202-116">See also</span></span>

- [<span data-ttu-id="73202-117">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="73202-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
