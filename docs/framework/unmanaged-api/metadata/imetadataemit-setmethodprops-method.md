---
description: ': Imetadatayayma:: SetMethodProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: edecdc14abb386f8fa4cd70535f2b8c012bdc59f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772113"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="3730d-103">IMetaDataEmit::SetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3730d-103">IMetaDataEmit::SetMethodProps Method</span></span>

<span data-ttu-id="3730d-104">[Imetadatayayma::D efineMethod](imetadataemit-definemethod-method.md)için önceki bir çağrı tarafından tanımlanan bir yöntemin belirtilen göreli sanal adresinde depolanan özelliği ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="3730d-104">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3730d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3730d-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3730d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3730d-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="3730d-107">'ndaki Değiştirilecek metodun belirteci.</span><span class="sxs-lookup"><span data-stu-id="3730d-107">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="3730d-108">'ndaki Üye öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="3730d-108">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="3730d-109">'ndaki Kodun adresi.</span><span class="sxs-lookup"><span data-stu-id="3730d-109">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="3730d-110">'ndaki Yöntemi için uygulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="3730d-110">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3730d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3730d-111">Requirements</span></span>  

 <span data-ttu-id="3730d-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3730d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3730d-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3730d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3730d-114">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3730d-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3730d-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3730d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3730d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3730d-116">See also</span></span>

- [<span data-ttu-id="3730d-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3730d-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3730d-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3730d-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
