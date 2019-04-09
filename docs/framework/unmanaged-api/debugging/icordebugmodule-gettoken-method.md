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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c28182feff8e4b7d49b7d068da1496d44fa2f917
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150364"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="52fff-102">ICorDebugModule::GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52fff-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="52fff-103">Bu modül için tablo girişi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="52fff-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52fff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52fff-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52fff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52fff-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="52fff-106">[out] Bir işaretçi `mdModule` modülün meta verilerinin başvuran belirteci.</span><span class="sxs-lookup"><span data-stu-id="52fff-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52fff-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52fff-107">Remarks</span></span>  
 <span data-ttu-id="52fff-108">Belirteç geçirilebilir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [Imetadataımport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), ve [Imetadataassemblyımport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) meta veri alma arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="52fff-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52fff-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52fff-109">Requirements</span></span>  
 <span data-ttu-id="52fff-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52fff-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52fff-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52fff-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52fff-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52fff-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="52fff-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="52fff-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="52fff-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52fff-114">See also</span></span>

- [<span data-ttu-id="52fff-115">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="52fff-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
