---
title: "IMetaDataImport::ResolveTypeRef Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResolveTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 390387abef5c48b4842adcfbfca126bb8292cc28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="76e2f-102">IMetaDataImport::ResolveTypeRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76e2f-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="76e2f-103">Çözümler bir <xref:System.Type> belirtilen TypeRef belirteç tarafından temsil edilen başvuru.</span><span class="sxs-lookup"><span data-stu-id="76e2f-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76e2f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76e2f-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76e2f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76e2f-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="76e2f-106">[in] Başvurulan tür bilgileri döndürmek için TypeRef meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="76e2f-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="76e2f-107">[in] Döndürmek için IID arabiriminin `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="76e2f-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="76e2f-108">Genellikle, bu IID_IMetaDataImport olacaktır.</span><span class="sxs-lookup"><span data-stu-id="76e2f-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="76e2f-109">[out] Başvurulan türünün tanımlandığı modül kapsamı için bir arabirim.</span><span class="sxs-lookup"><span data-stu-id="76e2f-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="76e2f-110">[out] Başvurulan tür temsil eden bir TypeDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="76e2f-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76e2f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76e2f-111">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="76e2f-112">Birden çok uygulama etki alanları yüklerse, bu yöntem kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="76e2f-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="76e2f-113">Yöntemi, uygulama etki alanı sınırları uymaz.</span><span class="sxs-lookup"><span data-stu-id="76e2f-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="76e2f-114">Derleme birden fazla sürümünü yüklenir ve aynı ad ile aynı türde içerdikleri, bulduğu ilk türü modül kapsamı yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="76e2f-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="76e2f-115">`ResolveTypeRef` Diğer modüller tür tanımında yöntemi arar.</span><span class="sxs-lookup"><span data-stu-id="76e2f-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="76e2f-116">Tür tanımı bulunursa, `ResolveTypeRef` TypeDef Belirtecin türü için yanı sıra, modül kapsamı için bir arabirim döndürür.</span><span class="sxs-lookup"><span data-stu-id="76e2f-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="76e2f-117">Türü başvurusu çözümlenemedi AssemblyRef, çözümleme kapsamını varsa `ResolveTypeRef` yöntemi çağrıları ya da ile zaten açılmış olan meta veri kapsamları eşleşmeye arar [Imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)yöntemi veya [Imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="76e2f-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="76e2f-118">Bunun nedeni, `ResolveTypeRef` yalnızca diskte veya genel derleme önbelleğinde derleme depolandığı AssemblyRef kapsamdan belirleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="76e2f-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76e2f-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76e2f-119">Requirements</span></span>  
 <span data-ttu-id="76e2f-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76e2f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76e2f-121">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="76e2f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76e2f-122">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="76e2f-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76e2f-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76e2f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e2f-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76e2f-124">See Also</span></span>  
 [<span data-ttu-id="76e2f-125">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="76e2f-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="76e2f-126">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="76e2f-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
