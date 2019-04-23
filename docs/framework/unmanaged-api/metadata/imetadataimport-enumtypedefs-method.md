---
title: IMetaDataImport::EnumTypeDefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 20913d1cfa258036e8c20e826415f96a8984fdb4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103369"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="b6c57-102">IMetaDataImport::EnumTypeDefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6c57-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="b6c57-103">Geçerli kapsamdaki tüm türleri temsil eden TypeDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="b6c57-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6c57-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6c57-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6c57-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6c57-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b6c57-106">[out] Yeni Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6c57-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="b6c57-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6c57-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="b6c57-108">[in] TypeDef simgeleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="b6c57-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b6c57-109">[in] En büyük boyutunu `rTypeDefs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="b6c57-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="b6c57-110">[out] Döndürülen TypeDef belirteçleri sayısı `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="b6c57-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6c57-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b6c57-111">Return Value</span></span>  
  
|<span data-ttu-id="b6c57-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6c57-112">HRESULT</span></span>|<span data-ttu-id="b6c57-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6c57-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b6c57-114">`EnumTypeDefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b6c57-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b6c57-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="b6c57-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b6c57-116">Bu durumda, `pcTypeDefs` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="b6c57-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6c57-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6c57-117">Remarks</span></span>  
 <span data-ttu-id="b6c57-118">TypeDef simgesi genişletilebilirlik mekanizması eklenen herhangi bir tür yanı sıra, bir sınıf veya arabirim gibi bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b6c57-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6c57-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6c57-119">Requirements</span></span>  
 <span data-ttu-id="b6c57-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6c57-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6c57-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b6c57-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6c57-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b6c57-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6c57-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6c57-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c57-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6c57-124">See also</span></span>

- [<span data-ttu-id="b6c57-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6c57-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b6c57-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6c57-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
