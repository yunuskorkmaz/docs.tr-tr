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
ms.openlocfilehash: 4c998d70fa5dd41ab4c1656f129bb77767a8ab97
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574631"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="2c265-102">IMetaDataEmit2::SetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c265-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="2c265-103">Belirtilen belirteç tarafından başvurulan genel parametre tanımı için özellik değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2c265-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c265-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c265-104">Syntax</span></span>  
  
```  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c265-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c265-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="2c265-106">[in] Genel parametre tanımı için olan değerleri ayarlamak belirteç.</span><span class="sxs-lookup"><span data-stu-id="2c265-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="2c265-107">[in] Değerini [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) türünü genel parametresi için açıklayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="2c265-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="2c265-108">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2c265-108">[in] Optional.</span></span> <span data-ttu-id="2c265-109">Değerleri ayarlamak istediğiniz parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="2c265-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="2c265-110">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="2c265-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="2c265-111">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2c265-111">[in] Optional.</span></span> <span data-ttu-id="2c265-112">Tür kısıtlamaları Sıfırla sonlandırılmış dizisi.</span><span class="sxs-lookup"><span data-stu-id="2c265-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="2c265-113">Dizi üyeleri olmalıdır bir `mdTypeDef`, `mdTypeRef`, veya `mdTypeSpec` meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="2c265-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c265-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c265-114">Requirements</span></span>  
 <span data-ttu-id="2c265-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c265-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c265-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2c265-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c265-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="2c265-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c265-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c265-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c265-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c265-119">See also</span></span>
- [<span data-ttu-id="2c265-120">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c265-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="2c265-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c265-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
