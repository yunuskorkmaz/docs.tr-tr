---
title: IMetaDataEmit::SetMethodProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ef6771ec3f458c20701cc330a5730367b3c5b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445932"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="7ec48-102">IMetaDataEmit::SetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ec48-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="7ec48-103">Belirtilen göreli sanal adresinde, önceki bir çağrı tarafından tanımlanan bir yöntemin depolanan özelliği, güncelleştirir veya ayarlar [Imetadataemit::definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="7ec48-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ec48-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ec48-104">Syntax</span></span>  
  
```  
HRESULT SetMethodProps (   
    [in]  mdMethodDef md,   
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,   
    [in]  DWORD       dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ec48-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ec48-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="7ec48-106">[in] Değiştirilecek yöntemi için belirteci.</span><span class="sxs-lookup"><span data-stu-id="7ec48-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="7ec48-107">[in] Üye öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="7ec48-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="7ec48-108">[in] Kod adresi.</span><span class="sxs-lookup"><span data-stu-id="7ec48-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="7ec48-109">[in] Uygulama bayrakları yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ec48-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ec48-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ec48-110">Requirements</span></span>  
 <span data-ttu-id="7ec48-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ec48-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ec48-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7ec48-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ec48-113">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7ec48-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ec48-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ec48-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec48-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ec48-115">See Also</span></span>  
 [<span data-ttu-id="7ec48-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ec48-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="7ec48-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ec48-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
