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
ms.openlocfilehash: fd7f149e806727d849cdceb3ffbc5dc7392fcf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177407"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="5036f-102">IMetaDataEmit2::SetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5036f-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="5036f-103">Belirtilen belirteç tarafından başvurulan genel parametre tanımı için özellik değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5036f-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5036f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5036f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5036f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5036f-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="5036f-106">[içinde] Değerleri ayarlamak için genel parametre tanımı için belirteç.</span><span class="sxs-lookup"><span data-stu-id="5036f-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="5036f-107">[içinde] Genel parametrenin türünü açıklayan [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) numaralandırmadeğeri.</span><span class="sxs-lookup"><span data-stu-id="5036f-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="5036f-108">[içinde] Isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5036f-108">[in] Optional.</span></span> <span data-ttu-id="5036f-109">Değerleri ayarlamak için parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="5036f-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="5036f-110">[içinde] Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5036f-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="5036f-111">[içinde] Isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5036f-111">[in] Optional.</span></span> <span data-ttu-id="5036f-112">Sıfır sonlandırılmış tür kısıtlamaları dizisi.</span><span class="sxs-lookup"><span data-stu-id="5036f-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="5036f-113">Dizi üyeleri bir `mdTypeDef` `mdTypeRef`, `mdTypeSpec` veya meta veri belirteci olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5036f-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5036f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5036f-114">Requirements</span></span>  
 <span data-ttu-id="5036f-115">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5036f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5036f-116">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5036f-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5036f-117">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5036f-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5036f-118">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5036f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5036f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5036f-119">See also</span></span>

- [<span data-ttu-id="5036f-120">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5036f-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="5036f-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5036f-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
