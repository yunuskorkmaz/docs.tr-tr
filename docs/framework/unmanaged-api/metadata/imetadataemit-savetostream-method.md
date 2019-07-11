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
ms.openlocfilehash: 96b3b270fb12aa451d9026435dd3d2c4c196b09c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782022"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="24f4b-102">IMetaDataEmit::SaveToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24f4b-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="24f4b-103">Belirtilen geçerli kapsamdaki tüm meta verileri kaydeder `IStream`.</span><span class="sxs-lookup"><span data-stu-id="24f4b-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24f4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24f4b-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24f4b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24f4b-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="24f4b-106">[in] Kaydetmek için yazılabilir akış.</span><span class="sxs-lookup"><span data-stu-id="24f4b-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="24f4b-107">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="24f4b-107">[in] Reserved.</span></span> <span data-ttu-id="24f4b-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="24f4b-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24f4b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24f4b-109">Requirements</span></span>  
 <span data-ttu-id="24f4b-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24f4b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24f4b-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="24f4b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24f4b-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="24f4b-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24f4b-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24f4b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f4b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24f4b-114">See also</span></span>

- [<span data-ttu-id="24f4b-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24f4b-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="24f4b-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24f4b-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
