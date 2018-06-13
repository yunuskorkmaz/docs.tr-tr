---
title: IMetaDataEmit::SaveToStream Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 656f5ee20e50ea9ac5c03711adfd0b8264fbcca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444964"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="4b2d3-102">IMetaDataEmit::SaveToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b2d3-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="4b2d3-103">Belirtilen geçerli kapsamdaki tüm meta veriler kaydeder `IStream`.</span><span class="sxs-lookup"><span data-stu-id="4b2d3-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b2d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b2d3-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b2d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b2d3-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="4b2d3-106">[in] Kaydetmek için yazılabilir akış.</span><span class="sxs-lookup"><span data-stu-id="4b2d3-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="4b2d3-107">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="4b2d3-107">[in] Reserved.</span></span> <span data-ttu-id="4b2d3-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b2d3-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b2d3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b2d3-109">Requirements</span></span>  
 <span data-ttu-id="4b2d3-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b2d3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b2d3-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4b2d3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b2d3-112">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4b2d3-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b2d3-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b2d3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b2d3-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b2d3-114">See Also</span></span>  
 [<span data-ttu-id="4b2d3-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b2d3-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4b2d3-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b2d3-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
