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
ms.openlocfilehash: 8f6b5582b96dfc83eed482def2c4c4abfeb33a4c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207792"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="bb6a4-102">IMetaDataEmit::SaveToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb6a4-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="bb6a4-103">Belirtilen geçerli kapsamdaki tüm meta verileri kaydeder `IStream`.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb6a4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb6a4-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb6a4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb6a4-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="bb6a4-106">[in] Kaydetmek için yazılabilir akış.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="bb6a4-107">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-107">[in] Reserved.</span></span> <span data-ttu-id="bb6a4-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb6a4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb6a4-109">Requirements</span></span>  
 <span data-ttu-id="bb6a4-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb6a4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb6a4-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bb6a4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb6a4-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="bb6a4-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb6a4-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb6a4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6a4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb6a4-114">See also</span></span>

- [<span data-ttu-id="bb6a4-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb6a4-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bb6a4-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb6a4-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
