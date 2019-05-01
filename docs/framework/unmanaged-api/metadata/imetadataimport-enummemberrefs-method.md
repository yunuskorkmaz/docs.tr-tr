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
ms.openlocfilehash: a08577f15a6fab0e630d40032a23c273ee935faa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992335"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="0b6ee-102">IMetaDataImport::EnumMemberRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b6ee-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="0b6ee-103">Belirtilen türün üyelerini temsil eden MemberRef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b6ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b6ee-104">Syntax</span></span>  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b6ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b6ee-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0b6ee-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="0b6ee-107">[in] Numaralandırılacak üyeleri olan türü için bir TypeDef, TypeRef, MethodDef veya ModuleRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="0b6ee-108">[out] Dizi MemberRef belirteçlerini depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0b6ee-109">[in] En büyük boyutunu `rMemberRefs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0b6ee-110">[out] Döndürülen MemberRef belirteçleri gerçek sayısını `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b6ee-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0b6ee-111">Return Value</span></span>  
  
|<span data-ttu-id="0b6ee-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b6ee-112">HRESULT</span></span>|<span data-ttu-id="0b6ee-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b6ee-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0b6ee-114">`EnumMemberRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0b6ee-115">Numaralandırılacak hiçbir MemberRef belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="0b6ee-116">Bu durumda, `pcTokens` için sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b6ee-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b6ee-117">Requirements</span></span>  
 <span data-ttu-id="0b6ee-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b6ee-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b6ee-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0b6ee-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b6ee-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0b6ee-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b6ee-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b6ee-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b6ee-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b6ee-122">See also</span></span>

- [<span data-ttu-id="0b6ee-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b6ee-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0b6ee-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b6ee-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
