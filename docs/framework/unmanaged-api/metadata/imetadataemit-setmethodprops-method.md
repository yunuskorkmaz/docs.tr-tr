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
ms.openlocfilehash: 9662a14b4ea97aed16968083489324d46c38dda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177519"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="416ae-102">IMetaDataEmit::SetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="416ae-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="416ae-103">[IMetaDataEmit::DefineMethod'a](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)yapılan bir önceki çağrıyla tanımlanan bir yöntemin belirtilen göreli sanal adreste depolanan özelliği nispi olarak ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="416ae-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="416ae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="416ae-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="416ae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="416ae-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="416ae-106">[içinde] Yöntemin değiştirilmesi için belirteç.</span><span class="sxs-lookup"><span data-stu-id="416ae-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="416ae-107">[içinde] Üye öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="416ae-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="416ae-108">[içinde] Kodun adresi.</span><span class="sxs-lookup"><span data-stu-id="416ae-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="416ae-109">[içinde] Yöntem için uygulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="416ae-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="416ae-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="416ae-110">Requirements</span></span>  
 <span data-ttu-id="416ae-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="416ae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="416ae-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="416ae-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="416ae-113">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="416ae-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="416ae-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="416ae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="416ae-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="416ae-115">See also</span></span>

- [<span data-ttu-id="416ae-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="416ae-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="416ae-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="416ae-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
