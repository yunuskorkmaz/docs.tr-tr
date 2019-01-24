---
title: IMetaDataEmit::Save Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a2be03e82d5be9bae64d7169709d16c40b66e37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511887"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="5d9bd-102">IMetaDataEmit::Save Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d9bd-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="5d9bd-103">Belirtilen adresteki bir dosyaya geçerli kapsamdaki tüm meta verileri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5d9bd-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d9bd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d9bd-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d9bd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d9bd-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="5d9bd-106">[in] Kaydedilecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="5d9bd-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="5d9bd-107">Bu değer null ise, bellek içi kopyayı son kullanılan konuma kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5d9bd-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="5d9bd-108">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5d9bd-108">[in] Reserved.</span></span> <span data-ttu-id="5d9bd-109">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d9bd-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d9bd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d9bd-110">Requirements</span></span>  
 <span data-ttu-id="5d9bd-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d9bd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d9bd-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5d9bd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d9bd-113">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="5d9bd-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d9bd-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d9bd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d9bd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d9bd-115">See also</span></span>
- [<span data-ttu-id="5d9bd-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d9bd-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5d9bd-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d9bd-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
