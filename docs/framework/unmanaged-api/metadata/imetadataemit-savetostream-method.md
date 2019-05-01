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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042997"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="17b52-102">IMetaDataEmit::SaveToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17b52-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="17b52-103">Belirtilen geçerli kapsamdaki tüm meta verileri kaydeder `IStream`.</span><span class="sxs-lookup"><span data-stu-id="17b52-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17b52-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17b52-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17b52-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17b52-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="17b52-106">[in] Kaydetmek için yazılabilir akış.</span><span class="sxs-lookup"><span data-stu-id="17b52-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="17b52-107">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="17b52-107">[in] Reserved.</span></span> <span data-ttu-id="17b52-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17b52-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17b52-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17b52-109">Requirements</span></span>  
 <span data-ttu-id="17b52-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17b52-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17b52-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="17b52-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17b52-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="17b52-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17b52-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17b52-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b52-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17b52-114">See also</span></span>

- [<span data-ttu-id="17b52-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17b52-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="17b52-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17b52-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
