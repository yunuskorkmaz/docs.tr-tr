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
ms.openlocfilehash: 57f6de1f7edf7c75a3f96cb2bf9fb98fdbd6f65e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007864"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="06d29-102">IMetaDataEmit::SetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06d29-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="06d29-103">[Imetadatayayma::D efineMethod](imetadataemit-definemethod-method.md)için önceki bir çağrı tarafından tanımlanan bir yöntemin belirtilen göreli sanal adresinde depolanan özelliği ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="06d29-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06d29-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="06d29-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06d29-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06d29-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="06d29-106">'ndaki Değiştirilecek metodun belirteci.</span><span class="sxs-lookup"><span data-stu-id="06d29-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="06d29-107">'ndaki Üye öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="06d29-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="06d29-108">'ndaki Kodun adresi.</span><span class="sxs-lookup"><span data-stu-id="06d29-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="06d29-109">'ndaki Yöntemi için uygulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="06d29-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06d29-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06d29-110">Requirements</span></span>  
 <span data-ttu-id="06d29-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06d29-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06d29-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="06d29-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="06d29-113">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="06d29-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06d29-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06d29-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d29-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06d29-115">See also</span></span>

- [<span data-ttu-id="06d29-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06d29-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="06d29-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06d29-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
