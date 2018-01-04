---
title: "IMetaDataImport::EnumUnresolvedMethods Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumUnresolvedMethods
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4e77453fc11b77b602d4a89f0d90540c06b0a08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="45e68-102">IMetaDataImport::EnumUnresolvedMethods Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45e68-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="45e68-103">Geçerli meta veri kapsamında çözümlenmemiş yöntemleri temsil eden MemberDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="45e68-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e68-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45e68-104">Syntax</span></span>  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45e68-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45e68-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="45e68-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="45e68-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="45e68-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="45e68-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="45e68-108">[out] MemberDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="45e68-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="45e68-109">[in] En büyük boyutunu `rMethods` dizi.</span><span class="sxs-lookup"><span data-stu-id="45e68-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="45e68-110">[out] Döndürülen MemberDef belirteçleri sayısı `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="45e68-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45e68-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="45e68-111">Return Value</span></span>  
  
|<span data-ttu-id="45e68-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45e68-112">HRESULT</span></span>|<span data-ttu-id="45e68-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45e68-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="45e68-114">`EnumUnresolvedMethods`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="45e68-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="45e68-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="45e68-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="45e68-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="45e68-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45e68-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45e68-117">Remarks</span></span>  
 <span data-ttu-id="45e68-118">Çözümlenmemiş yöntemi bildirildi, ancak uygulanmadı biridir.</span><span class="sxs-lookup"><span data-stu-id="45e68-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="45e68-119">Yöntem işaretlenmişse bir yöntemi numaralandırmada dahil `miForwardRef` ve her iki `mdPinvokeImpl` veya `miRuntime` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="45e68-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="45e68-120">Diğer bir deyişle, bir çözümlenmemiş yöntemi olarak işaretlenmiş bir sınıf yöntemdir `miForwardRef` ancak hangi değil (PInvoke ulaşıldı) yönetilmeyen kod uygulanan ve çalışma tarafından dahili olarak uygulanmadı</span><span class="sxs-lookup"><span data-stu-id="45e68-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="45e68-121">Numaralandırma modül kapsamındaki (globals) ya da arabirimleri veya soyut sınıflar tanımlanmış tüm yöntemleri dışlar.</span><span class="sxs-lookup"><span data-stu-id="45e68-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45e68-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45e68-122">Requirements</span></span>  
 <span data-ttu-id="45e68-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45e68-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45e68-124">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="45e68-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="45e68-125">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="45e68-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="45e68-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45e68-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e68-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45e68-127">See Also</span></span>  
 [<span data-ttu-id="45e68-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45e68-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="45e68-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45e68-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
