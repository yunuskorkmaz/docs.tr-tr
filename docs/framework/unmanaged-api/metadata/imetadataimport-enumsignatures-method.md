---
title: IMetaDataImport::EnumSignatures Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 193abe173b259ff2679642e229fce96151e37872
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179692"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="2849b-102">IMetaDataImport::EnumSignatures Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2849b-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="2849b-103">Tek başına imzaları geçerli kapsamda temsil eden imzası belirteçlerinin numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="2849b-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2849b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2849b-104">Syntax</span></span>  
  
```  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2849b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2849b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2849b-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2849b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2849b-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2849b-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="2849b-108">[out] İmza simgeleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="2849b-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2849b-109">[in] En büyük boyutunu `rSignatures` dizisi.</span><span class="sxs-lookup"><span data-stu-id="2849b-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="2849b-110">[out] Döndürülen, imzası belirteçlerinin sayısı `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="2849b-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2849b-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2849b-111">Return Value</span></span>  
  
|<span data-ttu-id="2849b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2849b-112">HRESULT</span></span>|<span data-ttu-id="2849b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2849b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2849b-114">`EnumSignatures` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2849b-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2849b-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="2849b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="2849b-116">Bu durumda, `pcSignatures` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="2849b-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2849b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2849b-117">Remarks</span></span>  
 <span data-ttu-id="2849b-118">İmza belirteçleri oluşturan [Imetadataemit::gettokenfromsig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2849b-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2849b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2849b-119">Requirements</span></span>  
 <span data-ttu-id="2849b-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2849b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2849b-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2849b-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2849b-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2849b-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2849b-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2849b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2849b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2849b-124">See also</span></span>

- [<span data-ttu-id="2849b-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2849b-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2849b-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2849b-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
