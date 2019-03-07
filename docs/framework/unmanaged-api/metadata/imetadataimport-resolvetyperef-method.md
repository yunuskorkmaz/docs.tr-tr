---
title: IMetaDataImport::ResolveTypeRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f74952c2b3960dc29e0d1970276d972b048837f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499166"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="d4b28-102">IMetaDataImport::ResolveTypeRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4b28-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="d4b28-103">Çözümlenen bir <xref:System.Type> belirtilen TypeRef belirteci tarafından temsil edilen bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="d4b28-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b28-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4b28-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4b28-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4b28-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="d4b28-106">[in] Başvurulan tür bilgilerini döndürmek için TypeRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="d4b28-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="d4b28-107">[in] Döndürmek için bir IID arabirimi `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="d4b28-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="d4b28-108">Genelde bu IID_IMetaDataImport olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d4b28-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="d4b28-109">[out] Başvurulan tür tanımlandığı modül kapsamı için bir arabirim.</span><span class="sxs-lookup"><span data-stu-id="d4b28-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="d4b28-110">[out] Başvurulan tür temsil eden bir tür tanımı belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4b28-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4b28-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4b28-111">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d4b28-112">Birden çok uygulama etki alanları yüklerse, bu yöntemi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="d4b28-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="d4b28-113">Yöntemi, uygulama etki alanı sınırları uymaz.</span><span class="sxs-lookup"><span data-stu-id="d4b28-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="d4b28-114">Bir derlemenin birden çok sürümü yüklü olan ve aynı ad ile aynı türde içerdikleri bulduğu ilk türünde modül kapsamı yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4b28-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="d4b28-115">`ResolveTypeRef` Diğer modül türü tanımında yöntemi arar.</span><span class="sxs-lookup"><span data-stu-id="d4b28-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="d4b28-116">Tür tanımını bulunursa `ResolveTypeRef` TypeDef belirteç türünün yanı sıra, bu modül kapsamı için bir arabirim döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4b28-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="d4b28-117">Tür başvurusu çözümlenemedi için AssemblyRef, çözüm kapsamını varsa `ResolveTypeRef` yöntemi çağrılarıyla ya da zaten açılmış olan meta veri kapsamlardaki bir eşleşme arar [Imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)yöntemi veya [Imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d4b28-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="d4b28-118">Bunun nedeni, `ResolveTypeRef` yalnızca diskte veya genel derleme önbelleğinde derleme depolandığı AssemblyRef kapsamından belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="d4b28-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4b28-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4b28-119">Requirements</span></span>  
 <span data-ttu-id="d4b28-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4b28-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4b28-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d4b28-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4b28-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d4b28-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4b28-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4b28-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b28-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4b28-124">See also</span></span>
- [<span data-ttu-id="d4b28-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4b28-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d4b28-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4b28-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
