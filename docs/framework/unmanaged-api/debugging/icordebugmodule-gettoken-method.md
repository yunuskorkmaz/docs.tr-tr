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
ms.openlocfilehash: 1cf4d82200709971201da60d06d0cb929641a104
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501891"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="f1a20-102">ICorDebugModule::GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1a20-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="f1a20-103">Bu modül için tablo girişi belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="f1a20-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a20-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f1a20-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1a20-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1a20-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="f1a20-106">dışı `mdModule`Modülün meta verilerine başvuran belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1a20-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1a20-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1a20-107">Remarks</span></span>  
 <span data-ttu-id="f1a20-108">Belirteç [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md)ve [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) meta veri alma arabirimlerine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f1a20-108">The token can be passed to the [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1a20-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1a20-109">Requirements</span></span>  
 <span data-ttu-id="f1a20-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1a20-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1a20-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f1a20-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1a20-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f1a20-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1a20-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1a20-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a20-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1a20-114">See also</span></span>

- [<span data-ttu-id="f1a20-115">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="f1a20-115">Metadata</span></span>](../metadata/index.md)
