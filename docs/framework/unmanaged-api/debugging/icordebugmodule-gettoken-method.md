---
title: ICorDebugModule::GetToken Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
ms.openlocfilehash: a6aff37a480460bfed7064d59b4c5276daf3207c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212509"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="357bb-102">ICorDebugModule::GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="357bb-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="357bb-103">Bu modül için tablo girişi belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="357bb-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="357bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="357bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="357bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="357bb-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="357bb-106">dışı `mdModule`Modülün meta verilerine başvuran belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="357bb-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="357bb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="357bb-107">Remarks</span></span>  
 <span data-ttu-id="357bb-108">Belirteç [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)ve [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) meta veri alma arabirimlerine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="357bb-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="357bb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="357bb-109">Requirements</span></span>  
 <span data-ttu-id="357bb-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="357bb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="357bb-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="357bb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="357bb-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="357bb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="357bb-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="357bb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="357bb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="357bb-114">See also</span></span>

- [<span data-ttu-id="357bb-115">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="357bb-115">Metadata</span></span>](../metadata/index.md)
