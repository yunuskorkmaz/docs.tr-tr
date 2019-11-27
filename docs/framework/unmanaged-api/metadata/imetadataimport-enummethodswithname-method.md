---
title: IMetaDataImport::EnumMethodsWithName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: b0817288040550b5f4c3c4ec063f6a7fdb004137
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450064"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="5d3b2-102">IMetaDataImport::EnumMethodsWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d3b2-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="5d3b2-103">Belirtilen ada sahip olan ve belirtilen TypeDef belirtecinin başvurduğu tür tarafından tanımlanan yöntemleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d3b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d3b2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d3b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d3b2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5d3b2-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5d3b2-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="5d3b2-108">'ndaki Yöntemlerini Numaralandırılacak türü temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="5d3b2-109">'ndaki Sabit listesinin kapsamını sınırlayan ad.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="5d3b2-110">dışı MethodDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5d3b2-111">'ndaki `rMethods` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5d3b2-112">dışı `rMethods`döndürülen MethodDef belirteçleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d3b2-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d3b2-113">Remarks</span></span>  
 <span data-ttu-id="5d3b2-114">Bu yöntem, alanları ve yöntemleri numaralandırır, ancak özellikleri veya olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="5d3b2-115">[IMetaDataImport:: EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)'ın aksine `EnumMethodsWithName`, belirtilen ada sahip olmayan tüm metot belirteçlerini atar.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d3b2-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5d3b2-116">Return Value</span></span>  
  
|<span data-ttu-id="5d3b2-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d3b2-117">HRESULT</span></span>|<span data-ttu-id="5d3b2-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d3b2-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5d3b2-119">`EnumMethodsWithName` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5d3b2-120">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="5d3b2-121">Bu durumda `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d3b2-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d3b2-122">Requirements</span></span>  
 <span data-ttu-id="5d3b2-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d3b2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d3b2-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5d3b2-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d3b2-125">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5d3b2-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5d3b2-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d3b2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d3b2-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d3b2-127">See also</span></span>

- [<span data-ttu-id="5d3b2-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d3b2-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5d3b2-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d3b2-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
