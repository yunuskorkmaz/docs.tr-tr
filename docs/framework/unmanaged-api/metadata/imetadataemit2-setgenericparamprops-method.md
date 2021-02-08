---
description: ': IMetaDataEmit2:: SetGenericParamProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9c6946bbd301450203bc6fb2b1202352119dc792
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771658"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="0aa84-103">IMetaDataEmit2::SetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0aa84-103">IMetaDataEmit2::SetGenericParamProps Method</span></span>

<span data-ttu-id="0aa84-104">Belirtilen belirteç tarafından başvurulan genel parametre tanımının özellik değerlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0aa84-104">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa84-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0aa84-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aa84-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0aa84-106">Parameters</span></span>  

 `gp`  
 <span data-ttu-id="0aa84-107">'ndaki Değerleri ayarlanacak genel parametre tanımının belirteci.</span><span class="sxs-lookup"><span data-stu-id="0aa84-107">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="0aa84-108">'ndaki Genel parametrenin türünü açıklayan [CorGenericParamAttr](corgenericparamattr-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="0aa84-108">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="0aa84-109">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="0aa84-109">[in] Optional.</span></span> <span data-ttu-id="0aa84-110">Değerlerinin ayarlanacağı parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="0aa84-110">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="0aa84-111">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0aa84-111">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="0aa84-112">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="0aa84-112">[in] Optional.</span></span> <span data-ttu-id="0aa84-113">Tür kısıtlamaları sıfır ile sonlandırılmış dizi.</span><span class="sxs-lookup"><span data-stu-id="0aa84-113">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="0aa84-114">Dizi üyeleri bir `mdTypeDef` , `mdTypeRef` veya `mdTypeSpec` meta veri belirteci olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0aa84-114">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aa84-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0aa84-115">Requirements</span></span>  

 <span data-ttu-id="0aa84-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aa84-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aa84-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0aa84-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0aa84-118">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0aa84-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0aa84-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aa84-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa84-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0aa84-120">See also</span></span>

- [<span data-ttu-id="0aa84-121">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0aa84-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="0aa84-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0aa84-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
