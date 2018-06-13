---
title: IMetaDataEmit2::SetGenericParamProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d74ee7512f640ab906f1119f61e4998b5e882eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445693"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="0e10d-102">IMetaDataEmit2::SetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e10d-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="0e10d-103">Belirtilen belirteç tarafından başvurulan genel parametresini tanımı için özellik değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0e10d-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e10d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e10d-104">Syntax</span></span>  
  
```  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e10d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e10d-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="0e10d-106">[in] Hangi değerlerini ayarlamak genel parametresini tanımı için belirteci.</span><span class="sxs-lookup"><span data-stu-id="0e10d-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="0e10d-107">[in] Değerini [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) türünü genel parametresi için açıklayan numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="0e10d-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="0e10d-108">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0e10d-108">[in] Optional.</span></span> <span data-ttu-id="0e10d-109">Değerleri ayarlanacak parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="0e10d-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="0e10d-110">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="0e10d-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="0e10d-111">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0e10d-111">[in] Optional.</span></span> <span data-ttu-id="0e10d-112">Tür kısıtlamaları sıfır sonlandırılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="0e10d-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="0e10d-113">Dizi üyeleri olmalıdır bir `mdTypeDef`, `mdTypeRef`, veya `mdTypeSpec` meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="0e10d-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e10d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e10d-114">Requirements</span></span>  
 <span data-ttu-id="0e10d-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e10d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e10d-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e10d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e10d-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0e10d-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e10d-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e10d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e10d-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e10d-119">See Also</span></span>  
 [<span data-ttu-id="0e10d-120">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e10d-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="0e10d-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e10d-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
