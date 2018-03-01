---
title: "IMetaDataImport::EnumMemberRefs Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ea308db566e37d10cccdc2777b5a2374408a8ea6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="09158-102">IMetaDataImport::EnumMemberRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09158-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="09158-103">Belirtilen türün üyeleri temsil eden MemberRef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="09158-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09158-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09158-104">Syntax</span></span>  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09158-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09158-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="09158-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="09158-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="09158-107">[in] Numaralandırılacak üyeleri olan türü için TypeDef, TypeRef, MethodDef veya ModuleRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="09158-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="09158-108">[out] MemberRef belirteçleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="09158-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="09158-109">[in] En büyük boyutunu `rMemberRefs` dizi.</span><span class="sxs-lookup"><span data-stu-id="09158-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="09158-110">[out] Döndürülen MemberRef belirteçleri gerçek sayısını `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="09158-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09158-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="09158-111">Return Value</span></span>  
  
|<span data-ttu-id="09158-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09158-112">HRESULT</span></span>|<span data-ttu-id="09158-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09158-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="09158-114">`EnumMemberRefs`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="09158-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="09158-115">Numaralandırılacak hiçbir MemberRef belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="09158-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="09158-116">Bu durumda, `pcTokens` için sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="09158-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09158-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09158-117">Requirements</span></span>  
 <span data-ttu-id="09158-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09158-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09158-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="09158-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09158-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="09158-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09158-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09158-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09158-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="09158-122">See Also</span></span>  
 [<span data-ttu-id="09158-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09158-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="09158-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09158-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
