---
title: ICorDebugModule::GetToken Metodu
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
ms.openlocfilehash: 3d1e0f0d57440f0074a7ca179955a7a13e41f5d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415860"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="bc029-102">ICorDebugModule::GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="bc029-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="bc029-103">Bu modül için tablo girişi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="bc029-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc029-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc029-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc029-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc029-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="bc029-106">[out] Bir işaretçi `mdModule` modülün meta verileri başvuran belirteci.</span><span class="sxs-lookup"><span data-stu-id="bc029-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc029-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc029-107">Remarks</span></span>  
 <span data-ttu-id="bc029-108">Belirteç için geçirilebilir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [Imetadataımport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), ve [Imetadataassemblyımport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) meta veri alma arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="bc029-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc029-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc029-109">Requirements</span></span>  
 <span data-ttu-id="bc029-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc029-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc029-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc029-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc029-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc029-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc029-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc029-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc029-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc029-114">See Also</span></span>  
 [<span data-ttu-id="bc029-115">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="bc029-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
