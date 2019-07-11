---
title: IMetaDataImport::EnumUnresolvedMethods Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74d0c2e9777a7bd3d49622fb326ecb6b58fbec07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782541"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="55cc6-102">IMetaDataImport::EnumUnresolvedMethods Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55cc6-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="55cc6-103">Geçerli meta veri kapsamda çözümlenmemiş yöntemleri temsil eden MemberDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="55cc6-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55cc6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55cc6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55cc6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55cc6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="55cc6-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="55cc6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="55cc6-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55cc6-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="55cc6-108">[out] Dizi MemberDef simgeleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="55cc6-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="55cc6-109">[in] En büyük boyutunu `rMethods` dizisi.</span><span class="sxs-lookup"><span data-stu-id="55cc6-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="55cc6-110">[out] Döndürülen MemberDef belirteçleri sayısı `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="55cc6-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55cc6-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="55cc6-111">Return Value</span></span>  
  
|<span data-ttu-id="55cc6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55cc6-112">HRESULT</span></span>|<span data-ttu-id="55cc6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55cc6-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="55cc6-114">`EnumUnresolvedMethods` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="55cc6-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="55cc6-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="55cc6-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="55cc6-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="55cc6-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55cc6-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55cc6-117">Remarks</span></span>  
 <span data-ttu-id="55cc6-118">Çözümlenmemiş bir yöntem bildirilmiş, ancak uygulanmamıştır biridir.</span><span class="sxs-lookup"><span data-stu-id="55cc6-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="55cc6-119">Yöntem işaretlenmişse, yöntem numaralandırmada `miForwardRef` ve her iki `mdPinvokeImpl` veya `miRuntime` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="55cc6-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="55cc6-120">Diğer bir deyişle, bir çözümlenmemiş işaretlenmiş bir sınıf yöntemi yöntemidir `miForwardRef` ancak hangi değil (PInvoke ulaşıldı) yönetilmeyen koda uygulanan ve çalışma zamanının kendisi tarafından dahili olarak uygulanan</span><span class="sxs-lookup"><span data-stu-id="55cc6-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="55cc6-121">Numaralandırma modül kapsamında (Genel) veya arabirimler veya soyut sınıflar içinde tanımlanan tüm yöntemleri dışlar.</span><span class="sxs-lookup"><span data-stu-id="55cc6-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55cc6-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55cc6-122">Requirements</span></span>  
 <span data-ttu-id="55cc6-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55cc6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55cc6-124">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="55cc6-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="55cc6-125">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="55cc6-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="55cc6-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55cc6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55cc6-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55cc6-127">See also</span></span>

- [<span data-ttu-id="55cc6-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55cc6-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="55cc6-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55cc6-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
