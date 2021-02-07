---
description: ': ICorDebugModule:: GetMetaDataInterface Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 39af2560b4c10f6dc490bfba5425e2339a7c1823
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691651"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="93bdb-103">ICorDebugModule::GetMetaDataInterface Metodu</span><span class="sxs-lookup"><span data-stu-id="93bdb-103">ICorDebugModule::GetMetaDataInterface Method</span></span>

<span data-ttu-id="93bdb-104">Modülün meta verilerini incelemek için kullanılabilecek bir meta veri arabirimi nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="93bdb-104">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93bdb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93bdb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93bdb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93bdb-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="93bdb-107">'ndaki Meta veri arabirimini belirten başvuru Kımlığı.</span><span class="sxs-lookup"><span data-stu-id="93bdb-107">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="93bdb-108">dışı `T:IUnknown` [Meta veri arabirimlerinden](../metadata/metadata-interfaces.md)biri olan bir nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="93bdb-108">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93bdb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93bdb-109">Remarks</span></span>  

 <span data-ttu-id="93bdb-110">Hata ayıklayıcı, `GetMetaDataInterface` Bu modülü düzenlemek için yapması gereken bir modül için özgün meta verilerin bir kopyasını oluşturmak üzere yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="93bdb-110">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="93bdb-111">Hata ayıklayıcı `GetMetaDataInterface` Modül için bir [ımetadatayayma](../metadata/imetadataemit-interface.md) arabirimi nesnesi almak için öğesini çağırır ve modülün meta verilerinin bir kopyasını belleğe kaydetmek Için [ımetadatayayma:: SaveToMemory](../metadata/imetadataemit-savetomemory-method.md) öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="93bdb-111">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93bdb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93bdb-112">Requirements</span></span>  

 <span data-ttu-id="93bdb-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93bdb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93bdb-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="93bdb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93bdb-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="93bdb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93bdb-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93bdb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93bdb-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93bdb-117">See also</span></span>

- [<span data-ttu-id="93bdb-118">Meta veri</span><span class="sxs-lookup"><span data-stu-id="93bdb-118">Metadata</span></span>](../metadata/index.md)
