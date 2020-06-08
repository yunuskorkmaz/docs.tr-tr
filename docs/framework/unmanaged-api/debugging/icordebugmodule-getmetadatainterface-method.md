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
ms.openlocfilehash: f5d0dd7a99087b21a5f827e4dce0f6342ae7b25a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501774"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="7479f-102">ICorDebugModule::GetMetaDataInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="7479f-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="7479f-103">Modülün meta verilerini incelemek için kullanılabilecek bir meta veri arabirimi nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="7479f-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7479f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7479f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7479f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7479f-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="7479f-106">'ndaki Meta veri arabirimini belirten başvuru Kımlığı.</span><span class="sxs-lookup"><span data-stu-id="7479f-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="7479f-107">dışı `T:IUnknown` [Meta veri arabirimlerinden](../metadata/metadata-interfaces.md)biri olan bir nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7479f-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7479f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7479f-108">Remarks</span></span>  
 <span data-ttu-id="7479f-109">Hata ayıklayıcı, `GetMetaDataInterface` Bu modülü düzenlemek için yapması gereken bir modül için özgün meta verilerin bir kopyasını oluşturmak üzere yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7479f-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="7479f-110">Hata ayıklayıcı `GetMetaDataInterface` Modül için bir [ımetadatayayma](../metadata/imetadataemit-interface.md) arabirimi nesnesi almak için öğesini çağırır ve modülün meta verilerinin bir kopyasını belleğe kaydetmek Için [ımetadatayayma:: SaveToMemory](../metadata/imetadataemit-savetomemory-method.md) öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="7479f-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7479f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7479f-111">Requirements</span></span>  
 <span data-ttu-id="7479f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7479f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7479f-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7479f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7479f-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7479f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7479f-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7479f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7479f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7479f-116">See also</span></span>

- [<span data-ttu-id="7479f-117">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="7479f-117">Metadata</span></span>](../metadata/index.md)
