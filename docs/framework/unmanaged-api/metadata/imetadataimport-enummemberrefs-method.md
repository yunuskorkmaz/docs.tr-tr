---
title: IMetaDataImport::EnumMemberRefs Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 444c892026f9b6de12255ebdcda829db82c9bfdb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780451"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="850c3-102">IMetaDataImport::EnumMemberRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="850c3-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="850c3-103">Belirtilen türün üyelerini temsil eden MemberRef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="850c3-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="850c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="850c3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="850c3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="850c3-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="850c3-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="850c3-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="850c3-107">[in] Numaralandırılacak üyeleri olan türü için bir TypeDef, TypeRef, MethodDef veya ModuleRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="850c3-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="850c3-108">[out] Dizi MemberRef belirteçlerini depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="850c3-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="850c3-109">[in] En büyük boyutunu `rMemberRefs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="850c3-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="850c3-110">[out] Döndürülen MemberRef belirteçleri gerçek sayısını `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="850c3-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="850c3-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="850c3-111">Return Value</span></span>  
  
|<span data-ttu-id="850c3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="850c3-112">HRESULT</span></span>|<span data-ttu-id="850c3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="850c3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="850c3-114">`EnumMemberRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="850c3-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="850c3-115">Numaralandırılacak hiçbir MemberRef belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="850c3-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="850c3-116">Bu durumda, `pcTokens` için sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="850c3-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="850c3-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="850c3-117">Requirements</span></span>  
 <span data-ttu-id="850c3-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="850c3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="850c3-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="850c3-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="850c3-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="850c3-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="850c3-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="850c3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="850c3-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="850c3-122">See also</span></span>

- [<span data-ttu-id="850c3-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="850c3-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="850c3-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="850c3-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
