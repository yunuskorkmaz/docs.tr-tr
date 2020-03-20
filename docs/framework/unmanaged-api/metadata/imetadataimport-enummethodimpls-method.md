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
ms.openlocfilehash: e766cec8fd84713e12c43cd1095650ed5b757bcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175479"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="e713d-102">IMetaDataImport::EnumMethodImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e713d-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="e713d-103">Belirtilen tipteki yöntemleri temsil eden MethodBody ve MethodDeclaration belirteçlerini okurum.</span><span class="sxs-lookup"><span data-stu-id="e713d-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e713d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e713d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e713d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e713d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e713d-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e713d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e713d-107">Bu yöntemin ilk araması için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e713d-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="e713d-108">[içinde] Yöntem uygulamaları numaralandırmak için türü için bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="e713d-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="e713d-109">[çıkış] MethodBody belirteçlerini depolamak için dizi.</span><span class="sxs-lookup"><span data-stu-id="e713d-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="e713d-110">[çıkış] MethodDeclaration belirteçlerini depolayabilmek için dizi.</span><span class="sxs-lookup"><span data-stu-id="e713d-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e713d-111">[içinde] Ve `rMethodBody` `rMethodDecl` dizilerin maksimum boyutu.</span><span class="sxs-lookup"><span data-stu-id="e713d-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e713d-112">[içinde] Döndürülen yöntemlerin gerçek `rMethodBody` `rMethodDecl`sayısı ve .</span><span class="sxs-lookup"><span data-stu-id="e713d-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e713d-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e713d-113">Return Value</span></span>  
  
|<span data-ttu-id="e713d-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e713d-114">HRESULT</span></span>|<span data-ttu-id="e713d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e713d-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e713d-116">`EnumMethodImpls`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e713d-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e713d-117">Sayısala maksat için herhangi bir yöntem belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e713d-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="e713d-118">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="e713d-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e713d-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e713d-119">Requirements</span></span>  
 <span data-ttu-id="e713d-120">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e713d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e713d-121">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e713d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e713d-122">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="e713d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e713d-123">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e713d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e713d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e713d-124">See also</span></span>

- [<span data-ttu-id="e713d-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e713d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e713d-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e713d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
