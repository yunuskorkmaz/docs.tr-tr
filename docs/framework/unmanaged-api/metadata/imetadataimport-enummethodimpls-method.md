---
title: IMetaDataImport::EnumMethodImpls Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
ms.openlocfilehash: 193e8788d5a1b28f43f2fb0d4d935a18542dd923
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427496"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="64545-102">IMetaDataImport::EnumMethodImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64545-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="64545-103">Belirtilen türdeki yöntemleri temsil eden MethodBody ve MethodDeclaration belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="64545-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64545-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64545-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64545-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64545-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="64545-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64545-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="64545-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="64545-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="64545-108">'ndaki Yöntem uygulamaları Numaralandırılacak tür için bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="64545-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="64545-109">dışı MethodBody belirteçlerini depolayacak dizi.</span><span class="sxs-lookup"><span data-stu-id="64545-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="64545-110">dışı MethodDeclaration belirteçlerini depolayacak dizi.</span><span class="sxs-lookup"><span data-stu-id="64545-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="64545-111">'ndaki `rMethodBody` ve `rMethodDecl` dizilerinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="64545-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="64545-112">'ndaki `rMethodBody` ve `rMethodDecl`döndürülen gerçek Yöntem sayısı.</span><span class="sxs-lookup"><span data-stu-id="64545-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64545-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="64545-113">Return Value</span></span>  
  
|<span data-ttu-id="64545-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64545-114">HRESULT</span></span>|<span data-ttu-id="64545-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64545-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="64545-116">`EnumMethodImpls` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="64545-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="64545-117">Numaralandırılacak hiçbir yöntem belirteci yok.</span><span class="sxs-lookup"><span data-stu-id="64545-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="64545-118">Bu durumda `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="64545-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64545-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64545-119">Requirements</span></span>  
 <span data-ttu-id="64545-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64545-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64545-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="64545-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64545-122">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="64545-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64545-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64545-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64545-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64545-124">See also</span></span>

- [<span data-ttu-id="64545-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64545-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="64545-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64545-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
