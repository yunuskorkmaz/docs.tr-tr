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
ms.openlocfilehash: 3c7709180e5b7811379c25977f8a8d23b91adb3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="7dab4-102">IMetaDataImport::EnumUnresolvedMethods Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dab4-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="7dab4-103">Geçerli meta veri kapsamında çözümlenmemiş yöntemleri temsil eden MemberDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7dab4-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dab4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7dab4-104">Syntax</span></span>  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7dab4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7dab4-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7dab4-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7dab4-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="7dab4-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7dab4-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="7dab4-108">[out] MemberDef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="7dab4-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7dab4-109">[in] En büyük boyutunu `rMethods` dizi.</span><span class="sxs-lookup"><span data-stu-id="7dab4-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="7dab4-110">[out] Döndürülen MemberDef belirteçleri sayısı `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="7dab4-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7dab4-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7dab4-111">Return Value</span></span>  
  
|<span data-ttu-id="7dab4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7dab4-112">HRESULT</span></span>|<span data-ttu-id="7dab4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dab4-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7dab4-114">`EnumUnresolvedMethods`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7dab4-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7dab4-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="7dab4-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="7dab4-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="7dab4-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dab4-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7dab4-117">Remarks</span></span>  
 <span data-ttu-id="7dab4-118">Çözümlenmemiş yöntemi bildirildi, ancak uygulanmadı biridir.</span><span class="sxs-lookup"><span data-stu-id="7dab4-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="7dab4-119">Yöntem işaretlenmişse bir yöntemi numaralandırmada dahil `miForwardRef` ve her iki `mdPinvokeImpl` veya `miRuntime` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7dab4-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="7dab4-120">Diğer bir deyişle, bir çözümlenmemiş yöntemi olarak işaretlenmiş bir sınıf yöntemdir `miForwardRef` ancak hangi değil (PInvoke ulaşıldı) yönetilmeyen kod uygulanan ve çalışma tarafından dahili olarak uygulanmadı</span><span class="sxs-lookup"><span data-stu-id="7dab4-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="7dab4-121">Numaralandırma modül kapsamındaki (globals) ya da arabirimleri veya soyut sınıflar tanımlanmış tüm yöntemleri dışlar.</span><span class="sxs-lookup"><span data-stu-id="7dab4-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dab4-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7dab4-122">Requirements</span></span>  
 <span data-ttu-id="7dab4-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dab4-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dab4-124">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7dab4-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7dab4-125">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7dab4-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7dab4-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dab4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dab4-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7dab4-127">See Also</span></span>  
 [<span data-ttu-id="7dab4-128">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="7dab4-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="7dab4-129">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="7dab4-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
