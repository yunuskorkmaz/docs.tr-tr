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
ms.openlocfilehash: f323e91e60c9735a51e955eaab6673ca167f294d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951874"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="ec6c6-102">IMetaDataImport::ResolveTypeRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec6c6-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="ec6c6-103">Belirtilen TypeRef <xref:System.Type> belirteci ile temsil edilen bir başvuruyu çözümler.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec6c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec6c6-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec6c6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec6c6-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="ec6c6-106">'ndaki İçin başvurulan tür bilgilerini döndürecek olan TypeRef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="ec6c6-107">'ndaki Döndürülecek arabirimin IID 'si `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="ec6c6-108">Genellikle bu IID_IMetaDataImport olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="ec6c6-109">dışı Başvurulan türün tanımlandığı modül kapsamına yönelik arabirim.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="ec6c6-110">dışı Başvurulan türü temsil eden bir TypeDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec6c6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec6c6-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ec6c6-112">Birden çok uygulama etki alanı yüklenmişse bu yöntemi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="ec6c6-113">Yöntem, uygulama etki alanı sınırlarına uymaz.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="ec6c6-114">Bir derlemenin birden çok sürümü yüklüyse ve aynı ad alanıyla aynı türü içeriyorsa, yöntemi bulduğu ilk türün modül kapsamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="ec6c6-115">Yöntemi `ResolveTypeRef` , diğer modüllerde tür tanımını arar.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="ec6c6-116">Tür tanımı bulunursa, `ResolveTypeRef` bu modül kapsamına ve tür için typedef belirtecine bir arabirim döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="ec6c6-117">Çözümlenecek tür başvurusunun, AssemblyRef 'nin bir çözüm kapsamı varsa, `ResolveTypeRef` yöntemi yalnızca [ımetadatadağıtıcı:: OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metoduna veya [' ye yapılan çağrılarla zaten açılmış olan meta veri kapsamları içinde bir eşleşme arar. Imetadatadağıtıcı:: OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="ec6c6-118">Bunun nedeni `ResolveTypeRef` , yalnızca diskte veya derlemenin depolandığı genel derleme önbelleğinde bulunan AssemblyRef kapsamından saptanamıyor.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec6c6-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec6c6-119">Requirements</span></span>  
 <span data-ttu-id="ec6c6-120">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec6c6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec6c6-121">**Üst bilgi** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ec6c6-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec6c6-122">**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ec6c6-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec6c6-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec6c6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec6c6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec6c6-124">See also</span></span>

- [<span data-ttu-id="ec6c6-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec6c6-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ec6c6-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec6c6-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
