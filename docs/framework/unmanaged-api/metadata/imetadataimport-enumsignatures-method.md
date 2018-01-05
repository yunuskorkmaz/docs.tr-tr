---
title: "IMetaDataImport::EnumSignatures Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumSignatures
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88d47e2512103947f007c81450157a0b3e334a33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="32e3b-102">IMetaDataImport::EnumSignatures Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32e3b-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="32e3b-103">Geçerli kapsamdaki tek başına imzaları temsil eden imza belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="32e3b-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32e3b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32e3b-104">Syntax</span></span>  
  
```  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32e3b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32e3b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="32e3b-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="32e3b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="32e3b-107">Bu, bu yöntem ilk çağrısı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="32e3b-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="32e3b-108">[out] İmza belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="32e3b-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="32e3b-109">[in] En büyük boyutunu `rSignatures` dizi.</span><span class="sxs-lookup"><span data-stu-id="32e3b-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="32e3b-110">[out] Döndürülen imza belirteçleri sayısı `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="32e3b-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32e3b-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="32e3b-111">Return Value</span></span>  
  
|<span data-ttu-id="32e3b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32e3b-112">HRESULT</span></span>|<span data-ttu-id="32e3b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32e3b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="32e3b-114">`EnumSignatures`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="32e3b-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="32e3b-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="32e3b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="32e3b-116">Bu durumda, `pcSignatures` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="32e3b-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32e3b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32e3b-117">Remarks</span></span>  
 <span data-ttu-id="32e3b-118">İmza belirteçleri tarafından oluşturulan [Imetadataemit::gettokenfromsig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32e3b-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32e3b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32e3b-119">Requirements</span></span>  
 <span data-ttu-id="32e3b-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32e3b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32e3b-121">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="32e3b-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32e3b-122">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="32e3b-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32e3b-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32e3b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32e3b-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32e3b-124">See Also</span></span>  
 [<span data-ttu-id="32e3b-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32e3b-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="32e3b-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32e3b-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
